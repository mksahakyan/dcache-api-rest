# dcache-api-rest
#### Display list of Files for a given folder

>Get list of all files in the current folder.

##### Request
```sh
POST  http://localhost:2880/api/v1/LIST/files/public

Content-Type: application/json
Accept: application/json

{
    "access_token": ["ACCESS_TOKEN"],
    "files": []
}

```
#####Valid forlder paths
*/public, /public/myFolder1, /public/myFolder2/subFolder2, etc.

#####Object Structure

Each File object contains the following attributes

| Attribute   |      Type      |  Description |
|----------|:-------------:|:------|
| size|  long | File's size |
| creationTime |    Date   |   File's creation time |
| mtime |Date |    File's last modification time |
| fileType | String |    Type of the file ( e.g. REG, DIR, LINK, SPECIAL ) |
| fileName | String |    File's name |
| path | String |  File's path corresponding to given pnfsid |

##### Responce Example

> Collection of File objects is returned. (For brevity, only the first object is shown.)
Each File object contains the following structures.

```sh
{
    "List":
    [
        {
            "size": 378,
            "ctime": 0,
            "creationTime": "Tue Jan 19 12:12:43 CET 2016",
            "atime": 0,
            "mtime": "Tue Jan 19 12:12:43 CET 2016",
            "owner": 0,
            "group": 0,
            "mode": 0,
            "fileType": "REGULAR",
            "fileName": "testFile1",
            "path": "/public/testFile1"
        },
      ....
       
    ]
}
        

```
##### Example: Limiting files number in the list

> The number of the files in the list could be limitted by specifaing the **range** structure in the request body.

##### Request

```sh

POST  http://localhost:2880/api/v1/LIST/getFilesbyRange/public

Content-Type: application/json
Accept: application/json

{
    "access_token": ["ACCESS_TOKEN"],
    "range": ["1", "50"]
}

```


#### Display specified files

##### Request

```sh

POST  http://localhost:2880/api/v1/LIST/files/public

Content-Type: application/json
Accept: application/json

{
    "access_token": ["ACCESS_TOKEN"],
    "files": ["testFile1", "testFile2"]
}

```
#### Move folder or file to new directory

> Move a folder or a file objects into a new directory.
The destination path is specified in **destination** structure. 

> Here's an example of how to call the REST API to move a file into the myNewFolder folder.

##### Request

```sh

POST   http://localhost:2880/api/v1/LIST/move/public/testFile7


Content-Type: application/json
Accept: application/json

{
    "access_token": ["ACCESS_TOKEN"],
    "destination": "public/myNewFolder" 
}

```

##### Responce

> "ok" if the operation was succesfull, error message otherwise

#### Create new folder
 
> To create a new folder we pass  the **name** attribute in the request body.


> the following exaple show to call Rest Api to create new folder as child of a folder specified in the request URL.

##### Request

```sh

POST    http://localhost:2880/api/v1/LIST/create/public/myNewFolder


Content-Type: application/json
Accept: application/json

{
    "access_token": ["ACCESS_TOKEN"],
    "name": "myFolder4" 
}

```
##### Responce
> ok if the call was successful

