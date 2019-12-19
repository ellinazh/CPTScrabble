# CPTScrabble
/*
 * To change this license header, choose License Headers in Project Properties.
 * To change this template file, choose Tools | Templates
 * and open the template in the editor.
 */
package scrabble;

import java.util.ArrayList;
import java.util.Scanner;

/**
 *
 * @author e.ruiya
 */
public class Scrabble {

    /**
     * @param args the command line arguments
     */
    public static void main(String[] args) {
        Scanner in = new Scanner(System.in);
        //1.
        String[][] Scrabble = new String[15][15];
        for (int i = 0; i < 15; i++) {
            for (int j = 0; j < 15; j++) {
                Scrabble[i][j] = ".";
            }
        }

        String word_1;
        String Alphabet = "ABCDEFGHIJKLMNOPQRSTUVWXYZ_";
        String[] Letters = Alphabet.split("");
        ArrayList<String> Dictionary = new ArrayList<>();
        for (int i = 0; i < Letters.length; i++) {
            Dictionary.add(Letters[i]);
        }
        int xcoordinate = 0;
        int ycoordinate = 0;
        int coordination = 0;

        //Triple Word
        Scrabble[0][0] = "T";
        Scrabble[0][7] = "T";
        Scrabble[0][14] = "T";
        Scrabble[7][0] = "T";
        Scrabble[7][14] = "T";
        Scrabble[14][0] = "T";
        Scrabble[14][7] = "T";
        Scrabble[14][14] = "T";
        //Beginning
        Scrabble[7][7] = "S";
        //Double Letter
        Scrabble[0][3] = "8";
        Scrabble[0][11] = "8";
        Scrabble[2][6] = "8";
        Scrabble[2][8] = "8";
        Scrabble[3][0] = "8";
        Scrabble[3][7] = "8";
        Scrabble[3][14] = "8";
        Scrabble[6][2] = "8";
        Scrabble[6][6] = "8";
        Scrabble[6][8] = "8";
        Scrabble[6][12] = "8";
        Scrabble[7][3] = "8";
        Scrabble[7][11] = "8";
        Scrabble[8][2] = "8";
        Scrabble[8][6] = "8";
        Scrabble[8][8] = "8";
        Scrabble[8][12] = "8";
        Scrabble[11][0] = "8";
        Scrabble[11][7] = "8";
        Scrabble[11][14] = "8";
        Scrabble[12][6] = "8";
        Scrabble[12][8] = "8";
        Scrabble[14][3] = "8";
        Scrabble[14][11] = "8";
        //Double Word
        Scrabble[1][1] = "D";
        Scrabble[1][13] = "D";
        Scrabble[2][2] = "D";
        Scrabble[2][12] = "D";
        Scrabble[3][3] = "D";
        Scrabble[3][11] = "D";
        Scrabble[4][4] = "D";
        Scrabble[4][10] = "D";
        Scrabble[10][4] = "D";
        Scrabble[10][10] = "D";
        Scrabble[11][3] = "D";
        Scrabble[11][11] = "D";
        Scrabble[12][2] = "D";
        Scrabble[12][12] = "D";
        Scrabble[13][1] = "D";
        Scrabble[13][13] = "D";
        Scrabble[14][0] = "D";
        Scrabble[14][14] = "D";
        //Triple Letter
        Scrabble[1][5] = "7";
        Scrabble[1][9] = "7";
        Scrabble[5][1] = "7";
        Scrabble[5][5] = "7";
        Scrabble[5][9] = "7";
        Scrabble[5][13] = "7";
        Scrabble[9][1] = "7";
        Scrabble[9][5] = "7";
        Scrabble[9][9] = "7";
        Scrabble[9][13] = "7";
        Scrabble[13][5] = "7";
        Scrabble[13][9] = "7";
        int[] Letter_num = {9, 2, 2, 3, 15, 2, 2, 2, 8, 1, 1, 5, 3, 6, 6, 2, 1, 6, 6, 6, 6, 2, 1, 1, 1, 1, 2};
        int[] Letter_value = {1, 3, 3, 2, 1, 4, 2, 4, 1, 8, 10, 1, 2, 1, 1, 3, 8, 1, 1, 1, 1, 4, 10, 10, 10, 10, 0};
        //Loop
        int Player_1_points = 0;
        int Player_2_points = 0;
        int start = -1;
        ArrayList<String> Player_1_rack = new ArrayList<>();
        ArrayList<String> Player_2_rack = new ArrayList<>();
        int turns = 0;
        String[] word_3 = new String[0];
        String word_4 = "";
        Player_1_rack = Racks(Letter_num, Letters, Player_1_rack, turns, word_4, Dictionary, xcoordinate, ycoordinate, coordination, Scrabble, word_3,start);//int[] letters_num, String[] letters, ArrayList<String> RackLetters, int turns,String word2,ArrayList<String> Dictionary,int xcoordinate,int ycoordinate,int coordination,String[][]Scrabble,String[] word) {
        Player_2_rack = Racks(Letter_num, Letters, Player_2_rack, turns, word_4, Dictionary, xcoordinate, ycoordinate, coordination, Scrabble, word_3,start);
        PrintingBoard(Scrabble, Player_1_rack, Player_2_rack, Player_1_points, Player_2_points,turns);
        turns = 1;
        System.out.println("");
        System.out.println("Enter number of total turns");
        int turn = in.nextInt();
        int ans = 0;
        while (turns <= turn) {
            switch (turns % 2) {
                case 1:
                    System.out.println("Player 1 move");
                    System.out.println("Do you wish to redraw all your letters?");
                    System.out.println("1-Yes");
                    System.out.println("2-No");
                    ans = in.nextInt();
                    if (ans == 1) {
                        Player_1_rack = Redrawletters(Letter_num, Letters, Player_1_rack, turns);//int[] letters_num, String[] letters, ArrayList<String> RackLetters, int turns
               
                    System.out.println(Player_1_rack);
                    turns++;
                    
                    System.out.println("Player 2 turn now");
                    }
                    break;
                case 2:
                    System.out.println("Player 2 move");
                    System.out.println("Do you wish to redraw all your letters?");
                    System.out.println("1-Yes");
                    System.out.println("2-No");
                    ans = in.nextInt();
                    if (ans == 1) {
                        Player_2_rack = Redrawletters(Letter_num, Letters, Player_2_rack, turns);//int[] letters_num, String[] letters, ArrayList<String> RackLetters, int turns
                    
                    System.out.println(Player_2_rack);
                    turns++;
                    System.out.println("Player 1 turn now");
                    }
                    break;
            }
            System.out.println("");
            start = 0;
            System.out.println("Enter placement of the first letter of the word");
            System.out.println("x-coordinate(how many spaces to the right)");
            xcoordinate = in.nextInt();
            System.out.println("y-coordinate(how many spaces down");
            ycoordinate = in.nextInt();
            System.out.println("Is the word horizontal of vertical");
            System.out.println("1-Horizontal");
            System.out.println("2-Vertical");
            coordination = in.nextInt();
            System.out.println("Enter word");
            word_1 = in.next();
            String[] word_2 = word_1.split("");
            if (EmptyLetter(word_2)) {
                System.out.println("What letter do you want the blank square to be");
                String NewLetter = in.next();
                for (int i = 0; i < word_2.length; i++) {
                    if (word_2[i].equals("_")) {
                        word_2[i] = NewLetter.toUpperCase();
                    }
                }
            }
            if ((turns % 2) == 1) {
                if (ValidMove(xcoordinate, ycoordinate, coordination, word_2, turns, Scrabble, Player_1_rack, Dictionary, word_1,start)) {//int xcoordinate, int ycoordinate, int coordination, String[] word,ValidMove2(ArrayList<String>Rack,String[] word,ArrayList<String>Dictionary,String word2)
                    //
                    Player_1_rack = Racks(Letter_num, Letters, Player_1_rack, turns, word_1, Dictionary, xcoordinate, ycoordinate, coordination, Scrabble, word_2,start);
                    Player_2_rack = Racks(Letter_num, Letters, Player_2_rack, turns, word_1, Dictionary, xcoordinate, ycoordinate, coordination, Scrabble, word_2,start);
                    //Statements to add points onto the two players score continuously

                    Player_1_points = Player_1_points + Points(Letter_value, Letters, Letter_num, Player_1_points, word_2, xcoordinate, ycoordinate, Scrabble, coordination, turns);

                    //Adding points up to here
                    for (int i = 0; i < word_2.length; i++) {
                        if (coordination == 1) {
                            Scrabble[ycoordinate - 1][xcoordinate + i - 1] = word_2[i];
                        } else {
                            Scrabble[ycoordinate + i - 1][xcoordinate - 1] = word_2[i];
                        }
                    }
                    PrintingBoard(Scrabble, Player_1_rack, Player_2_rack, Player_1_points, Player_2_points,turns);//String[][]Scrabble,ArrayList<String>Player_1_rack,ArrayList<String>Player_2_rack,int Player_1_points,int Player_2_points

                } else {
                    System.out.println("Not a valid move, please try again");
                }
            }
            if (turns % 2 == 0) {
                if (ValidMove(xcoordinate, ycoordinate, coordination, word_2, turns, Scrabble, Player_2_rack, Dictionary, word_1,start)) {//int xcoordinate, int ycoordinate, int coordination, String[] word,ValidMove2(ArrayList<String>Rack,String[] word,ArrayList<String>Dictionary,String word2)
                    //
                    Player_1_rack = Racks(Letter_num, Letters, Player_1_rack, turns, word_1, Dictionary, xcoordinate, ycoordinate, coordination, Scrabble, word_2,start);
                    Player_2_rack = Racks(Letter_num, Letters, Player_2_rack, turns, word_1, Dictionary, xcoordinate, ycoordinate, coordination, Scrabble, word_2,start);
                    //Statements to add points onto the two players score continuously

                    Player_2_points = Player_2_points + Points(Letter_value, Letters, Letter_num, Player_2_points, word_2, xcoordinate, ycoordinate, Scrabble, coordination, turns);
                    //Adding points up to here
                    for (int i = 0; i < word_2.length; i++) {
                        if (coordination == 1) {
                            Scrabble[ycoordinate - 1][xcoordinate + i - 1] = word_2[i];
                        } else {
                            Scrabble[ycoordinate + i - 1][xcoordinate - 1] = word_2[i];
                        }
                    }
                    PrintingBoard(Scrabble, Player_1_rack, Player_2_rack, Player_1_points, Player_2_points,turns);//String[][]Scrabble,ArrayList<String>Player_1_rack,ArrayList<String>Player_2_rack,int Player_1_points,int Player_2_points

                } else {
                    System.out.println("Not a valid move, please try again");
                }
            }
            turns++;
        }
        if (Player_1_points > Player_2_points) {
            System.out.println("Congatulations Player 1 wins!");
        } else if (Player_1_points < Player_2_points) {
            System.out.println("Congratulations Player 2 wins!");
        } else {
            System.out.println("It's a tie!");
        }
    }

    public static int Points(int[] points, String[] letters, int[] num_letters, int point, String[] word, int xcoordinate, int ycoordinate, String[][] Scrabble, int coordination, int turns) {
        int count = 0;
        ArrayList<Integer> indexes = new ArrayList<>();
        for (int i = 0; i < word.length; i++) {
            for (int j = 0; j < letters.length; j++) {
                if ((word[i]).equalsIgnoreCase(letters[j])) { //Takes the indexes of the letters in the alphabet correponding to letters in the word
                    indexes.add(j);
                }
            }
        }
        if (turns == 1) {
            count = 2 * SpecialLetter(word, Scrabble, ycoordinate, xcoordinate, coordination, letters, points, indexes);
        } else {
            count = SpecialLetter(word, Scrabble, ycoordinate, xcoordinate, coordination, letters, points, indexes);
        }
        return count;

    }

    public static int SpecialLetter(String[] word, String[][] Scrabble, int ycoord, int xcoord, int coordination, String[] letters, int[] points, ArrayList<Integer> indexes) {
        int i;
        int doubleletter = 0;
        int tripleletter = 0;
        int totalword = 0;
        for (i = 0; i < indexes.size(); i++) {
            totalword = totalword + points[indexes.get(i)];//Adding all points
        }//Total points of word without doubling tripling
        ArrayList<String> DL = new ArrayList<>();
        ArrayList<String> TL = new ArrayList<>();
        for (i = 0; i < word.length; i++) {
            if (coordination == 1) {
                switch (Scrabble[ycoord - 1][xcoord + i - 1]) {
                    case "8": {
                        DL.add(word[i]);
                        ArrayList<Integer> Index = DoubleLetter(DL, letters);
                        for (i = 0; i < Index.size(); i++) {
                            for (int j = 0; j < points.length; j++) {
                                if (Index.get(i) == j) {
                                    doubleletter = points[j] + doubleletter;
                                }

                            }
                        }
                        totalword = totalword + doubleletter;
                        break;
                    }
                    case "7": {
                        TL.add(word[i]);
                        ArrayList<Integer> Index = TripleLetter(TL, letters);
                        for (i = 0; i < Index.size(); i++) {
                            for (int j = 0; j < points.length; j++) {
                                if (Index.get(i) == j) {
                                    tripleletter = 2 * points[j] + tripleletter;
                                }
                            }
                        }
                        totalword = totalword + tripleletter;
                        break;
                    }
                }
            } else {
                if (Scrabble[ycoord + i - 1][xcoord - 1].equals("d")) {
                    DL.add(word[i]);
                    ArrayList<Integer> Index = DoubleLetter(DL, letters);
                    for (i = 0; i < Index.size(); i++) {
                        for (int j = 0; j < points.length; j++) {
                            if (Index.get(i) == j) {
                                doubleletter = points[j] + doubleletter;
                            }
                        }
                    }
                    totalword = totalword + doubleletter;
                } else if (Scrabble[ycoord + i - 1][xcoord + i - 1].equals("t")) {
                    TL.add(word[i]);
                    ArrayList<Integer> Index = TripleLetter(TL, letters);
                    for (i = 0; i < Index.size(); i++) {
                        for (int j = 0; j < points.length; j++) {
                            if (Index.get(i) == j) {
                                tripleletter = 2 * points[j] + tripleletter;
                            }
                        }
                    }
                    totalword = totalword + tripleletter;

                }
            }
        }
        //Double Word Triple Word
        for (i = 0; i < word.length; i++) {
            if (coordination == 1) {
                switch (Scrabble[ycoord - 1][xcoord + i - 1]) {
                    case "D":
                        totalword = 2 * totalword;
                        System.out.println(totalword);
                        return totalword;
                    case "T":
                        totalword = 3 * totalword;
                        System.out.println(totalword);
                        return totalword;
                }
            } else {
                switch (Scrabble[ycoord + i - 1][xcoord - 1]) {
                    case "D":
                        totalword = 2 * totalword;
                        System.out.println(totalword);
                        return totalword;
                    case "T":
                        totalword = 3 * totalword;
                        System.out.println(totalword);
                        return totalword;
                }
            }

        }
        return totalword;
    }

    public static ArrayList<Integer> DoubleLetter(ArrayList<String> array, String[] letters) {
        int i;
        ArrayList<Integer> Index = new ArrayList<>();
        for (i = 0; i < array.size(); i++) {
            for (int j = 0; j < letters.length; j++) {
                if (array.get(i).equalsIgnoreCase(letters[j])) {
                    Index.add(j);
                }
            }
        }
        return Index;

    }

    public static ArrayList<Integer> TripleLetter(ArrayList<String> array, String[] letters) {
        int i;
        ArrayList<Integer> Index = new ArrayList<>();
        for (i = 0; i < array.size(); i++) {
            for (int j = 0; j < letters.length; j++) {
                if (array.get(i).equalsIgnoreCase(letters[j])) {
                    Index.add(j);
                }
            }
        }
        return Index;
    }

    public static boolean ValidMove(int xcoordinate, int ycoordinate, int coordination, String[] word, int turns, String[][] Scrabble, ArrayList<String> Rack, ArrayList<String> Dictionary, String word2,int start) {
        if (start == 0) {
            for (int i = 0; i < word.length; i++) {
                if (coordination == 1) {
                    if (Scrabble[ycoordinate - 1][xcoordinate - 1].equals("S")) {
                        if ((xcoordinate - 1) <= 15 && (ycoordinate - 1) <= 15) {
                            if (xcoordinate + word.length - 2 <= 15) {
                                return ValidMove2(Rack, Dictionary, word, word2, ycoordinate, xcoordinate, coordination, Scrabble);    //ValidMove2(ArrayList<String>Rack,String[] word,ArrayList<String>Dictionary,String word2)
                            }
                        }
                    }
                }
            }
            for (int i = 0; i < word.length; i++) {
                if (coordination == 2) {

                    if (Scrabble[ycoordinate - 1][xcoordinate + i - 1].equals("S")) {
                        if ((xcoordinate - 1) <= 15 && (ycoordinate - 1) <= 15) {
                            if (ycoordinate + word.length - 2 <= 15) {
                                return ValidMove2(Rack, Dictionary, word, word2, ycoordinate, xcoordinate, coordination, Scrabble);
                            }
                        }
                    }
                }
            }
        } else {
            if ((xcoordinate - 1) <= 15 && (ycoordinate - 1) <= 15) {
                if (coordination == 1) {
                    if (xcoordinate + word.length - 2 <= 15) {
                        return ValidMove2(Rack, Dictionary, word, word2, ycoordinate, xcoordinate, coordination, Scrabble);
                    }
                } else {
                    if (ycoordinate + word.length - 2 <= 15) {
                        return ValidMove2(Rack, Dictionary, word, word2, ycoordinate, xcoordinate, coordination, Scrabble);
                    }
                }
            }

        }

        return true;
    }

    public static boolean ValidMove2(ArrayList<String> Rack, ArrayList<String> Dictionary, String[] word2, String word, int ycoordinate, int xcoordinate, int coordination, String[][] Scrabble) {//Checks for whether words are used from rack; The one time the real word will be used...

        if (UseOtherLetters(word2, Scrabble, xcoordinate, ycoordinate, coordination) == false)// public static boolean UseOtherLetters(String[] word,String[][] Scrabble, int xcoord, int ycoord,int coordination){
        {
            //See if word2 is a subset of the rack letters
            int i = 0;
            int j = 0;
            for (i = 0; i < word2.length; i++) {
                for (j = 0; j < Rack.size(); j++) {
                    if (word2[i].equalsIgnoreCase(Rack.get(j))) {
                        break;
                    }
                }

                // If the above inner loop was not broken at all then word2[i] is not present in Rack[] 
                if (j == Rack.size()) {
                    return false;
                }
            }

            // If we reach here then all elements of word2 are present in the rack 
            return ValidMove3(word, Dictionary);
        } else {
            ArrayList<Integer> X = new ArrayList<>();
            int[] Y = new int[word2.length];
            ArrayList<Integer> Index = new ArrayList<>();
            ArrayList<String> Word = new ArrayList<>();
            if (coordination == 1) {
                for (int i = 0; i < word2.length; i++) {
                    if (!Scrabble[ycoordinate - 1][xcoordinate + i - 1].equals("D") || !Scrabble[ycoordinate - 1][xcoordinate + i - 1].equals("T") || !Scrabble[ycoordinate - 1][xcoordinate + i - 1].equals("7") || !Scrabble[ycoordinate - 1][xcoordinate + i - 1].equals("8")) {
                        X.add(i);
                    }
                }
            } else {
                for (int i = 0; i < word2.length; i++) {
                    if (!Scrabble[ycoordinate + i - 1][xcoordinate - 1].equals("D") || !Scrabble[ycoordinate + i - 1][xcoordinate - 1].equals("T") || !Scrabble[ycoordinate + i - 1][xcoordinate - 1].equals("7") || !Scrabble[ycoordinate + i - 1][xcoordinate - 1].equals("8")) {
                        X.add(i);
                    }
                }
            }
            for (int i = 0; i < word2.length; i++) {
                for (Integer X1 : X) {
                    if (i != X1) {
                        Y[i]++;
                    }
                }
            }
            for (int i = 0; i < Y.length; i++) {
                if (Y[i] != 3) {
                    Index.add(i);
                }
            }
            Index.stream().forEach((Index1) -> {
                Word.add(word2[Index1]);
            });
            int i = 0;
            int j = 0;
            for (i = 0; i < Word.size(); i++) {
                for (j = 0; j < Rack.size(); j++) {
                    if (Word.get(i).equalsIgnoreCase(Rack.get(j))) {
                        break;
                    }
                }

                // If the above inner loop was not broken at all then word2[i] is not present in Rack[] 
                if (j == Rack.size()) {
                    return false;
                }
            }

            // If we reach here then all elements of word2 are present in the rack 
            return ValidMove3(word, Dictionary);
        }
    }

    public static boolean ValidMove3(String word, ArrayList<String> Dictionary) {
        //check for dictionary terms
        //The one time the word will actually be used
        if (Dictionary.stream().anyMatch((Dictionary1) -> (word.equalsIgnoreCase(Dictionary1)))) {
            return true;
        }

        return false;
    }

    public static ArrayList<String> Racks(int[] letters_num, String[] letters, ArrayList<String> RackLetters, int turns, String word2, ArrayList<String> Dictionary, int xcoordinate, int ycoordinate, int coordination, String[][] Scrabble, String[] word,int start) {
        int count = 0;
        if (turns == 0) {
            while (count < 7) {
                int x = (int) ((27) * Math.random());
                if (letters_num[x] > 0) {
                    RackLetters.add(letters[x]);
                    letters_num[x]--;
                    count++;
                }
            }

        } else {
            if (ValidMove(xcoordinate, ycoordinate, coordination, word, turns, Scrabble, RackLetters, Dictionary, word2,start)) { //int xcoordinate, int ycoordinate, int coordination, String[] word, int turns, String[][] Scrabble, ArrayList<String> Rack, ArrayList<String> Dictionary, String word2
                for (String word1 : word) {
                    for (int j = 0; j < RackLetters.size(); j++) {
                        if (word1.equalsIgnoreCase(RackLetters.get(j))) {
                            RackLetters.set(j, "$");
                        }
                    }
                }
            }
            for (int i = 0; i < RackLetters.size(); i++) {
                if (RackLetters.get(i).equals("$")) {
                    int x = (int) ((27) * Math.random());
                    RackLetters.set(i, letters[x]);
                    letters_num[x]--;
                }
            }

        }
        return RackLetters;
    }

    public static void PrintingBoard(String[][] Scrabble, ArrayList<String> Player_1_rack, ArrayList<String> Player_2_rack, int Player_1_points, int Player_2_points,int turns) {
        if(turns ==0){
        for (int i = 0; i < 15; i++) {
            System.out.print(Scrabble[0][i]);
        }
        System.out.println("    Player 1 Points");
        for (int i = 0; i < 15; i++) {
            System.out.print(Scrabble[1][i]);
        }
        System.out.println("    " + Player_1_points);
        for (int i = 0; i < 15; i++) {
            System.out.print(Scrabble[2][i]);
        }
        System.out.println("    Player 2 Points");
        for (int i = 0; i < 15; i++) {
            System.out.print(Scrabble[3][i]);
        }
        System.out.println("    " + Player_2_points);
        for (int i = 0; i < 15; i++) {
            System.out.print(Scrabble[4][i]);
        }
        System.out.println("    Player 1 Rack");
        for (int i = 0; i < 15; i++) {
            System.out.print(Scrabble[5][i]);
        }
        System.out.println("    " + Player_1_rack);
        for (int i = 0; i < 15; i++) {
            System.out.print(Scrabble[6][i]);
        }
        System.out.println("    Player 2 Rack");
        for (int i = 0; i < 15; i++) {
            System.out.print(Scrabble[7][i]);
        }
        System.out.println("    " + Player_2_rack);

        for (int i = 8; i < 15; i++) {
            for (int j = 0; j < 15; j++) {
                System.out.print(Scrabble[i][j]);
            }
            System.out.println("");

        }
        }
        else{
        if(turns%2 ==0){
        for (int i = 0; i < 15; i++) {
            System.out.print(Scrabble[0][i]);
        }
        System.out.println("    Player 1 Points");
        for (int i = 0; i < 15; i++) {
            System.out.print(Scrabble[1][i]);
        }
        System.out.println("    " + Player_1_points);
        for (int i = 0; i < 15; i++) {
            System.out.print(Scrabble[2][i]);
        }
        System.out.println("    Player 2 Points");
        for (int i = 0; i < 15; i++) {
            System.out.print(Scrabble[3][i]);
        }
        System.out.println("    " + Player_2_points);
        for (int i = 0; i < 15; i++) {
            System.out.print(Scrabble[4][i]);
        }
        System.out.println("    Player 1 Rack");
        for (int i = 0; i < 15; i++) {
            System.out.print(Scrabble[5][i]);
        }
        System.out.println("    " + Player_1_rack);
        for (int i = 0; i < 15; i++) {
            System.out.print(Scrabble[6][i]);
        }
        System.out.println("");
        for (int i = 0; i < 15; i++) {
            System.out.print(Scrabble[7][i]);
        }
        System.out.println("    " );

        for (int i = 8; i < 15; i++) {
            for (int j = 0; j < 15; j++) {
                System.out.print(Scrabble[i][j]);
            }
            System.out.println("");

        }

        }
        else{
        for (int i = 0; i < 15; i++) {
            System.out.print(Scrabble[0][i]);
        }
        System.out.println("    Player 1 Points");
        for (int i = 0; i < 15; i++) {
            System.out.print(Scrabble[1][i]);
        }
        System.out.println("    " + Player_1_points);
        for (int i = 0; i < 15; i++) {
            System.out.print(Scrabble[2][i]);
        }
        System.out.println("    Player 2 Points");
        for (int i = 0; i < 15; i++) {
            System.out.print(Scrabble[3][i]);
        }
        System.out.println("    " + Player_2_points);
        for (int i = 0; i < 15; i++) {
            System.out.print(Scrabble[4][i]);
        }
        System.out.println("");
        for (int i = 0; i < 15; i++) {
            System.out.print(Scrabble[5][i]);
        }
        System.out.println("");
        for (int i = 0; i < 15; i++) {
            System.out.print(Scrabble[6][i]);
        }
        System.out.println("    Player 2 Rack");
        for (int i = 0; i < 15; i++) {
            System.out.print(Scrabble[7][i]);
        }
        System.out.println("    " + Player_2_rack);

        for (int i = 8; i < 15; i++) {
            for (int j = 0; j < 15; j++) {
                System.out.print(Scrabble[i][j]);
            }
            System.out.println("");

        }
        
    }
        }
    }
    

    public static boolean UseOtherLetters(String[] word, String[][] Scrabble, int xcoord, int ycoord, int coordination) {
        ArrayList<Integer> X = new ArrayList<>();
        ArrayList<Integer> Y = new ArrayList<>();
        if (coordination == 1) {
            for (int i = 0; i < word.length; i++) {
                if (!Scrabble[ycoord - 1][xcoord + i - 1].equals("D") || !Scrabble[ycoord - 1][xcoord + i - 1].equals("T") || !Scrabble[ycoord - 1][xcoord + i - 1].equals("7") || !Scrabble[ycoord - 1][xcoord + i - 1].equals("8")) {
                    X.add(xcoord + i - 1);
                    Y.add(ycoord - 1);
                }
            }
        } else {
            for (int i = 0; i < word.length; i++) {
                if (!Scrabble[ycoord + i - 1][xcoord - 1].equals("D") || !Scrabble[ycoord + i - 1][xcoord - 1].equals("T") || !Scrabble[ycoord + i - 1][xcoord - 1].equals("7") || !Scrabble[ycoord + i - 1][xcoord - 1].equals("8")) {
                    X.add(xcoord - 1);
                    Y.add(ycoord + i - 1);
                }
            }
        }
        return !X.isEmpty();
    }

    public static boolean EmptyLetter(String[] word) {
        for (String word1 : word) {
            if (word1.equals("_")) {
                return true;
            }
        }
        return false;
    }

    public static ArrayList<String> Redrawletters(int[] letters_num, String[] letters, ArrayList<String> RackLetters, int turns) {
        int count = 0;
//Reinput letters into "bag"
        RackLetters.stream().forEach((RackLetter) -> {
            for (int j = 0; j < letters_num.length; j++) {
                if (RackLetter.equals(letters[j])) {
                    letters_num[j]++;
                }
            }
        });
//Drwing new letters
        while (count < 7) {
            int x = (int) ((27) * Math.random());
            if (letters_num[x] > 0) {
                RackLetters.set(count, letters[x]);
                letters_num[x]--;
                count++;
            }
        }

        return RackLetters;
    }
}
