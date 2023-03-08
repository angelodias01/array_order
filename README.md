# array_order
How to order a array in java!

import java.util.Scanner;

public class ex1_ArrayOrder 
{
    private static double min_value = -100.00, max_value = 100.00, in = 0,final_v = 0;
    private static int dim = 0;

    public static void main(String[] args)
    {
        System.out.println("\u000c");
        Scanner input = new Scanner(System.in);

        while(dim == 0)
        {
            System.out.println("Insert a number for the array size! ");
            String in = input.next();
            try 
            {
                dim = Integer.parseInt(in); 
            }
            catch(NumberFormatException e) {
                System.out.println("Input is not valid!"); 
            }
        }  
        System.out.println("\u000c");

        double[] array = new double[dim];
        double[] array_ord_asc = new double[dim];
        double[] array_ord_desc = new double[dim];

        System.out.println("Insert " + dim + " numbers between -100 and 100! ");
        for(int i = 0; i < dim; i++)
        { 
            boolean in_num = false;
            while(in_num == false)
            { 
                String in = input.next();
                try {
                    double insert_num = Double.parseDouble(in); 
                    if(insert_num  >= min_value && insert_num  <= max_value)
                    {
                        array[i] = insert_num ;
                        in_num = true;
                    }
                    else
                    {
                        while(insert_num  < min_value || insert_num  > max_value){
                            System.out.println("Invalid number: ");
                            System.out.println("Insert " + dim + " numbers between -100 and 100! ");
                            in_num = false;
                            break;
                        }
                    }
                }catch(NumberFormatException e) {
                    System.out.println("Invalid input!");
                    in_num = false;
                    break;
                }
            }
        }

        System.out.println("\u000c");

        System.out.print("Inputed Array: "); 
        prdouble_array(array);
        System.out.println("\n"); 

        System.out.print("Ordered Ascendent Array: "); 
        array_ord_asc = sort_array_asc(array);
        prdouble_array(array_ord_asc);
        System.out.println("\n"); 
        
        System.out.print("Ordered Descendent Array: "); 
        array_ord_desc = sort_array_desc(array);
        prdouble_array(array_ord_desc);
        input.close();
    }

    private static double[] sort_array_asc(double[] array)
    {
        //bubble sort method
        double[] sorted_array_asc = array;
        for (int x = 0; x < dim; x++) 
        {     
            for (int y = x+1; y < dim; y++) 
            {     
                if(array[x] > array[y]) {//swap elements if not in order
                    final_v = array[x];    
                    array[x] = array[y];    
                    array[y] = final_v;    
                }     
            }     
        } 
        return sorted_array_asc;
    }

    private static double[] sort_array_desc(double[] array)
    {
        //bubble sort method
        double[] sorted_array_desc = array;
        for (int a = 0; a < dim; a++) 
        {     
            for (int b = a+1; b < dim; b++) 
            {     
                if(array[a] < array[b]) {//swap elements if not in order
                    final_v = array[a];    
                    array[a] = array[b];    
                    array[b] = final_v;    
                }     
            }     
        } 
        return sorted_array_desc;
    }

    private static void prdouble_array(double[] array)
    {
        //prdoubles the array
        for (int i = 0; i < dim; i++) 
        {     
            System.out.print("|" + array[i] + "|");
        }
    }
} 
