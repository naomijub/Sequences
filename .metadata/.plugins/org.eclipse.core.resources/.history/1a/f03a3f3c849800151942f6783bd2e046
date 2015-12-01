package Sequences.GA;

/**
 * Hello world!
 *
 */
public class App 
{
    public static void main( String[] args )
    {
        Chromosome pop = new Chromosome();
        pop.fitness();
        int bestFit = -10000;
        int bestIdx = 0;
        int count = 0;
        
        while(bestFit != 0){
        	pop.crossingover();
        	pop.mutate();
        	pop.convert();
        	pop.fitness();
        	bestFit = pop.getBestFitness();
        	bestIdx = pop.getBestIdx();
        	pop.average();
        	pop.cleanBest();
        	System.out.println(count+" BestFit: "+bestFit);
        	pop.printGene(bestIdx);
        	System.out.println();
        	count++;
        }
        System.out.println();
        System.out.println(count+" BestFit: "+bestFit+" Average: "+pop.getAverage());
    	pop.printGene(bestIdx);
        
    }
}
