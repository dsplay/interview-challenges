# Instagram Challenge

## Goal

Create a complete web app (back and front-end) to show Instagram last posts of a user from a given valid user token.

## How to get a valid token

You can easily generate a token for your account at https://token.dsplay.tv/instagram

## Reference App

https://pcc-instagram-viewer.netlify.app/

This is more or less what we expect you to do.

## Back-end

The back-end will have to interact with [Instagram Basic Display API](https://developers.facebook.com/docs/instagram-basic-display-api) to retrieve the data from the token.

You can decide if the back-end will have one or more endpoints.

The API response example, considering a single endpoint, could be something like this:
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
         "id":"1231256464654",
         "caption":"Instagram post with carousel",
         "media_type":"CAROUSEL_ALBUM",
         "media_url":"https://scontent-iad3-1.cdninstagram.com/v/xyz",
         "permalink":"https://www.instagram.com/p/abc",
         "timestamp":"2021-04-03T19:52:59+0000"
      },
      {
         "username":"lukeskywalker",
         "id":"1231256464654",
         "caption":"Video post",
         "media_type":"VIDEO",
         "media_url":"https://scontent-iad3-1.cdninstagram.com/v/xyz",
         "permalink":"https://www.instagram.com/p/abc",
         "thumbnail_url":"https://scontent-iad3-1.cdninstagram.com/v/xyz",
         "timestamp":"2021-04-02T10:38:01+0000"
      },
      {
         "username":"lukeskywalker",
         "id":"1231256464654",
         "caption":"image post 💘",
         "media_type":"IMAGE",
         "media_url":"https://scontent-iad3-1.cdninstagram.com/v/xyz",
         "permalink":"https://www.instagram.com/p/abc",
         "timestamp":"2021-03-27T22:44:13+0000"
      }
   ]
}
```

- To get the user profile info you must use the `/me` endpoint: https://developers.facebook.com/docs/instagram-basic-display-api/reference/me
```js
// axios request example
const response = await axios.get(INSTAGRAM_USER_PROFILE_URL, {
  params: {
    fields: 'id,username,account_type,media_count',
    access_token: userToken,
  },
});
```
- To get the recent user media (posts) you must use the `/me/media` endpoint: https://developers.facebook.com/docs/instagram-basic-display-api/reference/user/media 
```js
// axios request example
const response = await axios.get(INSTAGRAM_USER_MEDIA_URL, {
  params: {
    fields: 'username,id,caption,media_type,media_url,permalink,thumbnail_url,timestamp',
    access_token: userToken,
  },
});
```


