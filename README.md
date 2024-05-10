# Fetching json to js
## _Just with github, no server work_

This is a guide to making a simple fetching module with html, js and fetch from a json website with no server work.  Just a hosted website and reachable json file.


## Steps
- The website to display output
- The json file to have things to be put on the website
- The js to fetch the json data

## Method I use
- Github to host the website and the json data

## What you will need
 - Website hosting (e.g. [Github](https://github.com/))
 - Internet access
 - This guide...

## Installation

Setup your website by making a html (* the main web file that will be reached if you goto the web adress with no file*)
**e.g. user.github.io/project will be the same as if you went to user.github.io/project/index.html automatically**

In github make sure you set the project to the main root and make sure all of your files including your __index.html__ file.

Your html to show the table that you will fetch data from another file and will fill the table with.

```html
<table id="tasklist">
    <tr>
      <th>Class</th>
      <th>Task</th>
      <th>Due date</th>
    </tr>
  </table>
```

Now some css.

If you want to put the css in the html file you can copy it in 
```html
<style>
here
</style>
```

```css
#tasklist {
  font-family: Arial, Helvetica, sans-serif;
  border-collapse: collapse;
  width: 100%;
}

#tasklist td, #tasklist th {
  border: 1px solid #ddd;
  padding: 8px;
}

#tasklist tr:nth-child(even){background-color: #f2f2f2;}

#tasklist tr:hover {background-color: #ddd;}

#tasklist th {
  padding-top: 12px;
  padding-bottom: 12px;
  text-align: left;
  background-color: #04AA6D;
  color: white;
}
```

And now for the bit you've been waiting for. The js (javascript).

If you want to put the js in the html file you can copy it in 
```html
<script>
here
</script>
```

```js
fetch('https://user.github.io/fetch.json')
  .then(response => response.json())
  .then(data => {
    // Once the JSON data is retrieved, you can populate the table with it
    populateTableWithJSONData(data);
  })
  .catch(error => {
    console.error('Error fetching JSON data:', error);
  });

  
    function populateTableWithJSONData(data) {
  const table = document.getElementById('tasklist');

  data.forEach(task => {
    const row = table.insertRow(-1);
    const classCell = row.insertCell(0);
    const taskCell = row.insertCell(1);
    const dueDateCell = row.insertCell(2);

    classCell.textContent = task.Class;
    taskCell.textContent = task.Task;
    dueDateCell.textContent = task.DueDate;
  });
}
```

Replace the https://user.github.io/fetch.json with your fetching json.  It should look like this.

```json
[
  {
    "Class": "Math",
    "Task": "Area, Perimeter...",
    "DueDate": "10/05/2024",
  },
  {
    "Class": "English",
    "Task": "bookname book study",
    "DueDate": "n/a",
  },
  {
    "Class": "Random task",
    "Task": "blah, blah",
    "DueDate": "today",
  }
]

```

Your full html file can look like this:

```html
<table id="tasklist">
    <tr>
      <th>Class</th>
      <th>Task</th>
      <th>Due date</th>
    </tr>
  </table>
<style>
#tasklist {
  font-family: Arial, Helvetica, sans-serif;
  border-collapse: collapse;
  width: 100%;
}

#tasklist td, #tasklist th {
  border: 1px solid #ddd;
  padding: 8px;
}

#tasklist tr:nth-child(even){background-color: #f2f2f2;}

#tasklist tr:hover {background-color: #ddd;}

#tasklist th {
  padding-top: 12px;
  padding-bottom: 12px;
  text-align: left;
  background-color: #04AA6D;
  color: white;
}

</style>

<script>
fetch('https://user.github.io/fetch.json')
  .then(response => response.json())
  .then(data => {
    // Once the JSON data is retrieved, you can populate the table with it
    populateTableWithJSONData(data);
  })
  .catch(error => {
    console.error('Error fetching JSON data:', error);
  });

  
    function populateTableWithJSONData(data) {
  const table = document.getElementById('tasklist');

  data.forEach(task => {
    const row = table.insertRow(-1);
    const classCell = row.insertCell(0);
    const taskCell = row.insertCell(1);
    const dueDateCell = row.insertCell(2);

    classCell.textContent = task.Class;
    taskCell.textContent = task.Task;
    dueDateCell.textContent = task.DueDate;
  });
}
</script>

```

## Issues and troubleshooting
You might get this error in the console:
```
Cross-Origin Request Blocked: The Same Origin Policy disallows reading the remote resource at https://user.github.io/fetch.json. (Reason: CORS header ‘Access-Control-Allow-Origin’ missing). Status code: 404.
```
Just make sure you have the files in the same github page.
If you have any more issues you can email me here: <email>

## Sources

Here are the tools used in this project

| Source | Website |
| ------ | ------ |
| GitHub | https://github.com/ |
| Github reposetry (source code) | [plugins/googledrive/README.md][PlGd] |

## Contributors

Calicat_ [[github]](github)
