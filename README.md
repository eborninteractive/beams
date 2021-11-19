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

Note that because rest api calls are asynchronous you need to enclose your function call in an `async statement`. You also have to use the `await syntax` before the actual function.
```javascript
<script>
		
	(async () => {

		var content = '<div class="cases">';
		var posts = await mxs_get_cases(10);

		for(let i = 0; i< posts.length; i++) {

			content += '<div class="case"><div class="image"><img src="'+posts[i].caseimage.thumbnail+'"></div><div class="text"><h2>'+posts[i].title+'</h2>'+posts[i].short_desc+'</div></div>';

		}

		content += '</div>';

		$('#content-container').html(content);	

	})();
		
</script>
 ```
 
Show selected case. 

Note that because rest api calls are asynchronous you need to enclose your function call in an `async statement`. You also have to use the `await syntax` before the actual function.
```javascript
<script>
		
	(async () => {

		var post = (await mxs_get_case(id));

		var content_single = '<div class="topimage"><img src="'+post[0].caseimage.full+'"></div><div class="content">'+post[0].content;

		$('#content-container').html(content_single);

	})();
		
</script>
 ```
 
# Functions
**mxs_get_cases(** _number_of_cases_ **)** – Gets Maxess Cases

Parameters:

- **id**
_(Number)_ The Case id.

- **card_ids**
_(Array)_ Gets the id:s of the connected Case Cards.

- **title**
_(String)_ The Case Title.

- **permalink**
_(String)_ The Case Permalink.

- **content**
_(String)_ The Case full Content.

- **short_desc**
_(String)_ The Case short description (excerpt).

- **caseimage**
_(Array)_ The Case main image in different formats.
	- Image formats:

	- **full**
	_(String)_ Image size: 1867x552 px
	
	- **medium**
	_(String)_ Image size: 1800x532 px
	
	- **small**
	_(String)_ Image size: 300x89 px
	
	- **thumbnail**
	_(String)_ Image size: 150x150 px
	
- **sourcefiles**
_(Array)_ The connected sourcefiles.
	- Parameters:

	- **id**
	_(Number)_ The sourcefile id.
	
	- **title**
	_(String)_ The sourcefile manually named label.
	
	- **url**
	_(String)_ The sourcefile url.
	
	- **filename**
	_(String)_ The sourcefile original filename.
	
	- **filesize**
	_(Number)_ The sourcefile filesize.
	
	- **icon**
	_(String)_ The sourcefile fileicon.

- **blocks**
_(Array)_ Gets the contents different blocks.
	- Parameters:

	- **name**
	_(String)_ The block name.
	
	- **content**
	_(String)_ Get the unformatted text content (used in specific blocks).
	
	- **url**
	_(String)_ Used for the image-block to get the image url.
	
	- **innerHTML**
	_(String)_ Get the html-formatted content.

```javascript
/* Usage examples: */

/* Get post id: */
var postid = posts[i].id;

/*  Get posts thumbnail image: */ 
var postimage = posts[i].caseimage.thumbnail;
 ```
 
 **mxs_get_case(** _id_ **)** – Get specific Maxess Case

Parameters:

- **id**
_(Number)_ The Case id.

- **card_ids**
_(Array)_ Gets the id:s of the connected Case Cards.

- **title**
_(String)_ The Case Title.

- **permalink**
_(String)_ The Case Permalink.

- **content**
_(String)_ The Case full Content.

- **short_desc**
_(String)_ The Case short description (excerpt).

- **caseimage**
_(Array)_ The Case main image in different formats.
	- Image formats:

	- **full**
	_(String)_ Image size: 1867x552 px
	
	- **medium**
	_(String)_ Image size: 1800x532 px
	
	- **small**
	_(String)_ Image size: 300x89 px
	
	- **thumbnail**
	_(String)_ Image size: 150x150 px
	
- **sourcefiles**
_(Array)_ The connected sourcefiles.
	- Parameters:

	- **id**
	_(Number)_ The sourcefile id.
	
	- **title**
	_(String)_ The sourcefile manually named label.
	
	- **url**
	_(String)_ The sourcefile url.
	
	- **filename**
	_(String)_ The sourcefile original filename.
	
	- **filesize**
	_(Number)_ The sourcefile filesize.
	
	- **icon**
	_(String)_ The sourcefile fileicon.

- **blocks**
_(Array)_ Gets the contents different blocks.
	- Parameters:

	- **name**
	_(String)_ The block name.
	
	- **content**
	_(String)_ Get the unformatted text content (used in specific blocks).
	
	- **url**
	_(String)_ Used for the image-block to get the image url.
	
	- **innerHTML**
	_(String)_ Get the html-formatted content.

```javascript
/* Usage examples: */

/* Get posts full content: */
var postid = post[0].content;

/*  Get posts full image: */ 
var postimage = post[0].caseimage.full;
 ```
