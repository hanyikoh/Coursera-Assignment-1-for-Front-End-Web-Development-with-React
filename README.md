This project was bootstrapped with [Create React App](https://github.com/facebook/create-react-app).

## Available Scripts

In the project directory, you can run:

### `npm start`

Runs the app in the development mode.<br />
Open [http://localhost:3000](http://localhost:3000) to view it in the browser.

The page will reload if you make edits.<br />
You will also see any lint errors in the console.

### `npm test`

Launches the test runner in the interactive watch mode.<br />
See the section about [running tests](https://facebook.github.io/create-react-app/docs/running-tests) for more information.

### `npm run build`

Builds the app for production to the `build` folder.<br />
It correctly bundles React in production mode and optimizes the build for the best performance.

The build is minified and the filenames include the hashes.<br />
Your app is ready to be deployed!

See the section about [deployment](https://facebook.github.io/create-react-app/docs/deployment) for more information.

### `npm run eject`

**Note: this is a one-way operation. Once you `eject`, you can’t go back!**

If you aren’t satisfied with the build tool and configuration choices, you can `eject` at any time. This command will remove the single build dependency from your project.

Instead, it will copy all the configuration files and the transitive dependencies (webpack, Babel, ESLint, etc) right into your project so you have full control over them. All of the commands except `eject` will still work, but they will point to the copied scripts so you can tweak them. At this point you’re on your own.

You don’t have to ever use `eject`. The curated feature set is suitable for small and middle deployments, and you shouldn’t feel obligated to use this feature. However we understand that this tool wouldn’t be useful if you couldn’t customize it when you are ready for it.

## Learn More

You can learn more in the [Create React App documentation](https://facebook.github.io/create-react-app/docs/getting-started).

To learn React, check out the [React documentation](https://reactjs.org/).

### Code Splitting

This section has moved here: https://facebook.github.io/create-react-app/docs/code-splitting

### Analyzing the Bundle Size

This section has moved here: https://facebook.github.io/create-react-app/docs/analyzing-the-bundle-size

### Making a Progressive Web App

This section has moved here: https://facebook.github.io/create-react-app/docs/making-a-progressive-web-app

### Advanced Configuration

This section has moved here: https://facebook.github.io/create-react-app/docs/advanced-configuration

### Deployment

This section has moved here: https://facebook.github.io/create-react-app/docs/deployment

### `npm run build` fails to minify

This section has moved here: https://facebook.github.io/create-react-app/docs/troubleshooting#npm-run-build-fails-to-minify

### Installing json-server

- json-server is a node module, and hence can be installed globally by typing the following at the command prompt:

```
npm install json-server -g
```

### Configuring the Server

- At any convenient location on your computer, create a new folder named **json-server**, and move to this folder.

- Download the db.json file provided above to this folder.

- Move to this folder in your terminal window, and type the following at the command prompt to start the server:

  ```
  json-server --watch db.json -p 3001 -d 2000
  ```

- This should start up a server at port number 3001 on your machine. The data from this server can be accessed by typing the following addresses into your **browser address bar**:

```
http://localhost:3001/dishes
http://localhost:3001/promotions
http://localhost:3001/leaders
http://localhost:3001/feedback
```

- Type these addresses into the browser address and see the JSON data being served up by the server. This data is obtained from the db.json file

- The json-server also provides a static web server. Any resources that you put in a folder named **public** in the **json-server** folder above, will be served by the server at the following address:

```
http://localhost:3001/
```

- Shut down the server by typing **ctrl-C** in the terminal window.

### Serving up the Images

- Create a public folder in your json-server folder.
- Download the images.zip file that we provide above, unzip it and move the images folder containing the images to the public folder.
- Restart the json-server as we did before. Now your server will serve up the images for our React app. You can view these images by typing the following into your browser address bar:

```
http://localhost:3001/images/<image name>.png
```

### Conclusions

In this exercise, you learnt how to configure and start a simple server using the **json-server** node module. You also learnt how the server can serve up static web content.



## Example of How to Post A New Source

```javascript
export const postComment = (dishId, rating, author, comment) => (dispatch) => {

    const newComment = {
        dishId: dishId,
        rating: rating,
        author: author,
        comment: comment
    };
    newComment.date = new Date().toISOString();
    
    return fetch(baseUrl + 'comments', {
        method: "POST",
        body: JSON.stringify(newComment),
        headers: {
          "Content-Type": "application/json"
        },
        credentials: "same-origin"
    })
    .then(response => {
        if (response.ok) {
          return response;
        } else {
          var error = new Error('Error ' + response.status + ': ' + response.statusText);
          error.response = response;
          throw error;
        }
      },
      error => {
            throw error;
      })
    .then(response => response.json())
    .then(response => dispatch(addComment(response)))
    .catch(error =>  { console.log('post comments', error.message); alert('Your comment could not be posted\nError: '+error.message); });
};

```

------

## 										React Animation

## React-Transition-Group

React-transition-group provides a set of components  that enable you to manage components tips including mounting and unmounting. 



he transition group is the component that the React-transition-group supports. 

The transition group manages a set of transitions that you apply to a list. So, if you are applying to a list, then you know that the list items may come in and go and so on. So, for example, if you have a long list and then you add a new item to the list and you wanted to animate the entering of the new item into that list, then the management of that, by using the transition class, that if you enclose the entire list in a transition group and then apply the transition to each list item, then the in property of the transition and the turning  of the in prop to true and false will be controlled by the transition group.  So, it automatically toggles the in prop for the components that are enclosed inside it.  So, if you apply to a list each list item, the in prop will be toggled as required. 

when you have a list of items, you can stagger things into place like this.

```javascript
const cmnts = comments.map((commnts) => {
            return (
                <ul key={commnts.id} className="list-unstyled">
                    <Stagger in>
                        {comments.map((comment) => {
                            return (
                                <Fade in>
                                    <li key={comment.id}>
                                        <p>{comment.comment}</p>
                                        <p>-- {comment.author} , {new 		    Intl.DateTimeFormat('en-US', { year: 'numeric', month: 'short', day: '2-digit' }).format(new Date(Date.parse(comment.date)))}</p>
                                    </li>
                                </Fade>
                            );
                        })}
                    </Stagger>
                </ul>
            );
        }
```


