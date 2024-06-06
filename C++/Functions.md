
```c++
int addNumber(int num1, int num2) {
	int sum = num1 + num2;
	return sum;
}
```


# Forward declaration
To tell the compiler that the function exist before it is actually defined.
This can also be used when you have multiple files. Function in other files are not recognize by other files so forward declaration help to solve this issue.
```c++
int add(int x, int y);

int main ()
{
	std::cout << add(1, 2) << '\n';
	return 0;
}

int add(int x, int y) 
{
	return x + y;
}
```




