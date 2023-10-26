# Reading Files By Path

Use below to get the file list under specify path, then use pattern to do file name mapping.

```
function getFileNameUnderThePathById(path, id) {
    var directory = path;
    var xmlHttp = new XMLHttpRequest();
    xmlHttp.open('GET', directory, false); // false for synchronous request
    xmlHttp.send(null);
    var ret = xmlHttp.responseText;
    var fileList = ret.split('\n');
    for (i = 0; i < fileList.length; i++) {
        var fileinfo = fileList[i].split(' ');
        if (fileinfo.indexOf(id + "_") != 0) {
            return fileinfo[i];
        }
    }
}
```

After got the file name, use fetch api to get the file content with the file name and the path.

```
function getMarkdownContentByPath(path) {
    fetch(path)
        .then(response => response.text())
        .then(data => {
            document.getElementById("markdownField").innerHTML = marked.parse(data);
        })
        .catch(error => {
            console.error('An error occurred:', error);
        });
}
```
