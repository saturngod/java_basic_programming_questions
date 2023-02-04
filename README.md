
Q1. 
An array is called paired if all even indices have odd values and all odd indices has even value. For example {1, 4, 7} is paired because a[0] and a[2] have odd values, and a[1] has even value. The method should return 1 if the paired, 0 otherwise.

A1:

Event Indexd မှာ Odd value ရှိပြီး Odd Index မှာ Event value ရှိရမယ်။​ ဟုတ်ခဲ့ရင် 1 ပြန်။ မဟုတ်ခဲ့ရင် 0 ပြန် ။

```java
public class Main {  
    public static void main(String[] args) {  
        int[] value = {1,4,7};  
        System.out.println(isPaired(value));  
    }  
    public static int isPaired(int[] a) {  
        for (int i = 0; i < a.length; i++) {  
            if (i % 2 == 0 && a[i] % 2 == 0) {  
                return 0;  
            }  
            if (i % 2 == 1 && a[i] % 2 == 1) {  
                return 0;  
            }  
        }  
        return 1;  
    }  
}
```

---

Q2. Write a function called maxDistance that find the max distance between non-trivial factors of a number. Non-trivial means, neither 1 nor the number it self. For example: 12 has factors: 2, 3, 4, 6 -> max distance is 6-2 = 4. If the number has only one factor (e.g. 49 has only one factor which 7) the method should return 0. If the number has no factors (e.g. 13), the method should return -1

A2:

Factor လား Non Factor လားဆိုပြီး ရှာဖို့ လိုပါတယ်။ Factor ဖြစ်ခဲ့ရင် distance ကို အကြီးဆုံး  value ကနေ နောက်ဆုံး value ကို နှုတ်ပေးဖို့ လိုပါတယ်။

Factor ဟုတ်မဟုတ် စစ်ဖို့ ပေးလိုက်သည့် num အထိ loop ပတ်ပြီး စားလို့ ပြတ်မပြတ် တွက်ဖို့ လိုပါတယ်။

```java
public static int maxDistance(int num) {  
    if (num <= 1) return -1;  
  
    int maxFactor = -1;  
    int minFactor = Integer.MAX_VALUE;  
  
    for (int i = 2; i <= num / 2; i++) {  
        if (num % i == 0) {  
            if (i > maxFactor) {  
                maxFactor = i;  
            }  
            if (i < minFactor) {  
                minFactor = i;  
            }  
        }  
    }  
    //no change for max and min value. So, it's not factor  
    if (maxFactor == -1 || minFactor == Integer.MAX_VALUE) return -1;  
  
    return maxFactor - minFactor;  
}
```

---

Q3:

input: {8, 9, 9, 5, 0} 
mile: 1 
output: {9, 9, 9, 5, 0} 

input: {8, 9, 9, 5, 0} 
mile: 2 
output: {0, 0, 0, 6, 0} 

input: {9, 9, 9, 9, 9, 9, 9, 9, 9, 9} 
mile: 1 
output: {0, 0, 0, 0, 0, 0, 0, 0, 0, 0} 

input: {9, 9, 9, 9, 9, 9, 9, 9, 9, 9} 
mile: 13 
output: {2, 1, 0, 0, 0, 0, 0, 0, 0, 0}

Q3: Answser

အဖြေက လွယ်ပါတယ်။​ carry value လေး ကို သယ်သွားဖို့ ပဲလိုတာပါ။

```java
public static int[] updateMileage(int[] mileage, int miles) {  
    int carry = miles;  
  
   for (int i=0; i < mileage.length; i++) {  
    int newValue = mileage[i] + carry;  
            mileage[i] = newValue % 10;  
            carry = newValue/10;  
   }  
  
   return mileage;  
  
}
```


---

Q4:  An array is said to be hollow if it contains 3 or more zeros in the middle that are preceded and followed by the same number of non-zero elements. Furthermore, all the zeroes in the array must be in the middle of the array. Write a function named isHollow that accepts an integer array and returns 1 if it is a hollow array, otherwise it returns 0.

```java
public static boolean middleZero(int[] values) {  
    int start = 0;  
    int end = 0;  
    int zeroCount = 0;  
    for(int i=0; i< values.length;i++) {  
        if(values[i] == 0) {  
            start = i - 1;  
            break;        }  
    }  
  
    for(int i=values.length-1; i >=0;i--) {  
        if(values[i] == 0) {  
            end = i + 1;  
            break;        }  
    }  
  
    for(int k = start + 1; k< end ; k++) {  
        if(values[k] == 0) {  
            zeroCount = zeroCount +1;  
        }  
        else {  
            return false;  
        }  
    }  
  
    return (zeroCount >=3 && start + 1 == values.length - end);  
  
}
```

---

Q5: 

A positive number n is consecutive-factored if and only if it has factors, i and j where i > 1, j > 1 and j = i + 1. Write a function named isConsecutiveFactored that returns 1 if its argument is consecutive-factored, otherwise it returns 0.

the function signature is  
int isConsectiveFactored(int n)

```java
 static int isConsecutiveFactored(int number) {
        ArrayList al = new ArrayList();
        for (int i = 2; i <= number; i++) {
            int j = 0;
            int temp;
            temp = number % i;

            if (temp != 0) {
                continue;
            } 

            else {

                al.add(i);
                number = number / i;
                j++;

            }
        }

        Object ia[] = al.toArray();
        System.out.println("Factors are: " + al);
        int LengthOfList = al.size();
        if (LengthOfList >= 2) {
            int a = ((Integer) ia[0]).intValue();
            int b = ((Integer) ia[1]).intValue();

            if ((a + 1) == b) {
                return 1;
            } else {
                return 0;
            }
        } else {
            return 0;
        }

    }
```

---

Q6: NextPefectSquare

Need to write a function `int isPerfectSquare(int n)`.

Example:

n = 6
next perfect square = 9

Answer:

```java
static int nextPerfectSquare(int n) {  
    if(n < 0) return 0;  
    int current = (int) Math.floor(Math.sqrt(n));  
    current = current + 1;  
  
    return current * current;  
}
```

---

Q7: Define the n-up count of an array to be the number of times the partial sum goes from less than or equal to n to greater than n during the calculation of the sum of the elements of the array.

For example, if n=5, the 5-upcount of the array {2, 3, 1, -6, 8, -3, -1, 2} is 3.

A7:

```java
static int nUpCount(int[] a, int n){  
    int nUpCount = 0;  
    int partialSum = 0;  
    int previousPartialSum = 0;  
    for(int i=0; i<a.length; i++){  
        previousPartialSum = partialSum;  
        partialSum += a[i];  
        if(previousPartialSum <= n && partialSum > n){  
            nUpCount++;  
        }  
    }  
    return nUpCount;  
}
```

---

Q 8:   Write a function named primeCount with signature
```
int primeCount(int start, int end);
```

The function returns the number of primes between start and end inclusive. Recall that a prime is a positive integer greater than 1 whose only integer factors  are 1 and itself.

A8:

```java
static boolean isPrime(int number) {  
    if(number <= 1 ) {  
        return false;  
    }  
    for(int i= 2 ; i<= number/2; i++) {  
        if(number % i == 0) {  
            return false;  
        }  
    }  
    return true;  
}  
static int primeCount(int start,int end) {  
  
    int count = 0;  
    for(int i=start ; i <= end; i++) {  
        if( isPrime(i)) {  
            count++;  
        }  
    }  
  
    return count;  
}
```

---

Q9: 
A Madhav array has the following property. 
```
a[0] = a[1] + a[2] = a[3] + a[4] + a[5] = a[6] + a[7] + a[8] + a[9] = ...
```
   

The length of a Madhav array must be `n*(n+1)/2` for some n.

A9:

a[0] = a[1] + a[2]
a[0]  = a[3]+ a[4] + a[5]
a[0]  = a[6]+ a[7] + a[8] + a[9]

So

```java
static int isMadhavArray(int[ ] a) {  
    if(a.length < 3 )  
        return 0;  
  
    int i = 1, counter = 2;  
    while (i < a.length) {  
  
        int sum = 0;  
        System.out.println("COUNTER IS " + counter);  
        for (int j = 0; j < counter; j++, i++) {  
  
            sum +=a[i];  
        }  
  
        System.out.println("SUM IS " + sum);  
        if(sum != a[0])  
            return 0;  
        System.out.println("--------");  
        System.out.println(i);  
        System.out.println(counter);  
        System.out.println("--------");  
        if(i == a.length)  
        {  
            System.out.println("----++++---");  
            if(counter*(counter+1)/2 == a.length)  
                return 1;  
        }  
        else {  
            counter++;  
            if((i+counter) > a.length)  
                return 0;  
        }  
    }  
    return 1;  
}
```

---

Q10:  An array is defined to be inertial if the following conditions hold:

 a. it contains at least one odd value

 b. the maximum value in the array is even

 c. every odd value is greater than every even value that is not the maximum value. 

  

So {11, 4, 20, 9, 2, 8} is inertial because 

 a. it contains at least one odd value

 b. the maximum value in the array is 20 which is even

 c. the two odd values (11 and 9) are greater than all the      

    even values that are not equal to 20 (the maximum), i.e., (4, 2, 8}. 

  

However, {12, 11, 4, 9, 2, 3, 10} is not inertial because it fails condition (c), i.e., 10 (which is even) is greater 9 (which is odd) but 10 is not the maximum value in the array.

  

Write a function called isIntertial that accepts an integer array and returns 1 if the array is inertial; otherwise it returns 0.

A10:
```java
static int isInterial(int[] a) {  
    if(a.length <= 0) {  
        return 0;  
    }  
    //find the odd  
    boolean odd = false;  
    boolean maxisEvent = false;  
    int max = a[0];  
    ArrayList<Integer> oddsArr = new ArrayList<>();  
    ArrayList<Integer> eventArr = new ArrayList<>();  
    for(int i = 0 ; i < a.length; i++) {  
        if(a[i] % 2 != 0) {  
            odd = true;  
            oddsArr.add(a[i]);  
        }  
        if (max < a[i]) {  
            max = a[i];  
            if(max % 2 == 0) {  
                maxisEvent = true;  
            }  
        }  
        if(a[i] != max && a[i] % 2 ==0) {  
            eventArr.add(a[i]);  
        }  
    }  
  
    for (int k=0 ; k < oddsArr.size(); k++) {  
        for (int y = 0 ; y < eventArr.size(); y++) {  
            if (oddsArr.get(k) < eventArr.get(y)) {  
                return 0;  
            }  
        }  
    }  
  
    if(odd == true && maxisEvent == true) {  
        return 1;  
    }  
    return 0;  
}
```

---

Q10 

Define a square pair to be the tuple <x, y> where x and y are positive, non-zero integers, x<y and x + y is a perfect square. A perfect square is an integer whose square root is also an integer, e.g. 4, 9, 16 are perfect squares but 3, 10 and 17 are not. Write a function named countSquarePairs that takes an array and returns the number of square pairs that can be constructed from the elements in the array. For example, if the array is {11, 5, 4, 20} the function would return 3 because the only square pairs that can be constructed from those numbers are <5, 11>, 

<5, 20> and <4, 5>.  You may assume that there exists a function named isPerfectSquare that returns 1 if its argument is a perfect square and 0 otherwise. E.G., isPerfectSquare(4) returns 1 and isPerfectSquare(8) returns 0.

  

If you are programming in Java or C#, the function signature is

int countSquarePairs(int[ ] a)

  

If you are programming in C++ or C, the function signature is

int countSquarePairs(int a[ ], int len)  where len is the number of elements in the array.

  

You may assume that there are no duplicate values in the array, i.e, you don't have to deal with an array like {2, 7, 2, 2}.


A10:

```java
public static int[] bubbleSort(int[] arr) {  
    for(int i=0 ; i < arr.length; i++) {  
        for(int k= i+1; k < arr.length; k++) {  
            if(arr[i] > arr[k]) {  
                int tmp = arr[k];  
                arr[k] = arr[i];  
                arr[i] = tmp;  
            }  
        }  
    }  
    return arr;  
}  
public static int countSquarePairs(int[] arr) {  
    if(arr.length < 2) {  
        return 0;  
    }  
    arr = bubbleSort(arr);  
    int count = 0;  
    for (int i = 0; i < arr.length - 1; i++) {  
        for (int j = i + 1; j < arr.length; j++) {  
            if(arr[i] > 0 && arr[j] > 0) {  
                int sum = arr[i] + arr[j];  
                int sqrt = (int) Math.sqrt(sum);  
                if (sqrt * sqrt == sum) {  
                    count++;  
                }  
            }  
        }  
    }  
    return count;  
}
```

---
Q 11 :

A prime number is an integer that is divisible only by 1 and itself. A porcupine number is a prime number whose last digit is 9 and the next prime number that follows it also ends with the digit 9. For example 139 is a porcupine number because:

    a. it is prime

    b. it ends in a 9

    c. The next prime number after it is 149 which also ends in 9. Note that 140, 141, 142, 143, 144, 145, 146, 147 and 148 are not prime so 149 is the next prime number after 139.

  

Write a method named findPorcupineNumber which takes an integer argument n and returns the first porcupine number that is greater than n. So findPorcupineNumber(0) would return 139 (because 139 happens to be the first porcupine number) and so would findPorcupineNumber(138). But findPorcupineNumber(139) would return 409 which is the second porcupine number.

  

The function signature is

int findPorcupineNumber(int n)

  

You may assume that a porcupine number greater than n exists.

A 11:

```java
public static boolean isPrimeNumber(int num) {  
    if (num <= 1) return false;  
    for (int i = 2; i <= Math.sqrt(num); i++) {  
        if (num % i == 0) return false;  
    }  
    return true;  
}  
public static int  findPorcupineNumber(int n){  
    int num = n + 1;  
    while (true) {  
        if (isPrime(num) && num % 10 == 9) {  
            //current one is prince and end with zero  
            int nextNum = num + 1;  
            //find next prime  
            while (!isPrimeNumber(nextNum)) {  
                nextNum += 1;  
            }  
            //and then check is end with 9  
            if (nextNum % 10 == 9) return num;  
        }  
        num++;  
    }  
  
  
}
```

---
Q12:

Consider the following algorithm

Start with a positive number n

if n is even then divide by 2

if n is odd then multiply by 3 and add 1

continue this until n becomes 1

The Guthrie sequence of a positive number n is defined to be the numbers generated by the above algorithm.

  

For example, the Guthrie sequence of the number 7 is 

7,  22, 11, 34, 17, 52, 26, 13, 40, 20, 10, 5, 16, 8, 4, 2, 1

  

It is easy to see that this sequence was generated from the number 7 by the above algorithm. Since 7 is odd multiply by 3 and add 1 to get 22 which is the second number of the sequence. Since 22 is even, divide by 2 to get 11 which is the third number of the sequence. 11 is odd so multiply by 3 and add 1 to get 34 which is the fourth number of the sequence and so on.

  

Note: the first number of a Guthrie sequence is always the number that generated the sequence and the last number is always 1.

  

Write a function named isGuthrieSequence which returns 1 if the elements of the array form a Guthrie sequence. Otherwise, it returns 0.

  

If you are programming in Java or C#, the function signature is

int isGuthrieSequence(int[ ] a)

  

If you are programming in C++ or C, the function signature is

int isGuthrieSequence(int a[ ], int len) when len is the number of elements in the array.

A12: 

```java
public static int isGuthrieSequence(int[] a) {  
    for (int i=0 ; i < a.length - 1; i++) {  
        int current = a[i];  
        int next = a[i+1];  
        if(current % 2 == 0) {  
            //event  
            if(next != current/2) {  
                return 0;  
            }  
        }  
        else {  
            //odd  
            if(next != (current*3) + 1) {  
                return 0;  
            }  
        }  
    }  
  
    //last number must 1  
    if(a[a.length -1] != 1) {  
        return 0;  
    }  
    return 1;  
}
```

---
Q13: 
The Stanton measure of an array is computed as follows. Count the number of 1s in the array. Let this count be n. The Stanton measure is the number of times that n appears in the array. For example, the Stanton measure of {1, 4, 3, 2, 1, 2, 3, 2} is 3 because 1 occurs 2 times in the array and 2 occurs 3 times.

  

Write a function named stantonMeasure that returns the Stanton measure of its array argument.

  

If you are  programming in Java or C#, the function prototype is

int stantonMeasure(int[ ] a)

  

If you are programming in C++ or C, the function prototype is

int stantonMeasure(int a[ ], int len) where len is the number of elements in the array.


A13:

```java
public static int stantonMeasure(int[ ] a) {  
    //find the 1  
    int one = 0;  
    int res = 0;  
    for(int i=0 ; i< a.length ; i++) {  
        if (a[i] == 1) {  
            one++;  
        }  
    }  
  
    for(int i=0 ; i< a.length ; i++) {  
        if (a[i] == one) {  
            res++;  
        }  
    }  
    return res;  
}
```

---

Q14:

The sum factor of an array is defined to be the number of times that the sum of the array appears as an element of the array. So the sum factor of {1, -1, 1, -1, 1, -1, 1} is 4 because the sum of the elements of the array is 1 and 1 appears four times in the array. And the sum factor of 

{1, 2, 3, 4} is 0 because the sum of the elements of the array is 10 and 10 does not occur as an element of the array. The sum factor of the empty array { } is defined to be 0.

  

Write a function named sumFactor that returns the sum factor of its array argument.

  

If you are programming in Java or C#, the function signature is

int sumFactor(int[ ] a)

  

If you are programming in C++ or C, the function signature is

int sumFactor(int a[ ], int len)  where len is the number of elements in the array.

A14:

```java
public static int sumFactor(int[ ] a) {  
    //sum the array  
    int sum = 0;  
    int count = 0;  
    for(int i=0 ; i < a.length; i++) {  
        sum = sum + a[i];  
    }  
  
    for(int i=0 ; i < a.length; i++) {  
        if (sum == a[i]) {  
            count = count + 1;  
        }  
    }  
  
    return count;  
  
}
```

---

Q15:

Consider the following algorithm

Start with a positive number n

if n is even then divide by 2

if n is odd then multiply by 3 and add 1

continue this until n becomes 1

  

The Guthrie index of a positive number n is defined to be how many iterations of the above algorithm it takes before n becomes 1.

  

For example, the Guthrie index of the number 7 is 16 because the following sequence is 16 numbers long.

22, 11, 34, 17, 52, 26, 13, 40, 20, 10, 5, 16, 8, 4, 2, 1

  

It is easy to see that this sequence was generated by the above algorithm. Since 7 is odd multiply by 3 and add 1 to get 22 which is the first number of the sequence. Since 22 is even, divide by 2 to get 11 which is the second number of the sequence. 11 is odd so multiply by 3 and add 1 to get 34 which is the third number of the sequence and so on.

  

Write a function named guthrieIndex which computes the Guthrie index of its argument. Its signature is

  

int guthrieIndex(int n)


A15:

```java
public static int guthrieIndex(int n) {  
    ArrayList<Integer> arr = new ArrayList<>();  
    if(n <= 1) {  
        return 0;  
    }  
  
    int val = n;  
        while(val != 1) {  
        System.out.println(val);  
        if (val % 2 == 0) {  
            val = val/2;  
  
        }  
        else {  
            val = (val * 3) + 1;  
        }  
  
        arr.add(val);  
    }  
  
    return arr.size();  
  
}
```

---
Q16:

It is a fact that there exist two numbers x and y such that x! + y! = 10!. Write a method named solve10 that returns the values x and y in an array. The notation n! is called n factorial and is equal to n * n-1 * n-2 * ... 2 * 1, e.g., 5! = 5*4*3*2*1 = 120.

A16:

```java
public static int[] solve10() {
    int[] result = new int[2];
    for (int i = 0; i <= 10; i++) {
        for (int j = 0; j <= 10; j++) {
            if (factorial(i) + factorial(j) == factorial(10)) {
                result[0] = i;
                result[1] = j;
                return result;
            }
        }
    }
    return result;
}

private static int factorial(int n) {
    int result = 1;
    for (int i = 2; i <= n; i++) {
        result *= i;
    }
    return result;
}
```

---

Q17:

An array can hold the digits of a number. For example the digits of the number 32053 are stored in the array {3, 2, 0, 5, 3}. Write a method call repsEqual that takes an array and an integer and returns 1 if the array contains only the digits of the number in the same order that they appear in the number. Otherwise it returns 0.

  

If you are programming in Java or C#, the function prototype is

   int repsEqual(int[ ] a, int n)

  

If you are programming in C++ or C, the function prototype is

   int repsEqual(int a[ ], int len, int n) where len is the number of elements in the array.

A17:

```java
public static int repsEqual(int[ ] a, int n){  
    if(a.length == 0) {  
        return 1;  
    }  
    String val = "";  
    String res = String.valueOf(n);  
  
    int k = 0;  
    while(a[k] == 0) {  
        k++;  
    }  
  
    for(int i = k ; i< a.length;i++) {  
        val = val + a[i];  
    }  
  
    if(val.equals(res)) {  
        return 1;  
    }  
    return 0;  
}
```

---

Q: 18

An array is called centered-15 if some consecutive sequence of elements of the array sum to 15 and this sequence is preceded and followed by the same number of elements.  For example 

{3, 2, 10, 4, 1, 6, 9} is centered-15 because  the sequence 10, 4, 1 sums to 15 and the sequence is preceded by two elements (3, 2) and followed by two elements(6,9).

  

Write a method called isCentered15 that returns 1 if its array argument is centered-15, otherwise it returns 0.

  

If you are programming in Java or C#, the function prototype is

   int isCentered15(int[ ] a)

  

If you are programming in C++ or C, the function prototype is

   int isCentered5(int a[ ], int len) where len is the number of elements in the array.

A: 18

```java
public static  int isCentered15(int[] a) {  
    for (int i = 0; i <=(a.length / 2); i++) {  
        int sum = 0;  
        for (int j = i; j < (a.length - i); j++) {  
            sum += a[j];  
        }  
        if (sum == 15)  
            return 1;  
    }  
    return 0;  
}
```

---

Q: 19

A perfect number is one that is the sum of its factors, excluding itself. The 1st perfect number is 6 because 6 = 1 + 2 + 3. The 2nd perfect number is 28 which equals 1 + 2 + 4 + 7 + 14. The third is 496 = 1 + 2 + 4 + 8 + 16 + 31 + 62 + 124 + 248. In each case, the number is the sum of all its factors excluding itself. 

  

Write a method named henry that takes two integer arguments, i and j and returns the sum of the ith and jth perfect numbers. So for example, henry (1, 3) should return 502 because 6 is the 1st perfect number and 496 is the 3rd perfect number and 6 + 496 = 502.

  

The function signature is

    int henry (int i, int j)

  

You do not have to worry about integer overflow, i.e., you may assume that each sum that you have to compute can be represented as a 31 bit integer. Hint: use modulo arithmetic to determine if one number is a factor of another.

A: 19

first we need to find the perfect sequence. So, first , we will do the 2. and then keep increasing the number.

```java
public static int henry(int i, int j) {  
    if(i < 0 || j <0) {  
        return 0;  
    }  
    int counter = 1;  
    int perfectSequence = 2;  
    int perfectFirstValue = 0;  
    int perfectSecondValue = 0;  
  
    while(true) {  
        //find the first perfect number  
        int sum = 0;  
        for(int k = 1 ; k < perfectSequence; k++) {  
            if(perfectSequence % k == 0) {  
                sum = sum + k;  
            }  
        }  
        if(sum == perfectSequence) {  
            //yes, this is perfect number  
            if(counter == i) {  
                perfectFirstValue = perfectSequence;  
            }  
            if (counter == j) {  
                perfectSecondValue = perfectSequence;  
            }  
  
            counter++;  
  
        }  
  
        if(perfectFirstValue != 0 && perfectSecondValue != 0) {  
            return perfectFirstValue + perfectSecondValue;  
        }  
        perfectSequence++;  
    }  
  
}
```

Q:20 

Write a method named isDivisible that takes an integer array and a divisor and returns 1 if all its elements are divided by the divisor with no remainder. Otherwise it returns 0.

  

If you are programming in Java or C#, the function signature is

    int isDivisible(int [  ] a, int divisor)

  

If you are programming in C or C++, the function signature is

    int isDivisible(int a[ ], int len, int divisor) where len is the number of elements in the array.

A:20

```java
public static int isDivisible(int[] a,int divisor) {
	for(int i = 0; i < a.length; i++) {
		if(a[i] % divisor != 0) {
			return 0;
		}
	}
	return 1;
}
```

---

Q: 21

An array is defined to be n-unique if exactly one pair of its elements sum to n. For example, the array {2, 7,  3, 4} is 5-unique because only a[0] and a[2] sum to 5. But the array {2, 3, 3, 7} is not 5-unique because a[0] + a[1] = 5 and a[0] + a[2] = 5.  

  

Write a function named isNUnique that returns 1 if its integer array argument is n-unique, otherwise it returns 0. So isNUnique(new int[ ]{2, 7, 3, 4}, 5) should return 1 and 

isNUnique(new int[] {2, 3, 3, 7}, 5) should return 0.

  

If you are programming in Java or C#, the function signature is

    int isNUnique(int[ ] a, int n)

  

If you are programming in C or C++, the function signature is

    int isNUnique(int a[ ], int len, int n) where len is the number of elements in the array.


A21:

```java
public static int isNUnique(int[ ] a, int n) {  
    int count = 0;  
    for(int i=0; i< a.length-1;i++) {  
        for(int j=i+1 ; j<a.length; j++) {  
            if(a[i] + a[j] == n) {  
                count++;  
            }  
        }  
    }  
    if(count == 1) {  
        return 1;  
    }  
    return 0;  
}
```

---
Q: 22

Write a function named isSquare that returns 1 if its integer argument is a square of some integer, otherwise it returns 0. Your function must not use any function or method (e.g. sqrt) that comes with a runtime library or class library! 

  

The signature of the function is  
`int isSquare(int n)`

A: 22
```java
public static int isSquare(int n) {
	if(n < 0) {
		return 0;
	}
	int num = (int)Math.floor(Math.sqrt(n));
	if(num * num  == n) {
		return 1;
	}
	else {
		return 0;
	}
}
```

---
Q:23

A number with a base other than 10 can be written using its base as a subscript. For example, 10112  represents the binary number 1011 which can be converted to a base 10 number as follows:

(1 * 20) + (1 * 21) + (0 * 22) + (1 * 23) = 1 + 2 + 0 + 8 = 1110

  

Similarily, the base 3 number 1123 can be converted to base 10 as follows:

(2 * 30) + (1 * 31) + (1 * 32) = 2 + 3 + 9 = 1410

  

And the base 8 number 3258 can be converted to base 10 as follows:

(5 * 80) + (2 * 81) + (3 * 82) = 5 + 16 + 192 = 21310

  

Write a method named isLegalNumber that takes two arguments. The first argument is an array whose elements are the digits of the number to test. The second argument is the base of the number represented by the first argument. The method returns 1 if the number represented by the array is a legal number in the given base, otherwise it returns 0. 

  

For example the number 3214 can be passed to the method as follows:

        isLegalNumber(new int[] {3, 2, 1},  4)

This call will return 1 because 3214 is a legal base 4 number. 

  

However, since all digits of a base n number must be less than n, the following call will return 0 because 3716 is not a legal base 6 number (the digit 7 is not allowed)

      isLegalNumber(new int[] {3, 7, 1},  6)

  

If you are programming in Java or C#, the signature of the method is

int isLegalNumber(int[  ] a, int base)

If you are programming in C or C++, the signature of the method is 

int isLegalNumber(int a[ ], int len, int base) where len is the size of the array.

A: 21

```java
public static int isLegalNumber(int[] a, int base) {  
    for (int i=0 ; i < a.length; i++) {  
        if(a[i] >= base) {  
            return 0;  
        }  
    }  
    return 1;  
}
```

---

Q: 22

Using the <array, base> representation for a number described in the second question write a method named convertToBase10 that  converts its <array, base> arguments to a base 10 number if the input is legal for the specified base. If it is not, it returns -1.

A: 22

```java

public static int convertToBase10(int[ ] a, int base) {  
    int sum = 0;  
    int pow = 0;  
    for (int i= a.length -1; i >= 0; i--) {  
        if(a[i] >= base) {  
            return -1;  
        }  
        sum = (int) (sum + (a[i] * Math.pow(base,pow)));  
        pow++;  
    }  
    return sum;  
}

```

---
Q: 23

The depth of an integer n is defined to be how many muloples of n it is necessary to compute before all 10 digits have appeared at least onece in some multiple.

A: 23

```java
public static int depth(int n) {  
    HashSet<Character> set = new HashSet<>();  
    int deep = 1;  
    while(set.size() != 10) {  
        int val = n * deep;  
        String k = String.valueOf(val);  
        for(int i=0; i < k.length() ; i++) {  
            set.add( k.charAt(i));  
        }  
        deep++;  
    }  
    return (deep -1);  
}
```

---
Q: 24

Find zero in the array. If container return 0 else return 1.

A:24

```java
public static arrayHasNoZero(int[] a) {
	for(int i=0;i<a.length;i++) {
		if(a[i] == 0) {
			return 0;
		}
	}
	return 1;
}
```

---
Q25:

A simple pattern match on the elements of an array A can be defined using another array P. Each element n of P is negative or positive (never zero) and defines the number of elements in a sequence in A. The first sequence in A starts at A[0] and its length is defined by P[0]. The second sequence follows the first sequence and its length is defined by P[1] and so on. Furthermore, for n in P, if n is positive then the sequence of n elements of A must all be positive. Otherwise the sequence of abs(n) elements must all be negative. The sum of the absolute values of the elements of P must be the length of A.  For example, consider the array 

A = {1,  2,  3, -5, -5,  2, 3, 18}

If P = {3, -2, 3} then A matches P because 

i.  the first 3 elements  of A  (1, 2, 3) are positive (P[0] is 3 and is positive),  

ii. the next 2 elements of A (-5, -5) are negative (P[1] is -2 and is negative) 

iii. and the last 3 elements of A (2, 3, 18) are positive (P[2] is 3 and is positive)

Notice that the absolute values of the elements of P  sum to 8 which is the length of A. The array A also matches the following patterns:

{2, 1, -1, -1, 2, 1},  {1, 2, -1, -1, 1, 2},  {2, 1, -2, 3}, {1, 1, 1, -1, -1, 1, 1, 1}

In each case the sum of the absolute values is 8, which is the length of A and each sequence of numbers in A  defined in a pattern is negative or positive as required.

The array A = {1,  2,  3, -5, -5,  2, 3, 18} does not match the following patterns:

i. P = {4, -1, 3} (because the first 4 elements of A are not positive (A[3] is negative) as required by P)

ii. P = {2, -3, 3} (because even though the first 2 elements of A are positive, the next 3 are required to be negative but A[2] is positive which does not satisfy this requirement.)

iii. P = {8} (because this requires all elements of A to be positive and they are not.)

Please note: Zero is neither positive nor negative.

  

Write a function named matches which takes arrays A and P as arguments and returns 1 if A matches P. Otherwise it returns 0. You may assume that P is a legal pattern, i.e., the absolute value of its elements sum to the length of A and it contains no zeros. So do not write code to check if P is legal!

If you are programming in Java or C# the signature of the function is

int matches(int[ ] a, int[ ] p)

A25:

```java
public static int matches(int[ ] a, int[ ] p) {  
        int start = 0;  
  
        int len = 0;  
  
        for(int i=0; i<p.length;i++) {  
            len = len + Math.abs(p[i]);  
        }  
  
        if(len != a.length) {  
            return 0;  
        }  
  
        for(int i=0; i<p.length;i++) {  
            for (int j = start; j < Math.abs(p[i]) + start; j++) {  
  
                if ((p[i] > 0 && a[j] <= 0) || (p[i] < 0 && a[j] > 0)) {  
                    return 0;  
                }  
//   explain the code  
//                if(p[i] > 0) {  
//                    if(a[j] <=0) {  
//                        return  0;  
//                    }  
//                }  
//                else if (p[i] < 0) {  
//                    if(a[j] >0 ) {  
//                        return 0;  
//                    }  
//                }  
            }  
            start = start + Math.abs(p[i]);  
        }  
        return 1;  
  
    }
```

---
Q: 26

Define a stacked number to be a number that is the sum of the first n positive integers for some n. The first 5 stacked numbers are

1 = 1

3 = 1 + 2

6 = 1 + 2 + 3

10 = 1 + 2 + 3+ 4

15 = 1 + 2 + 3 + 4 + 5

  

Note that from the above we can deduce that 7, 8, and 9 are not stacked numbers because they cannot be the sum of any sequence of positive integers that start at 1.

Write a function named isStacked that returns 1 if its argument is stacked. Otherwise it returns 0. Its signature is:

int isStacked(int n);

So for example, isStacked(10) should return 1 and isStacked(7) should return 0.


A26:

```java
public static int isStacked(int n) {  
    var sum = 0;  
    for(int i = 1 ; i < n ; i++) {  
        sum = sum + i;  
        if(sum == n) {  
            return 1;  
        }  
    }  
    return 0;  
}
```

---

Q27:

Define an array to be sum-safe if none of its elements is equal to the sum of its elements. The array

a = {5, -5, 0} is not sum-safe because the sum of its elements is 0 and a[2] == 0. However, the array a = {5, -2, 1} is sum-safe because the sum of its elements is 4 and none of its elements equal 4.

  

Write a function named isSumSafe that returns 1 if its argument is sum-safe, otherwise it returns 0.

If you are writing in Java or C#, the function signature is

int isSumSafe(int[ ]a)

If you are writing in C++ or C, the function signature is

int isSumSafe(int a[ ], int len) where len is the number of elements in a.

For example,  isSumSafe(new int[ ] {5, -5, 0}) should return 0 and isSumSafe(new int[ ]{5, -2, 1}) should return 1. 

Return 0 if the array is empty.

A 27:

```java
public static int isSumSafe(int[] a) {
	if(a.length == 0) {
		return 0;
	}
	int sum = 0;
	for(int i = 0 ; i < a.length; i++) {
		sum = sum + a[i];
	}
	for(int i = 0 ; i < a.length; i++) {
		if(a[i] == sum) {
			return 0;
		}
	}
	return 1;
}
```

---

Q28:

Define a positive number to be isolated if none of the digits in its square are in its cube. For example 163 is n isolated number because 69*69 =  26569  and 69*69*69 = 4330747 and the square does not contain any of the digits 0, 3, 4 and 7 which are the digits used in the cube. On the other hand 162 is not an isolated number because 162*162=26244 and 162*162*162 = 4251528 and the digits 2 and 4 which appear in the square are also in the cube.

  

Write a function named isIsolated that returns 1 if its argument is an isolated number,  it returns 0 if its not an isolated number and it returns -1 if it cannot determine whether it is isolated or not (see the note below). The function signature is:

  

int isIsolated(long n)

  

Note that the type of the input parameter is long. The maximum positive number that can be represented as a long is 63 bits long. This allows us to test numbers up to 2,097,151 because the cube of 2,097,151 can be represented as a long. However, the cube of 2,097,152 requires more than 63 bits to represent it and hence cannot be computed without extra effort. Therefore, your function should test if n is larger than 2,097,151 and return -1 if it is. If  n is less than 1 your function should also return -1.

  

Hint: n % 10 is the rightmost digit of n, n = n/10 shifts the digits of n one place to the right.


A28: 
```java
public static int isIsolated(long n) {  
  
    if (n < 1 || n > 2097151) {  
        return -1;  
    }  
    long square = n * n;  
    long cube = n * n * n;  
    String strSquare = String.valueOf(square);  
    String strCube = String.valueOf(cube);  
    for(int i=0 ; i< strSquare.length();i++) {  
        for(int k=0; k < strCube.length();k++) {  
            if(strSquare.charAt(i) == strCube.charAt(k)) {  
                return 0;  
            }  
        }  
    }  
    return 1;  
}
```

---

Q29:

An array is called vanilla if all its elements are made up of the same digit. For example {1, 1, 11, 1111, 1111111} is a vanilla array because all its elements use only the digit 1. However, the array {11, 101, 1111, 11111} is not a vanilla array because its elements use the digits 0 and 1. Write a method called isVanilla that returns 1 if its argument is a vanilla array. Otherwise it returns 0.

  

If you are writing in Java or C#, the function signature is

   int isVanilla(int[ ] a)

  

If you are writing in C or C++, the function signature is

  int isVanilla(int a[ ], int len) where len is the number of elements in the array a.

A29:

```java
public static int isVanilla(int[] a) {  
    if(a.length == 0) {  
        return 1;  
    }  
  
    String str = "";  
    for(int i=0; i < a.length; i++) {  
        str = str + String.valueOf(Math.abs(a[i]));  
    }  
  
    char first = str.charAt(0);  
    for(int i=1; i < str.length(); i ++) {  
        if(first != str.charAt(i)) {  
            return 0;  
        }  
    }  
    return 1;  
}
```

--- 

Q:  30

Define an array to be trivalent if all its elements are one of three different values. For example, {22, 19, 10, 10, 19, 22, 22, 10} is trivalent because all elements are either 10, 22, or 19. However, the array {1, 2, 2, 2, 2, 2, 2} is not trivalent because it contains only two different values (1, 2). The array {2, 2, 3, 3, 3, 3, 2, 41, 65} is not trivalent because it contains four different values (2, 3, 41, 65). 

  

Write a function named isTrivalent that returns 1 if its array argument is trivalent, otherwise it returns 0.

  

If you are writing in Java or C#, the function signature is

   int isTrivalent (int[ ] a)

  

If you are writing in C or C++, the function signature is

  int isTrivalent(int a[ ], int len) where len is the number of elements in the array a.

  

Hint: Remember that the elements of the array can be any value, so be careful how you initialize your local variables! For example using -1 to initialize a variable won’t work because -1 might be one of the values in the array.

A: 30

```java
public  static   int isTrivalent (int[ ] a) {  
    HashSet<Integer> data = new HashSet<>();  
  
    for(int i=0 ; i< a.length;i++) {  
        data.add(a[i]);  
    }  
    if(data.size() == 3) {  
        return 1;  
    }  
    return 0;  
}
```

---

Q: 31

An integer array is defined to be sequentially-bounded if it is in ascending order and each value, n,  in the array  occurs less than n times in the array. So {2, 3, 3, 99, 99, 99, 99, 99} is sequentially-bounded because it is in ascending order and the value 2 occurs less than 2 times, the value 3 occurs less than 3 times and the value 99 occurs less than 99 times. On the other hand, the array {1, 2, 3} is not sequentially-bounded because the value 1 does not occur < 1 times. The array {2, 3, 3, 3, 3} is not sequentially-bounded because the maximum allowable occurrences of 3 is 2 but 3 occurs 4 times. The array {12, 12, 9} is not sequentially-bounded because it is not in ascending order.

A: 31

```java
public static  int isSequentiallyBounded(int[ ] a) {  
    for(int i=0 ; i<a.length;i++) {  
        if(a[i] < 0) {  
            return 0;  
        }  
        int count = 0;  
        for(int j=0; j < a.length; j++) {  
            if(a[j] == a[i]) {  
                count++;  
            }  
        }  
        if(count > a[i]) {  
            return 0;  
        }  
    }  
    return 1;  
}
```

---
Q: 32

An array is defined to be minmax-disjoint if the following conditions hold:

a. The minimum and maximum values of the array are not equal.

b. The minimum and maximum values of the array are not adjacent to one another.

c. The minimum value occurs exactly once in the array. 

d. The maximum value occurs exactly once in the array.

  

For example the array {5, 4, 1, 3, 2} is minmax-disjoint because 

a. The maximum value is 5 and the minimum value is 1 and they are not equal.

b. 5 and 1 are not adjacent to one another

c. 5 occurs exactly once in the array

d. 2 occurs exactly once in the array

  

Write a function named isMinMaxDisjoint that returns 1 if its array argument is minmax-disjoint, otherwise it returns 0.

  

If you are programming in Java or C#, the function signature is

int isMinMaxDisjoint(int[ ] a)

  

If you are programming in C or C#, the function signature is

int isMinMaxDisjoint(int a[ ], int len) where len is the number of elements in the array.

A: 32

```java
public static  int isMinMaxDisjoint(int[ ] a) {  
    if(a.length == 0) {  
        return 0;  
    }  
    int min = a[0];  
    int max = a[0];  
    int minPos = 0;  
    int maxPos = 0;  
    int maxCount = 0;  
    int minCount = 0;  
    for(int i=1 ; i< a.length; i++) {  
        if(a[i] > max) {  
            max = a[i];  
            maxPos = i;  
        }  
        if(a[i] < min) {  
            min = a[i];  
            minPos = i;  
        }  
    }  
  
    for(int i=0 ; i< a.length;i++) {  
        if(a[i] == max) {  
            maxCount++;  
            if(maxCount > 1) {  
                return 0;  
            }  
        }  
  
        if(a[i] == min) {  
            minCount++;  
            if(minCount > 1) {  
                return 0;  
            }  
        }  
    }  
  
    if(maxPos == minPos || (maxPos + 1) == minPos || (maxPos -1) == minPos) {  
        return 0;  
    }  
  
    return 1;  
}
```

---

Q: 33

The number 124 has the property that it is the smallest number whose first three multiples contain the digit 2. Observe that 

124*1 = 124, 124*2 = 248, 124*3 = 372 and that 124, 248 and 372 each contain the digit 2. It is possible to generalize this property to be the smallest number whose first n multiples each contain the digit 2. Write a function named smallest(n) that returns the smallest number whose first n multiples contain the digit 2. Hint: use modulo base 10 arithmetic to examine digits.

  

Its signature is

int smallest(int n)


A: 33

ဒီမေးခွန်းကို နားလည်ဖို့ မနည်းဖတ်ရတယ်။​ သူပြောချင်တာက ပေးလိုက်သည့် နံပတ် အကြိမ် အတိုင်း မြှောက် ဖို့ လိုတယ်။ အဲဒီ ထဲမှာ တောက်လျှောက် ၂ ပါ ရမယ်။ ဥပမာ

n = 3 ဆိုရင်

124 x 1 = 124
124 x 2 = 248
124 x 3 = 372

ဒါကြောင့် loop က တောက်လျောက် ပတ်နေမယ် 2 မပါဘူး ဆိုတာ နဲ့ loop က ထွက်။ 

အစ ၁ ကနေ ပတ်။​ ၂ မပါဘူးဆိုရင် i ကို ၁ ပေါင်း ထက်တွက်။

```java
public static int smallest(int n) {  
    int i = 124;  
    while (true) {  
        int k = 1;  
        for (int j = 1; j <= n; j++) {  
            if (!containsTwo(i * j)) {  
                break;  
            }  
            k++;  
        }  
        if (k > n) {  
            return i;  
        }  
        i++;  
    }  
}  
  
private static boolean containsTwo(int num) {  
    while (num > 0) {  
        if (num % 10 == 2) {  
            return true;  
        }  
        num /= 10;  
    }  
    return false;  
}
```

---

Q: 34

Define a cluster in an integer array to be a maximum sequence of elements that are all the same value. For example, in the array {3, 3, 3, 4, 4, 3, 2, 2, 2, 2, 4} there are 5 clusters, {3, 3, 3}, {4, 4}, {3}, {2, 2, 2, 2} and {4}. A cluster-compression of an array replaces each cluster with the number that is repeated in the cluster. So, the cluster compression of the previous array would be {3, 4, 3, 2, 4}. The first cluster {3, 3, 3} is replaced by a single 3, and so on.

  

Write a function named clusterCompression with the following signature

  

If you are programming in Java or C#, the function signature is

int[ ] clusterCompression(int[ ] a)

  

If you are programming in C++ or C, the function signature is

int *clusterCompression(int a[ ], int len) where len is the length of the array. 

  

The function returns the cluster compression of the array a. The length of the returned array must be equal to the number of clusters in the original array! This means that someplace in your answer you must dynamically allocate the returned array.

  

In Java or C# you can use 

int[ ] result = new int[numClusters];

  

In C or C++ you can use 

int *result = (int *)calloc(numClusters, sizeof(int));


A: 34

ArrayList နဲ့ ဖြေလို့ ရပေမယ့် မေးခွန်းမှာ `int[ ] result = new int[numClusters];` ကို သုံးရမယ်လို့ ပြောထားတယ်။​​ ဒါကြောင့် number of clusters ကို အရင် ရှာရတယ်။

```java
public static int[ ] clusterCompression(int[ ] a) {  
    //find the number of cluster  
    if(a.length == 0) {  
        int[] empty = {};  
        return empty;  
    }  
  
    int numberClusters = 1;  
    int prev = a[0];  
    for(int i =1 ; i< a.length; i++) {  
        if(prev != a[i]) {  
            prev = a[i];  
            numberClusters++;  
        }  
    }  
    int[ ] result = new int[numberClusters];  
  
    prev = a[0];  
    result[0] = a[0];  
    int index = 0;  
    for(int i =1 ; i< a.length; i++) {  
        if(prev != a[i]) {  
            prev = a[i];  
            index++;  
            result[index] = a[i];  
        }  
    }  
    return result;  
}
```

---

Q: 35

Define an array to be a railroad-tie array if the following three conditions hold

  

a. The array contains at least one non-zero element 

b. Every non-zero element has exactly one non-zero neighbor 

c. Every zero element has two non-zero neighbors. 

  

For example, {1, 2, 0, 3, -18, 0, 2, 2} is a railroad-tie array because 

  

a[0] = 1 has exactly one non-zero neighbor (a[1])

a[1] = 2 has exactly one non-zero neighbor (a[0])

a[2] = 0 has two non-zero neighbors (a[1] and a[3])

a[3] = 3 has exactly one non-zero neighbor (a[4])

a[4] = -18 has exactly one non-zero neighbor (a[3])

a[5] = 0 has two non-zero neighbors (a[4] and a[6])

a[6] = 2 has exactly one non-zero neighbor (a[7])

a[7] = 2 has exactly one non-zero neighbor (a[6])

  

The following are not railroad-tie arrays

  

{1, 2, 3, 0, 2, 2}, because a[1]=2 has two non-zero neighbors. 

{0, 1, 2, 0, 3, 4}, because a[0]=0 has only one non-zero neighbor (it has no left neighbor)

{1, 2, 0, 0, 3, 4}, because a[2]=0 has only one non-zero neighbor (a[1])

{1}, because a[0]=1 does not have any non-zero neighbors.

{}, because the array must have at least one non-zero element

{0}, because the array must have at lease one non-zero element.

  

Write a function named isRailroadTie which returns 1 if its array argument is a railroad-tie array; otherwise it returns 0.

  

If you are writing in Java or C#, the function signature is

int isRailroadTie(int[ ] a)






A 35:

```java
public static int isRailroadTie (int [] a) {  
  
    if (a.length <= 1) {  
        return 0;  
    }  
  
    if (a[0] == 0 || a[a.length - 1] == 0) {  
        return 0;  
    }  
    int nonzerocount = 0;  
    for(int i=0 ; i < a.length; i++) {  
        if(a[i] != 0) {  
            nonzerocount++;  
        }  
    }  
  
    if(nonzerocount == 0) {  
        return 0;  
    }  
  
    if(a[0] == 0 || a[a.length - 1] == 0) {  
        return 0;  
    }  
  
    for(int i=0 ; i < a.length; i++) {  
  
        if(a[i] != 0) {  
            //find the  
            if(i == 0) {  
                if(a[i+1] == 0) {  
                    return 0;  
                }  
  
            }  
            else if(i == a.length -1) {  
                if(a[i-1] == 0) {  
                    return 0;  
                }  
            }  
            else {  
                int left = a[i-1];  
                int right = a[i+1];  
                //left or right must have at least non-zero  
                if(left !=0 && right != 0) {  
                    return 0;  
                }  
  
            }  
        }  
        else {  
            if(a[i-1] == 0) {  
                return 0;  
            }  
            if(a[i+1] == 0) {  
                return 0;  
            }  
        }  
    }  
  
    return 1;  
}
```