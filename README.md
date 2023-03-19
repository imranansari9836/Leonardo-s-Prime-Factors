# Leonardo-s-Prime-Factors
Leonardo loves primes and created  queries where each query takes the form of an integer, . For each , count the maximum number of distinct prime factors of any number in the inclusive range .

Note: Recall that a prime number is only divisible by  and itself, and  is not a prime number.

Example

The maximum number of distinct prime factors for values less than or equal to  is . One value with  distinct prime factors is . Another is .

Function Description

Complete the primeCount function in the editor below.

primeCount has the following parameters:

int n: the inclusive limit of the range to check
Returns

int: the maximum number of distinct prime factors of any number in the inclusive range .
Input Format

The first line contains an integer, , the number of queries.
Each of the next  lines contains a single integer, .

Constraints

Sample Input

6
1
2
3
500
5000
10000000000
Sample Output

0
1
1
4
5
10

import java.io.*;
import java.math.*;
import java.security.*;
import java.text.*;
import java.util.*;
import java.util.concurrent.*;
import java.util.function.*;
import java.util.regex.*;
import java.util.stream.*;
import static java.util.stream.Collectors.joining;
import static java.util.stream.Collectors.toList;

class Result {

    /*
     * Complete the 'primeCount' function below.
     *
     * The function is expected to return an INTEGER.
     * The function accepts LONG_INTEGER n as parameter.
     */

    public static int primeCount(long n) {
    // Write your code here
 if(n==1){
        return 0;
    }else if(n<=5){
        return 1;
    }else if(n  >= Long.parseLong("614889782588491410")){
        return 15;
    }else{
    List<Integer> prime=new ArrayList<>(Arrays.asList( 2,3, 5, 7, 11, 13, 17, 19, 23,                                                 29, 31, 37, 41, 43, 47, 53, 59,61, 67));
    long l=1;
    long h=1;
        for(int i=0;i< prime.size()-1; i++){
            l=h;
            h *=Long.parseLong(Integer.toString(prime.get(i)) );
            if(n >= l && n < h){
                return i;
            }
        }
    }
    return -1;
    }

}

public class Solution {
    public static void main(String[] args) throws IOException {
        BufferedReader bufferedReader = new BufferedReader(new InputStreamReader(System.in));
        BufferedWriter bufferedWriter = new BufferedWriter(new FileWriter(System.getenv("OUTPUT_PATH")));

        int q = Integer.parseInt(bufferedReader.readLine().trim());

        IntStream.range(0, q).forEach(qItr -> {
            try {
                long n = Long.parseLong(bufferedReader.readLine().trim());

                int result = Result.primeCount(n);

                bufferedWriter.write(String.valueOf(result));
                bufferedWriter.newLine();
            } catch (IOException ex) {
                throw new RuntimeException(ex);
            }
        });

        bufferedReader.close();
        bufferedWriter.close();
    }
}
