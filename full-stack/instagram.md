# Instagram Challenge

## Goal

Create a complete web app (back and front-end) to show Instagram last posts of a user from a given valid user token.

### How to get a valid token

You can easily generate a token for your account at https://token.dsplay.tv/instagram

### Reference App

https://pcc-instagram-viewer.netlify.app/

This is more or less what we expect you to build.

## Before you begin

Keep in mind that:
- You can start by building the back-end or the front-end (it's up to you);
- You have a basic and some extra goals for the back and front-end; Start by the basic one and then go to the extras;
- You don't have to finish everything. If you get stuck at some point, try to move to the next goal;


## Back-end

### Goals

- **Basic:** Write a function/module to call the Instagram APIs correctly and print the responses on the console;
- **Extra 1:** Expose your function/module as an HTTP server (e.g. Express.js app);
- **Extra 2:** Make your code available on GitHub;
- **Extra 3:** Make your application available on the web using any host (e.g. Heroku);


### Rules

- You can use Javascript (preferably), PHP, Python or Java;
- You can decide if the back-end will have one or more endpoints;
- You must create a README file having the instructions to run the code;

> The tips and examples will be in Javascript, but feel free to use your preferred language if it makes you more comfortable.


### Instructions

The back-end will have to interact with [Instagram Basic Display API](https://developers.facebook.com/docs/instagram-basic-display-api) to retrieve the data from the token.

- To get the user profile info you must use the `/me` endpoint: https://developers.facebook.com/docs/instagram-basic-display-api/reference/me

- To get the recent user media (posts) you must use the `/me/media` endpoint: https://developers.facebook.com/docs/instagram-basic-display-api/reference/user/media 


#### Tips and Code Snippets

- Example request to get user profile using `axios`
```js
const response = await axios.get(INSTAGRAM_USER_PROFILE_URL, {
  params: {
    fields: 'id,username,account_type,media_count',
    access_token: userToken,
  },
});
```

- Example request to get user media using `axios`
```js
const response = await axios.get(INSTAGRAM_USER_MEDIA_URL, {
  params: {
    fields: 'username,id,caption,media_type,media_url,permalink,thumbnail_url,timestamp',
    access_token: userToken,
  },
});
```

- Express.js hello world example with CORS enabled
```js
const express = require('express');
const cors = require('cors');

const app = express();
const port = process.env.PORT || 5000;

app.use(cors());

app.get('/', (req, res) => {
  res.send('Hello World!')
})

app.listen(port, () => {
  console.log(`Server listening at port ${port}`)
})
```

- Response example (considering a single endpoint):
```json
{
   "profile":{
      "id":"1231256464654",
      "username":"lukeskywalker",
      "account_type":"PERSONAL",
      "media_count":999
   },
   "media":[
      {
         "username":"lukeskywalker",
         "id":"22222222222222",
         "caption":"Instagram post with carousel",
         "media_type":"CAROUSEL_ALBUM",
         "media_url":"https://scontent-iad3-1.cdninstagram.com/v/xyz",
         "permalink":"https://www.instagram.com/p/abc",
         "timestamp":"2021-04-03T19:52:59+0000"
      },
      {
         "username":"lukeskywalker",
         "id":"333333333333333",
         "caption":"Video post",
         "media_type":"VIDEO",
         "media_url":"https://scontent-iad3-1.cdninstagram.com/v/xyz",
         "permalink":"https://www.instagram.com/p/abc",
         "thumbnail_url":"https://scontent-iad3-1.cdninstagram.com/v/xyz",
         "timestamp":"2021-04-02T10:38:01+0000"
      },
      {
         "username":"lukeskywalker",
         "id":"44444444444444",
         "caption":"image post 💘",
         "media_type":"IMAGE",
         "media_url":"https://scontent-iad3-1.cdninstagram.com/v/xyz",
         "permalink":"https://www.instagram.com/p/abc",
         "timestamp":"2021-03-27T22:44:13+0000"
      }
   ]
}
```

- Reference app backend endpoint
```
https://pcc-instagram-api-nodejs.herokuapp.com/api/user?token=<token>
```

## Front-end

### Goals

- **Basic:** Create a simple front-end (HTML/CSS/JS) application that consumes the API provided by the back-end and prints the result on the browser console;
- **Extra 1:** Create a basic user interface to receive the token and show the profile info and last posts from the user;
- **Extra 2:** Style the UI with CSS or your preferred styling solution (Sass, Less, JSS, Styled Components, etc));
- **Extra 3:** Make your code available on GitHub;
- **Extra 4:** Make your application available on the web using any host (e.g. Netlify);


### Rules

- You can use React (preferably), jQuery, vanilla Javascript, Vue, or even Ang... no, not Angular!;
- You must create a README file having the instructions to run the code;


#### Tips and Code Snippets

- If you prefer to start building the front-end or in the case you haven't been able to finish the back-end, you can use the Reference App [back-end endpoint](https://pcc-instagram-api-nodejs.herokuapp.com/api/user?token=<token>) or the provided "Example response" JSON as your input;
- If you, wisely, decide to use React :), you can bootstrap your project with [Create React App](https://reactjs.org/docs/create-a-new-react-app.html);
```sh
npx create-react-app instagram-viewer
cd instagram-viewer
npm start
```
- You can "steal" some CSS from the Reference App, instead of building it from scratch;

## Good Luck!
