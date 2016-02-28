# laberinto-JuanPabloLondono
laberinto-JuanPabloLondono created by Classroom for GitHub

import java.util.Scanner;
public class Laberinto
{
    static char MatrizGlobal[][];
    static int paredes = 0;
    static int ng = 0;
    static int resta = 0;
    public static void main (String [ ] args) 
    {
        LlenarMatriz();
        Marcar(ng-1,ng-1);
        Marcar(0,0);
        Resultado();
    }  

    public static void LlenarMatriz()
    {
        Scanner sc = new Scanner(System.in);
        System.out.println("");
        int n = sc.nextInt();
        ng = n;
        char Matriz[][]=new char[n][n];
        if(n>=3 && n<=33)
        {
            for (int x=0; x < Matriz.length; x++) {
                for (int y=0; y < Matriz[x].length; y++) {
                    String str = sc.next();

                    for(int z=0; z<n; z++)
                    {
                        char c = str.charAt(z);
                        if((c == '.') || (c == '#'))
                        {
                            Matriz[x][y] = c;
                        }
                        else
                        {
                            System.out.println("Entrada no valida, el programa fallara");
                        }
                        y++;
                    }
                }
            }
            MatrizGlobal = Matriz;
        }
    }

    public static void Marcar(int x,int y)
    {
        MatrizGlobal[x][y] = ',';
        if(x+1!=ng&&MatrizGlobal[x+1][y] == '.'){
            Marcar(x+1,y);
        }
        if(x-1!=-1&&MatrizGlobal[x-1][y] == '.'){
            Marcar(x-1,y);
        }
        if(y+1!=ng&&MatrizGlobal[x][y+1] == '.'){
            Marcar(x,y+1);
        }
        if(y-1!=-1&&MatrizGlobal[x][y-1] == '.'){
            Marcar(x,y-1);
        }
    }

    public static void Resultado()
    {
        for(int x = 0; x<MatrizGlobal.length;x++)
        {
            for(int y = 0;y<MatrizGlobal[x].length;y++)
            {
                if (MatrizGlobal[x][y] == ',')
                {
                    if(((x+1) == ng) || (MatrizGlobal[x+1][y] == '#'))
                    {
                        paredes++;
                    }
                    if(((x-1) == -1) || (MatrizGlobal[x-1][y] == '#'))
                    {
                        paredes++;
                    }
                    if(((y+1) == ng) || (MatrizGlobal[x][y+1] == '#'))
                    {
                        paredes++;
                    }
                    if(((y-1) == -1) || (MatrizGlobal[x][y-1] == '#'))
                    {
                        paredes++;
                    }
                }
            }
        }
        System.out.println((paredes-4)*9);
    }
}
