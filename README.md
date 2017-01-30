	/**
	 * Program to encrypt messages
	 * using Vigenere cipher
	 * */


	#include <stdio.h>
	#include <cs50.h>
	#include <stdlib.h>
	#include <string.h>
	#include <ctype.h>

	int main (int argc, string argv [])
	{
	    //To handle lack of argv[1]
	    if (argc <2 || argc > 2 )
	    {
		printf("Error!\n");
		return 1;
	    }

	    // else if (isalnum(argv[1]))
	    // {
	    //     printf("Error!");
	    //     return 1;
	    // }


	    //To encrypt message
	    else
	    {

	       string passcode = argv[1];
	       for(int i = 0, j = strlen(passcode); i < j; i++ )
	       {
		   if (!isalpha(passcode[i]))
		   {
		       printf("Error!");
		       return 1;
		   }
	       }


	       string msg = GetString();
	       int k = 0;
	       int key;

	       for (int i = 0, j = strlen(msg); i < j; i++)
	       {

		   int asc = (int)msg[i]; // Stores ASCII value of char




		   //To handle non-alphabetical characters

		if (!isalpha(msg[i]))
		  {


		      printf("%c", msg[i]);

		  }


		  //Handles characters in lowercase

		 else if (islower(msg[i]))
		  {

		      if (k >= strlen(passcode))
					  {
						  k = 0;
					  }


				  key = (int)(tolower(passcode[k]))- (int)'a';
		      int move_to = (asc + key);


		    while (move_to > 122) //Loop to wrap from z to a
		    {
			move_to = move_to - 122;
			move_to = (move_to)%122;
			move_to = move_to + 96;

		    }

		     printf("%c", (char)(move_to));
		     k++;

		  }


		  //Handles characters in upper case

		  else
		  {

		      if (k >= strlen(passcode))
					  {
						  k = 0;
					  }


				  key = (int)(tolower(passcode[k]))- (int)'a';
		      int move_to = (asc + key);


		    while (move_to > 90) //Loop to wrap from Z to A
		    {
			move_to = move_to - 90;
			move_to = (move_to)%90;
			move_to = move_to + 64;

		    }


		     printf("%c", (char)(move_to));
		     k++;
		  }
	       }
	       printf("\n"); //Prints new line after the exit of the loop
	       return 0;
	    }
	}
