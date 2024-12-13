# Channels
## Featured Channels
`GET /channels/featured`

Do not put your API domain into iconUrl/retinaIconUrl. The app will do that.

Response data:

`{"code": "", "data": { "count": 9, "anchorStr": "1408203984", "records": [{"channelId": 1, "channel": "Comedy", "iconUrl": "icon.png", "retinaIconUrl": "retina-icon.png"}, {"channelId": 2, "channel": "Technology", "iconUrl": "icon.png", "retinaIconUrl": "retina-icon.png"}]}, "previousPage": null, "backAnchor": "", "anchor": "1408203984", "nextPage": null, "size": 9, "success": true, "error": ""}`
# Likes
## View Likes
`GET /posts/(id)/likes`

Response data:

`{
    "code": "",
    "data": {
        "count": 2,
        "anchorStr": "0",
        "records": [{
                "username": "johndoe",
                "verified": true,
                "vanityUrls": [],
                "avatarUrl": "https://example.com/avatar.jpg",
                "userId": 123,
                "following": 1,
                "profileBackground": "0x33ccbf",
                "user": {
                    "private": 0
                },
                "location": "New York, USA"
            },
            {
                "username": "janedoe",
                "verified": false,
                "vanityUrls": [],
                "avatarUrl": "https://example.com/avatar2.jpg",
                "userId": 456,
                "following": 0,
                "profileBackground": "0x33ccbf",
                "user": {
                    "private": 0
                },
                "location": "Los Angeles, USA"
            }]
    },
    "previousPage": null,
    "backAnchor": "",
    "anchor": "0",
    "nextPage": 2,
    "size": 2,
    "success": true,
    "error": ""
}`
## Like Post
`POST /posts/(id)/likes`

Response data:

`{
    "code": "",
    "data": [],
    "success": true
}`
# Posts
## Create Post
`POST /posts`

Request data:

* `videoUrl` - The video URL. Provided by the video upload endpoint.
* `thumbnailUrl` - The video thumbnail URL. Provided by the thumbnail upload endpoint.
* `description` - The video description. Provided by the app.
* `entities` - Entities, most of the time only mentions. For tags, you'll need to get them from the video description. `[{'type': 'mention', 'id': <userId>, 'text': <username>, 'range': [start, end]}]`
* `[forsquareVenueId]` - The foursquare venue ID. Only provided by the app if the user wants to attach a location. This should be used for getting info from the foursquare API and providing the necessary information in timelines.
* `[venueName]` - The foursquare venue name. Only provided by the app if the user wants to attach a location.
* `[channelId]` - The channel ID. Only provided by the app if the user wants to post to a channel.

Response data:

`{
    "code": "",
    "data": [],
    "success": true
}`
# Uploads
## Upload Video
`PUT /videos/upload/(app version).mp4`

Request data: MP4 video data

Response data: X-Upload-Key header, which should be the final video URL.
## Upload Thumbnail
`PUT /videos/thumbs/(app version).mp4.jpg`

Request data: JPEG image data

Response data: X-Upload-Key header, which should be the final thumbnail URL.
## Upload Avatar
`PUT /videos/avatar/(app version).jpg`

Request data: JPEG image data

Response data: Just send 200 OK if successful.
# Users
## Get followers
`GET /users/(user id)/followers`

Response data:

`{
"code": "",
"data": {
    "count": 1,
    "anchorStr": "0",
    "records": [{
            "username": "username",
            "verified": 0,
            "vanityUrls": [],
            "avatarUrl": "http://v.cdn.vine.co/v/avatars/xxx",
            "userId": 1234567890,
            "following": 0,
            "profileBackground": "0x33ccbf",
            "user": {
                "private": 0
            },
            "location": "www.username.com"
        }],
    "previousPage": null,
    "anchor": 0,
    "nextPage": null,
    "size": 20
},
"success": true,
"error": ""
}`
## Get following
`GET /users/(user id)/following`

Response data:

`{
"code": "",
"data": {
    "count": 1,
    "anchorStr": "0",
    "records": [{
            "username": "username",
            "verified": 0,
            "vanityUrls": [],
            "avatarUrl": "http://v.cdn.vine.co/v/avatars/xxx",
            "userId": 1234567890,
            "following": 0,
            "profileBackground": "0x33ccbf",
            "user": {
                "private": 0
            },
            "location": "www.username.com"
        }],
    "previousPage": null,
    "anchor": 0,
    "nextPage": null,
    "size": 20
},
"success": true,
"error": ""
}`
