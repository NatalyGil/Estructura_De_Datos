package Sumatoria;
//realizado por Natalia Gil y Valeria Ospino

import java.io.*;
import java.util.Scanner;

public class Sumatorias {
    public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    int dato;
        String c;
        
        long tiempoInicial = System.nanoTime();
        int ejecuciones = 0;
        int [] valores = new int[1000000];

        
        int bandera = 1 ;
        double suma = 0.0;
        
            for (int i = 0; i < 1000000; i++) {
                
                while( bandera == 1){
                System.out.println("Introduzca un dato:");
                dato = sc.nextInt();
                suma = suma+dato;
                System.out.println("Desea continuar ingresando datos? S/N");
                c = sc.next();
                if (c.equalsIgnoreCase("N") || c.equalsIgnoreCase("n")){
                    bandera = 0;
                }
            }
            int temp = i * i;
            valores[i] = i * i + 1;
            ejecuciones = i;
        }
            System.out.println("La suma es: "+suma);

        long tiempoFinal = System.nanoTime();

        long tiempoEjecucion = tiempoFinal - tiempoInicial;

        System.out.println("Tiempo de ejecucion en nanosegundos: " + tiempoEjecucion);

        double tiempoEjecucionMs = tiempoEjecucion / 1_000_000.0;
        System.out.println("Tiempo de ejecucion en milisegundos: " + tiempoEjecucionMs);

        try {
            File archivo = new File("archivo.txt");

            FileWriter datos = new FileWriter("archivo.txt");
            datos.write("Tiempo de CPU, en milisegundos: " + tiempoEjecucionMs + "ms\n");
            datos.write("Ejecuciones: " + ejecuciones + "\n");
            datos.write("parametros: \n");
            for (int x = 0; x < valores.length; x++){
                datos.write(x+" . " + valores[x]+ "\n");
            }
            datos.close();
        }
        catch(FileNotFoundException e) {
        }
        catch(IOException e) {
        }
    }
}
