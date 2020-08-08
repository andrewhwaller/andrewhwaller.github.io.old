---
layout: post
title: Conditional Rendering in React
---
In the course of building my first React app (https://wikiannotator.com) I had to learn different ways to handle conditional rendering, i.e., changing what my components would render based on some sort of state change or other factor. There are three different implementations of conditional rendering that I ended up using in my app.

1. Using a function to render content conditionally
A good example of this is a spinner that I use in WikiAnnotator. I needed message attached to the spinner to change based on what the app was doing at the time. However, I didn't want to write new actions for each case; I really just needed the text to change in response to my app's state. To accomplish this, I used the following function:
	renderSpinnerMessage() {
		let spinnerMessage;

		if (this.props.articleLoading) {
			spinnerMessage = "Article loading...";
		} else if (this.props.articleSaving) {
			spinnerMessage = "Article saving...";
		}

		return spinnerMessage;
	}
This function has a different return value depending on what is going on in the app's state. I can then call this function inside the return statement in my render function and the appropriate text will be rendered!

2. Variables inside the render function
Similarly, I can also assign variables inside my render function and reference those variables inside the return statement. Functionally, this is very similar to what I just described, since all of the conditions are evaluated when the render function is called. However, one style or the other may suit you depending on the complexity of the logic and what parts of your component need to be conditionally rendered. I prefer using variables and regular if/else statements if I need to render a larger set of components based on on aspect of the app's state.

3: Inline conditionals
You can also write ternaries and other statements directly in your JSX code. This takes a bit of getting used to; one of the common ways to do this that I discovered is the && operator. If you begin your statement with an expression and follow it with && and then the component that you're trying to conditionally render, the evaluation of the first expression should determine whether or not your component/JSX renders. You can also use ternary operators in a similar way. 

For even more ways to handle conditional rendering, check out this article over at scotch.io: https://scotch.io/tutorials/7-ways-to-implement-conditional-rendering-in-react-applications
