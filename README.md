How to Build Simple Tic Tac Toe Game with React

Phase 1: Setup
Phase 2: React
  The Box component
  The Board component
  The Scoreboard component
  The App component
Phase 3: Utils
Phase 4: Storage
Phase 5: Styling




Phase 1: Setup
In the first phase, let’s create all files we need for our Tic Tac Toe game. To make this step easier we will use the create-react-app as our starting template. If you have it this package already installed on your computer, go ahead and use that with you favorite dependency manager. If not, I recommend using it via npx.

There is no reason to install the create-react-app package, even if you plan to use it more often. Npx will allow you to use it, or any other package hosted on npm, without installing it, as global or local dependency. Using npx is almost like using npm. The only difference is that you replace the npm with npx. The rest is the same.

One important thing you have to remember. Npx will need to temporarily download the package so you can use it. This means that you must be connected to internet. About the package. Don’t worry about cluttering your disk. Npx will automatically remove the package after you use it. The command to create the template for our Tic Tac Toe game is npx create-react-app react-tic-tac-toe.

After npx do its job, we will need to add one additional package. This will be react-router-dom. Our Tic Tac Toe game will have two views, or pages. The first will be a welcome screen showing list of scores from previous games. The second will be the Tic Tac Toe game board itself, with list of played moves.

We will use the react-router-dom to switch between these two views. And that will be all we need. If you want to use Sass or styled-components, or some other library for styling, go ahead and add it. In this tutorial, we will stick to good old CSS and stylesheets.




Phase 2: React
In the second phase, our task will be to build all React components we will need for our Tic Tac Toe game. We will create four components, board-box.jsx, board.jsx, scoreboard.jsx and the index.jsx.

The Box component
Let’s start with the simplest component. This will be the board-box.jsx, component for individual boxes or squares on the board. We will create this component as a stateless. It will be a simple button with click handler and label, both passed by props.


The Board component
Next component will be the main board for our Tic Tac Toe game. This component will be a little bit more complex and also much bigger than the previous one. First, we will create this component as a stateful component. Component state will be initialized with three key/value pairs-boxes, history , xIsNext.

The boxes item will be an array containing nine items, one item for each board box. All these items will be null. So, when box is empty, not “x” or “o”, it will be null. Otherwise, it will be either “x” or “o”. The history will be an empty array. When player makes a move, we will push players name to history array.

The last one, the xIsNext, will be boolean. We will initialize it as true. This will help us determine which player should make a move as next. After this, we will create new instance of Storage object (we will create this object later). We will use it later to store game results in localStorage.

The board component will contain two click handlers. First will be handleBoxClick and it will handle clicking on board boxes. With every click, it will check if board contains winning combination or if all boxes are clicked. If one of these conditions is true, the game ends. Otherwise, we will check which player made move, mark the box and push the move to game history.

The second one will be handleBoardRestart. This one will restart the component state to its initial state. The render method will contain conditions to show status message-who is winner, game is drawn or who is the next one to move. Next, it will contain link to scoreboard, the main board with boxes list with history of moves and button to start new game.

For the link to scoreboard, we will use Link from react-router-dom library that will redirect the user on / (root) view, or page.


The Scoreboard component
The Scoreboard component will be very simple. Similarly to Board, this will also be stateful component. Its state will contain one key/value pair, scoreboard. The value for this key will be an empty array. After Scoreboard component mounts we will use Storage object to load any data from local storage and update component state.

The render method will contain the list with previous games and link to start new game. For the link, we will again use Link from react-router-dom library that will redirect the user on /board view, or page.




The App component // src/index.jsx
The last component we need to create is the main App. Here, we will import Board and Scoreboard components/views we just created. We can also import CSS (or Sass) stylesheets to make our Tic Tac Toe game look better. However, the most important part of this component will be implementing BrowserRouter and Routes from react-router-dom.

We will use the router to create two routes, one for root (homepage) and one for the Tic Tac Toe game board. Root route will render the Scoreboard component. The board route will render Board component. As the last step we will render the App component into DOM.




Phase 3: Utils
Our Tic Tac Toe game is almost finished. However, before we can let anyone try our React Tic Tac Toe we need to create two utility functions. These functions will be findWinner and areAllBoxesClicked. The findWinner will contain an array with winning combinations and for loop.

The for loop will iterate over the array with winning combinations and check if the game board contains winning combination. If so, it will return the winner, either ‘x’ or ‘o’. Otherwise, it will do nothing. The areAllBoxesClicked will use forEach loop to iterate over all boxes count those that are not empty (not null).

If the number of these not empty (not null) boxes is equal to 9, it will return true-all boxes are click (filled). Otherwise, it will return false.




Phase 4: Storage
The last thing our Tic Tac Toe game needs is the Storage object. We will use this object to create and update data in browser localStorage object. When initialized, it will check if localStorage contains any data from previous games. If not, it will create new item create new item in localStorage for our Tic Tac Toe game.

Next, we will add two methods, getData and update. The first one will get existing data localStorage. The second one will push new data into localStorage. With this, we will now be able to show records of previous games on the scoreboard view, or page.




Phase 5: Styling
Our Tic Tac Toe game is working and ready for first players. The last thing we can do is make look better.