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

- To get the user profile info you must use the `/me` endpoint: https://developers.facebook.com/docs/instagram-basic-display-api/reference/me
- To get the recent user media (posts) you must use the `/me/media` endpoint: https://developers.facebook.com/docs/instagram-basic-display-api/reference/user/media 



