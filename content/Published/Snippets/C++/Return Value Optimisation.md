---
tags: snippets, cpp, compiler, optimisation
alias: Copy Elision, RVO
publish: true
---

# Table of contents

- [[#What is Copy Elision?|What is Copy Elision?]]
- [[#Why should I care?|Why should I care?]]
- [[#When does it happen, and how?|When does it happen, and how?]]
- [[#References|References]]

## What is Copy Elision?

> Copy elision refers to a compiler optimization technique that eliminates unnecessary copying of objects

[https://en.wikipedia.org/wiki/Copy_elision](https://en.wikipedia.org/wiki/Copy_elision)

## Why should I care?

Copying objects can object be expensive (depending on the size of the data), to avoid an expensive copy you can develop a good habit of structuring your code in such a way the compiler can properly reason about the data it is working with.

## When does it happen, and how?

Run the code: [http://cpp.sh/7hgdg](http://cpp.sh/7hgdg)

```cpp
#include <iostream>

class Example
{
public:
	Example() { std::cout << "Constructor" << std::endl; }
	~Example() { std::cout << "Destructor" << std::endl; }

	Example(const Example& Other)
	{
		std::cout << "Copy Constructor" << std::endl;
		IntVal = Other.IntVal;
	}

	int IntVal;
};

Example	CopyElided()
{
	Example Local;
	Local.IntVal = 1;
	return	Local;
}

Example	CopyNotElided(int PickEven)
{
	Example Return1;
	Example Return2;

	if (PickEven % 2 == 0)
	{
		Return1.IntVal = 1;
		return Return1;
	}
	else
	{
		Return2.IntVal = 2;
		return Return2;
	}
}

Example	CopyNotElided_Fixed(int PickEven)
{
	Example Result;

	if (PickEven % 2 == 0)
	{
		Result.IntVal = 1;
	}
	else
	{
		Result.IntVal = 2;
	}
	
	return Result;
}

int main()
{
	//Example temp1 = CopyElided();
	//Example temp2 = CopyNotElided(2);
	//Example temp3 = CopyNotElided_Fixed(2);
	return 0;
}
```

## References

- [https://en.cppreference.com/w/cpp/language/copy_elision](https://en.cppreference.com/w/cpp/language/copy_elision)
- [https://en.wikipedia.org/wiki/Copy_elision](https://en.wikipedia.org/wiki/Copy_elision)