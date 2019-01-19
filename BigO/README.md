# VI | Big O

## 1. The following code computes the product of a and b. What is its runtime?

### Step 1. The problem:
```
int product(int a, int b)
{
	int sum = 0;
	for(int i = 0; i < b; i++)
	{
		sum += a;
	}
	return sum;
}
```

### Step 2. The analysis:
This is a straightforward problem. The for loop is the most costly part of the function and it is executed b times. This means the function is O(b), or more conventionally, `O(n)`.

### Step 3. The correct answer and reasoning:
O(b), the for loop just iterates through b;

## 2. The following code computes a^b. What is its runtime?

### Step 1. The problem:
```
int power(int a, int b)
{
	if(b < 0)
		return 0; // error
	else if(b == 0)
		return 1;
	else
		return a * power(a, b - 1);
}
```

### Step 2. The analysis:
This problem is only slightly more difficult than the last, due to the lack of straightforward for loops that tell you exactly how many times they will run. This is a recursive function, which decreases b by one each time it runs, up until the base case of `b == 0`. This function will run b + 1 times, or O(b + 1). Dropping the constant and replacing b with the conventional n leaves us with `O(n)` runtime.

### Step 3. The correct answer and reasoning:
O(b). The recursive code iterates through b calls, since it subtracts one at each level.

## 3. This code computes a % b. What is its runtime?

### Step 1. The problem:
```
int mod(int a, int b)
{
	if(b <= 0)
		return -1;
	int div = a / b;
	return a - div * b;
}
```

### Step 2. The analysis:
This problem sees another increase in difficulty due to the change in operator to division instead of addition or subtraction. The case of `b <= 0` is only there to catch Div0 errors, and does not affect the runtime. Each time the function runs it will calculate div, and then the return statement. Since this runs only once it gives us a constant, or `O(1)` runtime.

### Step 3. The correct answer and reasoning:
O(1). It does a constant amount of work.

## 4. The following code performs integer division. What is its runtime (assume a and b are both positive)?

### Step 1. The problem:
```
int div(int a, int b)
{
	int count = 0;
	int sum = b;
	while(sum <= a)
	{
		sum += b;
		count++;
	}
	return count;
}
```

### Step 2. The analysis:
This code adds b to b each loop until b is greater than or equal to a. We can assume that if a is less than b, we will have a constant run time, because the while loop will do one comparison, and terminate. Otherwise, if a is greater than b, the loop will run a / b times. This leaves us with an `O(a/b)` runtime. We cannot simplify this to be in terms of n, because we don't know whether a or b will be the dominant term for any given function call.

### Step 3. The correct answer and reasoning:
O(a/b). The variable count will eventually equal a/b. The while loop iterates count times. Therefore, it iterates a/b times.
