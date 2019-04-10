---
published: true
---
So, it's been a crazy month and I haven't had the chance to get on here and give you guys an update recently. There were doctors and dogs and Dungeons and Dragons games. It was interesting, and stressful, to say the least. I did manage to keep coding while I was gone, though.

<!-- more -->

Learning something new is always fun. It is also challenging- honestly, that's part of the fun- and sometimes anxiety inducing. When you have anxiety to begin with, anything can be anxiety inducing, but new things, no matter how fun, are especially stressful. It's not that it was hard to start, there are tons of resources out there for learning Javascript. Great resources from straight documentation like [Mozilla Developer Network](https://developer.mozilla.org/en-US/docs/Web/JavaScript) to interactive tutorials like [Free Code Camp](https://www.freecodecamp.org/) and, of course, the never ending list of YouTube tutorials. 

All those sources can be a bit overwhelming. How do you know where to start? Do you start with theory or practice? How much theory is enough theory before starting a project? Do you really have to do a To Do List as your first project?

You don't, but I did anyway. Everyone does a To Do List as their first project. It's a good place to start, uses the HTML and CSS basis and the JavaScript basics you learn from the get go. After a little bit of theory from FreeCodeCamp and Mozilla I decded it was time to put the theory to work and the best way to do that was to build the ubiquitous To Do List. 

With how common this project is, there are what seems to be a never ending list of tutorials for it, a million choices on what to follow. So, of course, I decided to do mine from scratch on my own. Mostly. Well, the Javascript part, anyway. The HTML and CSS I basically took from [W3Schools To Do List Tutorial](https://www.w3schools.com/howto/howto_js_todolist.asp), with a few slight changes. 

I added just enough JavaScript to get it working to the minimum requirements- adding and checking off items. I'll keep building on to the code as I learn more JavaScript. For now, you can take a look at what I have so far [here](https://codepen.io/sjcswank/pen/YMZbLP). It's pretty basic.

The HTML is minimal, just a header, text input, an add button, and a blank list for the to-do items. The most important part was putting in ids on each of the elements so that I could pull them into the JavaScript later. For the CSS, There are only a few basic concepts, the header and inputs, the list items when first added, and the list items when checked off. It looks more complex than it actually is. Again, I mostly took those elements from W3Schools.

The JavaScript, though, that I wrote myself. I figured following a single tutorial straight through would be cheating, since it's JavaScript I'm trying to practice. So I watched and read several and put together a simplist version of a to do list I could manage. 

There's only two parts to this todo list's functionality: adding items to the list, and checking off completed items. So, there's only two functions in the Javascript: addTodoListItem() and boxChecked().

Adding items takes just a few steps, type in the name of the item, click the add button, show the item in the to do list. I added the ids to the input, button and list so that I could later use them in the JavaScript.
	
    <input type="text" id="input" placeholder="Enter todo list item">
    <button id="btnAdd" type="submit" class="btn">Add</button>
    
    <div class="list">
			<ul id="list">
				<!-- <li>This is a list item <input type="checkbox" class="checkbox"></li> -->
			</ul>
		</div>
    
In the JavaScript you can find an element by it's id, which is always unique to each element, and assign it to a variable so you can do actions on it. I needed to do this for the input, the button, and the list, as I needed to use all of those elements for the functionality. To begin with, I needed to pull in the value of the input so that I can add it to the to-do list. I will also need to use the button and the list later on so I assigned them all to variables at the start. One last vairable I will need is an id number for the newly created list items. 
	
    var input = document.getElementById("new");
	var btnAdd = document.getElementById("btnAdd");
	var list = document.getElementById("list");
    
To add an item to the to-do list, once the add button has been clicked, I needed to create an html element with the value of the input included and then tack it on to the current unordered list. I also had to verify that the input is actually there and I'm not creating a blank item. The first step is to figure out when the button has been clicked.

In JavaScript there is a function that picks up when the user interacts with an element on the webpage called an add event listener. An action and a function to call are passed as paramaters to the creating function. for the add button, the action I am looking for is a click, and the function to call is the function I wrote to add an item to the list. Once the event listener was added I could move on to writing the actual function to add the list item.
	
    //add event listener to btnAdd
	btnAdd.addEventListener("click", addTodoListItem);
    
    //add todo item to list
	function addTodoListItem() {
		//check for valid input
		if(input.value === "") {
			alert("You must enter some value!");
		}
		//create li with unique id
		let text = input.value;
		let item = `<li id="li-${id}">${text}<input id="box-${id}" class="checkboxes" type="checkbox"></li>`;
        //add li to ul
		list.insertAdjacentHTML('beforeend', item);
        //increment the id number for the next item
		id++;
        //reset the input field
		input.value = ""; 
	}
    
The second part of the list functionality is being able to check off items on the list. Again, I needed an event listener on the list item so when it is clicked I could call the check function. The check function needed to do only one thing: change the style of the list item so it looks checked off. I'd already created the CSS for the checked list items so it was a simple matter of adding the right class to the list item element.
	
    //add event listener to list
	list.addEventListener("click", boxChecked);
    
    //add strike through style to checked items
	function boxChecked(event) {
		const element = event.target;
        //check if element click was the checkbox and not just the item
		if (element.type === "checkbox"){
        	//add the checked class to the list item (parent of the check box)
			element.parentNode.classList.add("checked");
            //hide the check box
			element.style.display = "none";
		}
	}

Once those two functions were completed I decided to call it quits for the night. I intend to add more functionality to this as I practice more JavaScript. I also intend to make it look a little better as I go. For now, it works. I can add an item, I can see what items I've done. As a person who struggles with anxiety and depression, it's good for me to see a list of things I have accomplished ao I don't need to be able to remove things. Yet. 

I'll come back with more about this to-do list when I update it again. Should be fairly soon. I haven't forgottwn about the Strings and Things challenge, either! More solutions for that are coming soon as well! Until then,

Thanks for reading, and Happy Coding!
