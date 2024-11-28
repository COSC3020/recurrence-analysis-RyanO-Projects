# Recurrence Analysis -- Mystery Function

Analyze the running time of the following recursive procedure as a function of
$n$ and find a tight big $O$ bound on the runtime for the function. You may
assume that each operation takes unit time. You do not need to provide a formal
proof, but you should show your work: at a minimum, show the recurrence relation
you derive for the runtime of the code, and then how you solved the recurrence
relation.

```javascript
function mystery(n) {
    if(n <= 1)
        return;
    else {
        mystery(n / 3);                           // Recursive call (n/3)
        var count = 0;
        mystery(n / 3);                           // Recursive call (n/3)
        for(var i = 0; i < n*n; i++) {            // Loop over n^2
            for(var j = 0; j < n; j++) {          // Loop over n
                for(var k = 0; k < n*n; k++) {    // Loop over n^2
                    count = count + 1;
                }
            }
        }
        mystery(n / 3);                           // Recursive call (n/3)
    }
}
```

Add your answer to this markdown file. [This
page](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/writing-mathematical-expressions)
might help with the notation for mathematical expressions.

# Recurrence Relation
There are 3 recursive calls to the function of size (n/3) so we have 3T(n/3). We also have three nested loops of $n^2, n$, and $n^2$ that total to $n^5$ for an additional time complexity of $n^5$. Our recurrence relation then should look like,

$T(n) = 3T(n/3) + n^5$.

## Solving by Master Theorem
$T(n) = 3T(n/3) + n^5$

a=3, b=3, f(n) = $n^5$

$log_b(a) = log_3(3) = 1$

$n^5 > n^1 = f(n) > n^{log_b(a)}$

So, T(n) = f(n) = $O(n^5)$


I used [this article](https://www.programiz.com/dsa/master-theorem) to help me understand how to use the Master Theorem for the recurrence relation because substitution was too confusing for me in this case. Other than that I certify that I have listed all sources used to complete this exercise, including the use of any Large Language Models. All of the work is my own, except where stated otherwise. I am aware that plagiarism carries severe penalties and that if plagiarism is suspected, charges may be filed against me without prior notice.
