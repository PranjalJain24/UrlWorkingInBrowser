# how html and css rendering works

**Rendering Engine** – this takes HTML code and interprets it into what you see visually.
The rendering engine has a very important job as it displays what you see on your screen. It communicates with the networking layer of the browser to grab HTML code and other items passed from a remote server. 

## Then the browser takes the following steps:
* Process HTML markup and build the DOM tree.
* Process CSS markup and build the CSSOM tree.
* Combine the DOM and CSSOM into a render tree.
* Run layout on the render tree to compute geometry of each node.
* Paint the individual nodes to the screen.


### 1. Parsing HTML and creating the DOM Tree
HTML is a hierarchal structure whose elements are parsed and turned into a “DOM tree” by the rendering engine. The browser creates the Document Object Model. It is a tree of objects. Each HTML tag is a branch starting at the root element.

#### DOM Tree
For constructing DOM Tree it converts raw bytes of data into characters which are further transformed to Tokens.

Now what a Token is? An html file is broken down into small units of parsing called tokens. This is how the browser begins to understand what you’ve written.

The tokens are then converted into nodes.

The nodes are then linked in a tree data structure known as the DOM.

### 2. Parsing CSS and creating the CSSOM Tree
#### CSSOM Tree:
After the browser creates the DOM tree, it starts creating the CSSOM which Stands for CSS Object Model. It is basically a “map” of the CSS style which you can find on a web page. It is like the DOM but for CSS rules.

CSSOM Tree is constructed the same way as DOM Tree was created.

### 3. Render Tree Construction
#### Render Tree:
It is a tree which contains just the visible elements on the screen such as height/width and color ordered in the hierarchy in which they are to be displayed in the browser. The CSSOM and the DOM trees are combined into a render tree.

##### To construct the render tree, the browser roughly does the following:

1. Starting at the root of the DOM tree, traverse each visible node.

* Some nodes are not visible (for example, script tags, meta tags, and so on), and are omitted since they are not reflected in the rendered output.
* Some nodes are hidden via CSS and are also omitted from the render tree; for example, the span node---in the example above---is missing from the render tree because we have an explicit rule that sets the "display: none" property on it.
2. For each visible node, find the appropriate matching CSSOM rules and apply them.

3. Emit visible nodes with content and their computed styles.

The final output is a render that contains both the content and style information of all the visible content on the screen. With the render tree in place, we can proceed to the "layout" stage.


### 4. Layout Process
Once the render tree is constructed, the rendering engine recursively goes through the HTML elements in the tree and figure out where they should be placed on the screen. This starts at the top left in position 0,0 and elements and attributes are mapped to coordinates on the screen.
Once the browser finds out which rules apply to which elements, it will start calculating how much space it takes up and where is it on the screen.

It is challenging process because each element can affect others.

The "Layout" event captures the render tree construction, position, and size calculation in the Timeline.
When layout is complete, the browser issues "Paint Setup" and "Paint" events, which convert the render tree to pixels on the screen.

### 5. Painting 
Each node (branch) of the render tree is drawn out on the screen by communicating with the Operating System Interface which contains designs and styles for how UI elements should look.

The browser starts to fill pixel by pixel in the screen and repaints the screen if any dynamic changes occur.
