# PigLab
package d2;
import java.util.Scanner; // importing scanner class for uses input
import java.util.Random;// importing random class for the dice
 
public class game // classs name is game
{
   public static void main(String[] args) // main class 
   {
      int playerScores = 0;
      int playerTotal = 0;
      int computerScores = 0; // aka second player
      int computerTotal = 0;
      int dice;
      boolean gameOver = false; // default value of the boolean
      boolean turnOver = false;
      char repeat;
      String input;   
      Scanner keyboard  = new Scanner(System.in); // taking users input to figure out what to  do
       
      Random rand = new Random();
        
      System.out.println("Welcome to the game of Pig Game\n"); // introduction of the game 
       
      while (gameOver == false)
      {    
         do
         {
            dice = rand.nextInt(6) + 1;
            System.out.println("Player 1 rolled: " + dice); // PLayer one rolling his die first
            if (dice == 1)
            {
               playerScores = 0;
               System.out.print("Player 1´s turn! ");
               System.out.println("Player 1´s total is " + playerTotal);
               turnOver = true;
               while(playerTotal < 100);
            }
            else
            {
               playerScores += dice;
               System.out.print("Player 1 turn score is " +
                                playerScores);
               System.out.println(" If Player 1 holds Player 1 will have " +
                                  playerScores + " points.");
               System.out.println("Enter 'r' to roll " +
                                  "again, 'h' to hold."); // assiggning two values to check what to do based on the users input
               input = keyboard.nextLine();
               repeat = input.charAt(0);
  
               if (repeat == 'h') // if the user types a h 2 times repect the choise given to the user
                
                  break;                               
            }
         } while(turnOver == false || dice != 1);
            playerTotal += playerScores;
            System.out.println("Player 1 score is " + // show the score 
                               playerTotal);   
            playerScores = 0;
         if (playerTotal >= 100)
         {
            System.out.println("Player 1 WIN!");
            gameOver = true;
            while(playerTotal >= 100);
         } 
          
         System.out.println();
         System.out.println("Player 2´s turn."); // swithing player
         do
         {
            dice = rand.nextInt(6) + 1;
            System.out.println("Player 2 rolled: " +
                               dice);
            if(dice == 1)
            {
               computerScores = 0;
               System.out.print("Player 2 lost its turn!"); // defining lossing turn if roled a 1
               System.out.print(" Player 2 is " + 
                                computerTotal);
               turnOver = true;
               while(computerTotal < 100); 
            }
            else
            {
               computerScores += dice;
               if(computerScores >= 20 || (computerTotal +
                  computerScores) >= 100)
                  System.out.println("Player 2 holds"); 
                  turnOver = true;
            }
         } while (dice != 1 || computerScores < 20); 
             
            computerTotal += computerScores;
            System.out.println("Player 2´s score is " +
                               computerTotal + "\n");
            computerScores = 0;
         if (computerTotal >= 100)
         {
            System.out.println("Player 2 WINS!"); // defining who wins 
            gameOver = true;
            while (computerTotal >= 100);
         }
         if(keyboard!=null)
         keyboard.close();
          
   }
 }
}
