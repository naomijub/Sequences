package Sequences.GA;

import java.util.Random;

public class Chromosome {

	private final static int POP_SIZE = 70;
	private final static int GENE_SIZE = 8;
	private int[][] gene;
	private int[][] geneAux;
	private int[] fitness;
	private int bestFitness;
	private int bestIdx;
	private double average;
	
	public Chromosome(){
		fitness = new int[POP_SIZE];
		gene = new int[POP_SIZE][GENE_SIZE];
		geneAux = new int[70][8];
		Random rg = new Random();
		bestFitness = -10000;
		bestIdx = 0;
		average = 0;
		
		for(int i = 0;i < POP_SIZE;i++){
			fitness[i] = -5000;
			for(int j = 0;j < GENE_SIZE;j++){
				gene[i][j] = rg.nextInt(131 + i*j) % GENE_SIZE;
				geneAux[i][j] = 0;
			}
		}
	}
	
	public int getBestIdx(){
		return bestIdx;
	}
	
	public int getBestFitness(){
		return bestFitness;
	}
	
	public double getAverage(){
		return average;
	}
	
	public void printGene(int i){
		System.out.println(gene[i][0]+""+gene[i][1]+""+gene[i][2]+""+gene[i][3]+""+gene[i][4]+""+gene[i][5]+""+gene[i][6]+""+gene[i][7]);
	}
	
	public void fitness(){
		for(int i = 0;i < POP_SIZE;i++){
			int fit = 0;
			
			for(int j = 0;j < GENE_SIZE;j++){
				fit = fit - (int) Math.pow((j - gene[i][j]), 2.0);
				fit = fit + hasEqual(gene[i][j], i, j);
			}
			fitness[i] = fit;
		}
	}
	
	public int hasEqual(int gene, int posPop, int position){
		int fit = 0;
		
		for(int i = 0;i < GENE_SIZE;i++){
			if(this.gene[posPop][i] == gene && i != position){
				fit = fit - 50;
			}
		}
		return fit;
		
	}
	
	public void crossingover(){
		
		for(int i = 0;i < POP_SIZE;i++){
			int i1 = tournament();
			int i2 = tournament();
			
			for(int j = 0; j < 4;j++){
				geneAux[i][j] = gene[i1][j];
			}
			for(int j = 4; j < GENE_SIZE;j++){
				geneAux[i][j] = gene[i2][j];
			}
		}
		bestFitness();
	}
	
	public int tournament(){
		Random rg = new Random();
		int[] i = new int[5];
		int bestFit = -10000;
		int bestFitIdx = 0;
		
		for(int k = 0;k < 5;k++){
			i[k] = rg.nextInt(351) % POP_SIZE;
		}
		
		for(int k = 0;k < 5;k++){
			if (fitness[i[k]] > bestFit){
				bestFit = fitness[i[k]];
				bestFitIdx = i[k];
 			}
		}
		return bestFitIdx;
	}
	
	public void bestFitness(){
		for(int i = 0;i < POP_SIZE;i++){
			if(fitness[i] > bestFitness){
				bestFitness = fitness[i];
				bestIdx = i;
			}
		}
	}
	
	public void mutate(){
		Random rg = new Random();
		
		for(int i = 0;i < POP_SIZE;i++){
			int mutation = rg.nextInt(1001 + i*i) % 10;
			
			if(mutation < 3){
				int genePos = rg.nextInt(83) % GENE_SIZE;
				int gene = rg.nextInt(101) % GENE_SIZE;
				geneAux[i][genePos] = gene;
			}
		}
	}
	
	public void convert(){
		for(int i = 0;i < POP_SIZE;i++){
			for(int j = 0;j < GENE_SIZE;j++){
				gene[i][j] = geneAux[i][j];
			}
		}
	}
	
	public void average(){
		int sum = 0;
		for(int i = 0;i < POP_SIZE;i++){
			sum = sum + fitness[i];
		}
		average = sum / POP_SIZE;
	}
	
	public void cleanBest(){
		bestFitness = -10000;
		bestIdx = 0;
	}
}
