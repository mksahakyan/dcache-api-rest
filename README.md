# dcache-api-rest
#### Display list of Files for a given folder

>Get list of all files in the current folder.

##### Request
```sh
POST  http://localhost:2880/api/v1/LIST/getFilesbyRange/public

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
        .
        .
        .
       
    ]
}
        


```
