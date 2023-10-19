# Disabled Context Menu

Listening on context menu open
Keyword to search : holding, right click, mobile

```
window.oncontextmenu = function(event) {
     event.preventDefault();
     event.stopPropagation();
     return false;
};
```
