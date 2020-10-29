---
name: The basics of linear gradients
description: Learn how to implmenet linear gradients into your builds
keywords: gradients, customization, color
dateUpdated: 10/29/2020
product: Answers
categories: Frontend, Card Customizations
thumbnail: https://aws1.discourse-cdn.com/turtlehead/original/2X/d/d2c20d31958cf623580ca2fca9578a53e4bceb1c.png
---
# Overview
You can use linear gradients to format various aspects of your answers experience –CTAs, Answers Background, Results Title Bar, and Results Card to name a few—within the answers.scss file by editing the background-image. There are several types of gradients that can be used based on direction. Here are some examples of both gradient types and objects you can apply them to:

## Controlling Gradient Transitions

Linear-gradients transition evenly from one color to the next by default. However, you can use percentages after each color within a linear-gradient to identify start and stop values. The starting colors default start value when left blank is 0%. Similarly, the final colors stop value defaults to 100%.

## Adjusting the Transition:

You can toggle with how much space a color takes up within a particular object. If you want want one color to take up a majority you can do something like this:

### The Code:

```css
.HitchhikerAllFieldsStandard-title {
background-image: linear-gradient(to right, red 33%, pink 70%, purple);
}
```

### The Result:

![image|712×56](https://aws1.discourse-cdn.com/turtlehead/original/2X/d/d2c20d31958cf623580ca2fca9578a53e4bceb1c.png)

## Creating Hard Lines:

To do this you must apply percentage values based on where two colors reach a midpoint

### The Code:

```css
.HitchhikerAllFieldsStandard-title {
 background-image: linear-gradient(to right, red 33%, pink 33% 66%, purple 66%);
}
```

### The Result:

![image|723×61](https://aws1.discourse-cdn.com/turtlehead/original/2X/8/8dac2628804ee45690e61a4486fa3912c2aae4f7.png)

*You can use similar logic to adjust where you want the midpoint of a transition between colors to be (e.g., you want the object to be 70% of one color and 30% of a second color, but with an even transition)*

## Top to Bottom

### The Code:

```css
.yxt-Results-titleBar {
background-image: linear-gradient(red, orange, yellow);
}
```

### The Result:

![image|728×148](https://aws1.discourse-cdn.com/turtlehead/optimized/2X/1/110cc5662519b03df9106426506086f337e7904d_2_485x99.png)

## Left to Right

### The Code:

```css
.HitchhikerCTA {
background-image: linear-gradient(to right, red , orange, pink);
color: white;
}
```
### The Result

![image](https://aws1.discourse-cdn.com/turtlehead/original/2X/2/2eb08c1697a1c92e621704b4e473cd0b275401dc.png)

## Diagonal

### The Code

```css
.HitchhikerJobStandard {
background-image: linear-gradient(to bottom right, red, yellow);
color: white;
}
```
### The Result

![image|755×320](https://aws1.discourse-cdn.com/turtlehead/original/2X/2/217de31d34efa1c918c2c704d1ec8d41f9205a49.png)

*For FAQ Accordion cards you will need to reference the toggle object that contains the question AND the expanded content section*

## Using Angles to Define Direction

This is similar to the previous examples, but will give you more control of the direction. For example, value of 0deg is equivalent to “to top” while 90deg is equivalent “to right”.

### The Code

```css
body {
 background-image:linear-gradient(240deg, red, yellow, green);
}
```
### The Result:

![image|1596×614](https://aws1.discourse-cdn.com/turtlehead/optimized/2X/0/0b59836c0eee20a7d69e43dad6ea5dfe0ea571e3_2_936x360.png)

*[Read this post](https://hitchhikers.yext.com/community/t/adding-an-image-as-answers-background/1756) 2 for more info on how to edit the full answers background.*

## Repeating Gradients

### The Code:

```css
.HitchhikerAllFieldsStandard-title {
background-image: repeating-linear-gradient(red, pink 10%, purple 20%);
}
```
### The Result:

![image|712×174](https://aws1.discourse-cdn.com/turtlehead/original/2X/d/d80b73f14e3fb9de588afaf3393b084e74cdde0e.png)

*You can also define the direction using terms like “to left” or degree values with the same syntax structure as previous examples.*

**Note: For most of these examples, there are 2-3 colors used but you can use as many as you want.**