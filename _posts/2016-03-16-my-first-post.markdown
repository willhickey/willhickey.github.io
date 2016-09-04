---
layout: post
title:  "Project Euler #4"
date:   2016-03-16 13:43:21 -0600
categories: jekyll update
---
Here's my code to solve [Project Euler][Project-Euler] problem #4

{% highlight python %}
def isPalindrome(inputString):
	if inputString==inputString[::-1]:
		return True
	else:
		return False
#print isPalindrome(str(45654))
#'nested for loop'
maxPalindromeProduct=0
for i in range(100,1000):
	for j in range(100,1000):
		if isPalindrome(str(i*j)):
			if i*j>maxPalindromeProduct:
				maxPalindromeProduct=i*j
			#print str(i)+'*'+str(j)+' = '+str(i*j)+' is a palindrome!'
print str(maxPalindromeProduct)+' is the largest palindrome product!'

{% endhighlight %}

[Project-Euler]: https://projecteuler.net/

!(https://github.com/skammlade/skammlade.github.io/vlcsnap-2016-02-13-16h29m47s64.png)