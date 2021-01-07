# My-first-project-Java
Tic-Toc
package tictactoe;

import java.util.Scanner;

public class Main{
    public static char[][] tic = new char[3][3];
    public static int X_countS = 0;
    public static int O_countS = 0;
    public static boolean X_win = true;
    public static boolean O_win = true;


    public static void main( String[] args ){
        Scanner scanner = new Scanner(System.in);
        int k = 0;
        String word = "         ";
        System.out.println("---------");
        for ( int i = 0; i < tic.length; i++ ) {
            System.out.print("|" + " ");
            for ( int j = 0; j < tic.length; j++ ) {
                tic[i][j] = word.charAt(k);
                System.out.print(tic[i][j] + " ");
                k++;

            }
            System.out.println("|");

        }
        System.out.println("---------");




        while (X_win&&O_win&&(X_countS + O_countS < 9)) {
            System.out.print("Enter the coordinates: > ");
            String aI = scanner.next();
            String bJ = scanner.next();
            int X_diag1 = 0;
             int O_diag1 = 0;
             int X_diag2 = 0;
            int O_diag2 = 0;
            int Y_Y = 0;
            int X_X = 0;
            int O_X = 0;
             int O_Y = 0;
            while ( check(aI, bJ) ) {
                System.out.print("Enter the coordinates: > ");
                aI = scanner.next();
                bJ = scanner.next();
            }
            int xI = Integer.parseInt(aI);
            int yJ = Integer.parseInt(bJ);
            System.out.println("---------");
            for ( int i = 0; i < tic.length; i++ ) {
                System.out.print("|" + " ");
                for ( int j = 0; j < tic.length; j++ ) {

                    if((X_countS==O_countS)&& (xI - 1) == i && (yJ - 1) == j && tic[(xI - 1)][(yJ - 1)] == ' ') {
                        tic[i][j] = 'X';
                        X_countS++;

                    } else if(X_countS - O_countS == 1 && tic[(xI - 1)][(yJ - 1)] == ' ') {
                        tic[(xI - 1)][(yJ - 1)] = 'O';
                        O_countS++;
                    }
                    if(tic[i][j]=='X'&&i==j)
                    {
                        X_diag1++;
                    }
                    if(tic[i][j]=='X'&&((i+j)==2)){
                        X_diag2++;
                    }
                    if(tic[i][j]=='O'&&((i+j)==2)){
                        O_diag2++;
                    }
                    if(tic[i][j]=='O'&&i==j)
                    {
                        O_diag1++;
                    }
                    if(tic[i][j]=='X'&&tic[i][0]!='O'){
                        X_X++;
                    }else{
                        X_X=0;
                    }
                    if(tic[i][j]=='O'&&tic[i][0]!='X'){
                        O_X++;
                    }else {
                        O_X=0;
                    }
                    if(tic[0][j]=='O'&&tic[2][j]=='O'&&tic[1][j]=='O'){
                        O_Y++;
                    }else {
                        O_Y=0;
                    }
                    if(tic[0][j]=='X'&&tic[2][j]=='X'&&tic[1][j]=='X'){
                        Y_Y++;
                    }else {
                        Y_Y=0;
                    }




                    if(X_diag1==3||X_diag2==3||X_X==3||Y_Y==1){
                        X_win = false;

                    }
                    if(O_diag1==3||O_diag2==3||O_X==3||O_Y==1){
                        O_win = false;

                    }




                System.out.print(tic[i][j] + " ");

                }
                System.out.println("|");

            }

            System.out.println("---------");



        }
        if(!X_win){
            System.out.print("X wins");
        }else  if(!O_win){
            System.out.print("O wins");
        }else {
            System.out.print("Draw");
        }





    }


    public static boolean check( String aa, String bb ){ //заголовок метода
//ниже — тело метода


        if(! isNumeric(aa, bb)) {
            return true;
        }


        int a = Integer.parseInt(aa);
        int b = Integer.parseInt(bb);

        if(( a < 1 ) || ( a > 3 ) || ( b < 1 ) || ( b > 3 )) {
            System.out.println("Coordinates should be from 1 to 3!");
            return true;
        }

        if(tic[(a - 1)][b - 1] != ' ') {
            System.out.println("This cell is occupied! Choose another one!");
            return true;
        }

        return false;
    }

    public static boolean isNumeric( String str, String trs ){
        try {
            Integer.parseInt(str);
            Integer.parseInt(trs);
            return true;
        } catch (NumberFormatException e) {
            System.out.println("You should enter numbers!");
            return false;
        }
    }


}
