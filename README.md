# Junior Implmentation Developer Assessment 
### Sean Michael Feiner

#### May 7th, 2021

##### Portfolio: https://www.seanmichael.dev/
##### Github: https://github.com/sameghosts
##### https://www.linkedin.com/in/seanmichael-feiner/
---
The purpose of this pre-screening assessment is to determine if I will continue with an interview at the discretion of the hiring manager. Please see answers in this markdown as well as original test document, description of contract document, and a txt file version of my answers. 

All solutions / answers are to the best of my ability and when I make a point of clarification I note it in text or code commenting. Please feel free to contact me by email (seanfeiner.brown@gmail.com) or submit a pull request to this repository if you have questions, concerns or feedback. 

---
## Assessment

### Multiple Choice

####  1. Which of the following elements should be used to open a new webpage?
```
a. <button>
b. <a href="https://audioeye.com">
c. <div class="button">
d. <a href="#">
e. <input type="button">
```
#### Solution: Choice b. Given that we can assume we are using vanilla HTML / Javascript and not an advanced front-end framework with routing technologies (like JSX in React / Next), the link element / "A" tag is the most correct answer for what should open a new page. d. will act as a dead link and the buttons and div class are not enough without added javascript to launch a new page. 

#### 2. Which of the following elements should be used to open modal or dialog?
```
a. <button>
b. <a href="https://audioeye.com">
c. <div class="button">
d. <a href="#">
e. <input type="button">
```
#### Solution: Choices a. c. and e., where a. is what my gut says most correct. -- This is a tricky question. Technically any HTML element could be used to open a dialog or modal (which have slightly different use cases / user experience principles). Most often convention would say it would be a button or link and a would be the best case especially since we could assign it a unique class (unlike the div as it currently has a "button" class attrribute). 

#### 3. Which of the following elements should be used scroll to the top of a page?
```
a. <button>
b. <a href="https://audioeye.com">
c. <div class="button">
d. <a href="#">
e. <input type="button">
```
#### Solution: d.

#### 4. Which of the following options present an accessible input format?
```
a. <label>Do you like peas?
 <input type="text" name="peas">
</label>
b. <label>Do you like peas?</label>
 <input type="text" name="peas" id="pods">
c. <label for="peas">Do you like peas?</label>
<input type="text" name="peas" id="pods">
d. <label for="pods">Do you like peas?</label>
<input type="text" name="peas" id="pods">
e. <input type=”text” aria-label=”Do you like peas?”>
```
#### Solution: e.

#### 5. In CSS, what is the correct option to select on the paragraphs with the class name “warning” using the code snippet below?
```
// Code Snippet:
<p class="warning">Don't do it.</p>
<p>Do it.</p>
<p class="warning">Nooo, don't do it.</p>
```
```
a. warning {}
b. .warning {}
c. #warning {}
d. p {}
e. none
```
#### Solution: b. .warning (in css class selections are called with / are proceeded by "." and ids are called with "#")

___
### Short Answers

#### Question 6
```
Write a jQuery or JS function that would allow a <div> element with a click event listener
to be operated using keyboard controls`
````
#### Solution
````
// Given a div element that has a click event listener, we can add a similar event listener for accessability purposes using a keyboard.
    // This is useful for screen readers and navigation between elements using such technology moving between elements with tab.

//For the purposes of this question I am going to assume the html and click function / handler are already written. 
Process:
//Get document element assign to variable. can be done by class / id / or by tag 
//add event listener for keydown with a callback event function for the particular key and if key is pressed have variable call click 

const keyboardDiv = document.getElementsByClassName('accessibleDiv');

//here we have the standard click this is more psuedocode

keyboardDiv.addEventListener('click', ()=>{
    //do something
    return 
});

// our accessible handler, can be enter or any other, and also a combination, of keys. 
keyboardDiv.addEventListener('keydown', (e)=> {
    if (e.code === 'Enter') {
    keyboardDiv.click();
    }
});

````

#### Question 7
```
Write a jQuery or JS function that would give empty heading elements (<h1></h1>,
<h2></h2>…)a “role” attribute value of “presentation”
```
#### Solution
```
//Given empty heading elements we may have to write a helper function to determine if the heading elements are empty. This could be done with a conditional / ternary 

//Assign variable for particular document heading element
    //We could do all of these for each heading type (eg h1, h2, h3)
    // With a Query Selector we could also filter out just the empty ones, for ease I am showing how to add to all but noting where we would create a loop to check and only apply attribute to empty heading tags
    
const head1s = document.getElementsByTagName("h1");
const head2s = document.getElementsByTagName("h2");

//Here we need to check to see if the element is empty. we could do this with loops or mass apply.



// For Each mass apply 
head1s.forEach(h1 => h1.setAttribute("role", "presentation"));

// For each with check if empty

head2s.forEach(h2 => {
if (h2.innerHTML === ''){
h2.setAttribute("role", "presentation");
}
});

```

#### Question 8
````
Write a jQuery or JS function that takes two integer parameters. Starting with the sum of
your two parameters, print a countdown to the console (one second at a time) until the logs
reach zero
````
#### Solution
````
// I am going to show an iterative / looping method. 

const sumCountdown = (a, b) => {
    let sum = a + b;
    console.log(`Initial sum ${sum}`)
    for (sum; sum>=0; sum--){
        console.log(sum)
    }
}

// call the sumCountdown function with two variables / paramaters eg 
    // sumCountdown(5,6);
````

#### Question 9 
````
What is the difference between an id and a class? Why is understanding this difference
important?
````
#### Solution 
````
The difference between an id and a class (both being hooks to describer our html) is that an id is unique, whereas classes are not unique and each element can have many of them. 

ID - 
* Unique to each element
* Only one per page
* Can be used for content navigation with a link / "a" tag where the href attribute is set to the unique Id name
* In css selector is proceeded by a hashtag / octothorpe "#"

Classes -
* Not unique to each element and can be applied to many different things
* Many different elements on a page can have same classes
* Each element can have many or multiple classes
* In css, selector is proceeded by a full stop / period "."

Elements can have both classes and an Id. This is useful for accessibility content labeling, navigation, particular event handlers, and many other cases. Knowing if you need to target multiple elements in your page that share qualities (and therefore have the same class), versus when you need to target a unique / particular element (and therefore we would use the "id"), is important in each of these cases depending on what we need to do. 

````

#### Question 10 
````
A client has reported they are experiencing an issue with their website in which a modal will
not open when the trigger is clicked. Walk through the steps you would take to
troubleshoot the issue.
````
#### Solution
````
First I would check their code and check a live or production version to see the error and inspect how it looks in the browser. 

Then I would debug using console logs to make sure event handlers, listeners, and resulting functions are all working properly. I would take this data and refactor the code, save push the code (likely to a branch environment) and push it / create a pull request if it seems to be fixed. 

Furthermore, using a testing library like Jest would allow us to write a code to ensure the test cases are passing and the modal is generated prior to finalizing the fix. This means if any changes would be done in the future testing will need to be updated and possibly avoid an error like this again. 
````