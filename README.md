# MaxEss API
MaxEss API makes it possible to list selected cases from the maxess.se website on your own website.

# Live Demo
Check out a live demo [here](http://maxess.se/api/demo/).

# Usage
Download and link or directly link to the js-sourcefile from the MaxEss server.
```javascript
<script type="text/javascript" src="https://maxess.se/api/src/maxess-api.js"></script>
```

# Examples
List cases. 

Note that because rest api calls are asynchronous you need to enclose your function call in an **async statement**. You also have to use the **await syntax** before the actual function.
```javascript
<script>
		
  (async () => {

      var content = '<div class="cases">';
      var posts = await mxs_get_cases(10);

      for(let i = 0; i< posts.length; i++) {

          content += '<div class="item"><div class="image"><img src="'+posts[i].caseimage.small+'"></div><div class="text"><h2>'+posts[i].title+'</h2>'+posts[i].short_desc+'</div></div>';

      }

      content += '</div>';

      $('#content-container').html(content);	

    })();
		
</script>
 ```
