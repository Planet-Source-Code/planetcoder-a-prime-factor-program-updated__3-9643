<div align="center">

## A prime factor program \(UPDATED\!\)


</div>

### Description

Program for calculating prime factors. Accepts very large numbers upto 2^53 -1 (9007199254740991)or more than 9 billion billion. Shows elasped time if time taken is 1 second or more.

Largest prime accepted: 9007199254740881.
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[PlanetCoder](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/planetcoder.md)
**Level**          |Beginner
**User Rating**    |4.3 (13 globes from 3 users)
**Compatibility**  |C, Microsoft Visual C\+\+, Borland C\+\+
**Category**       |[Math](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/math__3-12.md)
**World**          |[C / C\+\+](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/c-c.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/planetcoder-a-prime-factor-program-updated__3-9643/archive/master.zip)

### API Declarations

```
&lt;stdio.h&gt;
&lt;math.h&gt;
&lt;time.h&gt;
```


### Source Code

```
/*Prime.c:
 	By Abdullah Chougle. Please VOTE at
 http://www.planet-source-code.com/vb/scripts/ShowCode.asp?txtCodeId=9643&lngWId=3
 	Program for calculating prime factors.
 Can accept nos. upto 2^53-1 (9007199254740991) or 9 billion billion.
 Shows elasped time if time taken is 1 second or more.
 	Largest prime accepted: 9007199254740881
 */
 #include <stdio.h> /*include the standard input/output header file*/
 #include <math.h>/*include the math.h file for complex mathematical operations such as sqrt() and fmod()*/
 #include <time.h>/*include this file for calculating elapsed time*/
 void prime_no(long double); /*function for checking the inputted value, whether it is a decimal, or beyond the range.*/
 long double calc_prime(long double); /*returns the first prime factor of the number passed to it from the above function, or returns the number itself if it is
prime*/
 main()
 {
 	long double prime; /*long double (and not "long int") is used for extra precision*/
 	while(1) /*infinite while loop, exited using a break statement*/
 	{
 		puts("Enter an integer to find its prime factors or enter 0 to quit:");
 		scanf("%Lf", &prime);
 		if(prime==0)
 			break; /*exiting the program*/
 		else
 			prime_no(prime); /*transferring control to this function*/
 	}
 }
 void prime_no(long double dx)
 {
 	long double pfact=1;/*where pfact denotes prime factor*/
 	long double x;
 	int count=1;
 /****************TIME************************/
 time_t starts, finishes;
 time(&starts);
 /*********************TIME*******************/
 	/***ERROR CHECKING**/
 	if (dx <0)
 	{
 		puts("You've entered a negative value. The minus sign will be ignored.");
 		dx = -dx;
 	}
 	if (floor(dx)!=dx && ceil(dx)!=dx) /*if rounded off value is not equal to inputted value*/
 	{
 		/**PRECISION CHECK**/
 		if(dx>9007199254740991) /*Max. precision of long double*/
 		{
 			puts("Sorry, this program can only handle numbers below 9007199254740991 (2^53 - 1)\n");
 			return;
 		}
 		/***ERROR CHECKING**/
 		puts("This value contains a decimal fraction.\nOnly the integral part will be considered.");
 		dx=floor(dx);
 	}
 /****CALCULATING AND DISPLAYING THE VALUES****/
 	if(dx==1)
 		printf("\tThis number is neither prime nor composite");
 	else
 	{
 		do
 		{
 			if(count==1)
 			{
 				printf("\t");
 				x=dx/pfact;
 			}
 			else
 				x/=pfact;
 			pfact=calc_prime(x);
 			if (count>1)
 				printf(", ");
 			if(pfact==dx)
 				printf("This is a prime number.");
 			else
 				printf("%.0Lf", pfact);
 			count++;
 		}while (pfact!=x);
 	}
 /**********************TIME*********************/
 time(&finishes);
 if(difftime(finishes,starts)) /*if elapsed time is greater than 1 second, then display it*/
 	printf("\tElapsed time: %g sec", difftime(finishes, starts));
 /**********************TIME*********************/
 	puts("\n");
 	return;
 }
 //type long double is used for calculati
 // on of large values
 long double calc_prime(long double x)
 {
 	register unsigned long count; /*register is used in an attempt to increase calculation speed*/
 	if (x==2)
 	{
 		return 2;
 	}
 	if (x>2)
 	{
 		if (fmod(x,2)==0) /*if x is divisible by 2*/
 			return 2;
 		for (count = 3; count <= sqrt(x); count+=2) /*try to divide the number by all odd integers upto x's square root until a factor is found*/
 		{
 			if (fmod(x,count)==0) /*where fmod denotes the remainder*/
 			{
 				return count;/*return the factor*/
 			}
 		}
 		return x;/*i.e. return the same number if it is prime.*/
 	}
 }
```

