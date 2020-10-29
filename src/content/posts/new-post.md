---
template: blog-post
title: Recursion and How It Works
slug: /recursion
date: 2020-05-09T05:53:16.102Z
description: Neon
featuredImage: /assets/recursion_tree.jpg
---
Recursion is a concept and to understand it, you must understand recursion, which is a concept. Bad jokes aside, recursion is a fundamental piece of any software engineer’s toolbox and being able to implement it in even basic situations will be beneficial and improve your overall understanding of computer science. Recursion can often be confusing because of what it symbolizes, therefore I will start with a contrived but concrete example. 

Let’s say you are a Chief Detective looking for a missing person. Every house in a specific 10 mile radius in outside your city may contain said person. You have some basic description of who you are looking for but no idea where to start. There are a few other detectives from your department to help you with your search as well. These detectives, however, are not horribly bright. You give each detective, let’s say you have 10, a square mile to search and very explicit instructions which read something like this:

1.	Start by searching the house.
2.	If this house is the last house in your assigned area and does not contain the criminal, then you can deduce the criminal is not in your area, pass this information to the next detective.
3.	If this house is empty but not the last house, then tell the next detective to repeat the search with the next house using the same procedure that you have defined here.
4.	If this house does contain the missing person, then notate that and pass it up the chain of command until all of the search results come back to you (the Chief Detective).

Or dictated in JavaScript code:
~~~
function searchBuildings(house) {
    if (house === lastHouseInArea && house !== houseWithMissingPerson) {
        return false;
    } 
    else if (house === empty && house !== lastHouseInArea) {
        return searchBuildings(house.next);
    }
    else if (house === houseWithMissingPerson) {
        return true;
    }
}
~~~

That’s it! Recursion explained in the most basic terms is simply when a function calls itself within the body of its own declaration. In our case, this is when the detective repeats the same procedure for the next house (house.next which is just a reference to the next house).  Technically, this next search is just another search waiting to be completed in the long line of searches in the area. Your plan is to divide-and-conquer which describes how the recursive function is implemented. When one of the other two conditions are met (the missing person is in the house or it is the last house and doesn’t contain the person) then your initial search, and all the associated “next” searches, will end (or return if we are referencing code). 

Recursion is often hard to break down because it can get complicated as the problems you are trying to solve get more complex. More inputs, more factors, more cases, all compound to make recursion sometimes less efficient than a solution that is iterative. Practically speaking, recursion is just another technique to allow you to write more efficient code and solve problems in your programs. Thinking recursively, even if it is difficult at the beginning of your journey into software engineering, will pay dividends because you can analyze a problem multiple ways and often times the recursive solution is simple, eloquent, and occasionally very fast.
Problems that deal with recursion can be split into two pieces, a recursive case and a base case. In our above example, the instances where either the detective was on the last house in their area and the person was not found or the house did contain the missing person would be considered the base cases. This is because they have a finite result that returns an actual value. In the latter instance this value would be false and in the former, true. Recursive functions need to have these base cases because otherwise the self-referential calls would go on endlessly. Here is a meme featuring Drake which may either help or confuse:

![Drake](/assets/drake.png "Drake Meme to Explain")

In the recursive case, the function itself is simply called again. This occurs in the condition where the detective finds that the house is empty but there are still more houses to search. The detective then repeats the same function as he did before. These continual “calls” to the search “stack” can be thought of as just instances of a search – which remember are not relevant until all searches are complete. If you think of it, this makes sense. You don’t really care about the result of an individual house search if it is not the last one or if it contains the missing person. You can put it on the backburner so to speak and continue on with your search and not care about the result right now. That is essentially how the call stack for recursive functions works. Each time the function is called an additional time, another result is popped onto the stack and the result is not evaluated until a base case is reached. Once a base case is met all the corresponding calls return depending on how the function is structured. For our detectives this is either false or true depending on what the result of the final search is, or if any houses along the way contain the missing person. 

Recursion is not easy to understand conceptually. However, not having complete mastery of a concept does not mean you cannot apply and learn it as you are developing as a software engineer. For the most part, use of recursion will be evident because you can identify a base case and a method by which to move toward it. Is there a condition that will inevitably and eventually be met? Will the inputs remain structured so that this will be the case? These types of questions will get you into a recursive mindset. Be careful though, once you start to use recursion then..

![Infinite](/assets/infinite_recursion.png "Infinite Recursion") 