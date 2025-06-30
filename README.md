# BEAMS API
BEAMS API makes it possible to list selected cases from the maxess.se website on your own website.

# Live Demo
Check out a live demo [here](http://beams.se/api/demo/).

# Usage
Download and link or directly link to the js-sourcefile from the BEAMS server.
```javascript
<script type="text/javascript" src="https://beams.se/api/src/beams-api.js"></script>
```

# Examples
### List cases ###

Note that because rest api calls are asynchronous you need to enclose your function call in an `async statement`. You also have to use the `await syntax` before the actual function call.
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
 
### Show specific case ###

Note that because rest api calls are asynchronous you need to enclose your function call in an `async statement`. You also have to use the `await syntax` before the actual function call.
```javascript
<script>
		
	(async () => {

		var post = (await mxs_get_case(id));

		var content_single = '<div class="topimage"><img src="'+post.caseimage.full+'"></div><h1>'+post.title+'</h1><div class="content">'+post.content+'</div>';

		$('#content-container').html(content_single);

	})();
		
</script>
 ```
 
# Functions
The different functions to use within the BEAMS Api.

### mxs_get_case ( _id_ ) 
Function to get a specific BEAMS case.

Attributes:

- **id**
_(Number)_ The Case id.

- **publish_date**
_(Date)_ The Case publish date.

- **start_date**
_(Date)_ The Case Start date (yyyymmdd).

- **end_date**
_(Date)_ The Case End date (yyyymmdd).

- **card_ids**
_(Array)_ Gets the id:s of the connected BEAMS Contact Cards.

- **title**
_(String)_ The Case Title.

- **permalink**
_(String)_ The Case Permalink.

- **content**
_(String)_ The Case full Content.

- **short_desc**
_(String)_ The Case short description (excerpt).

- **tag_ids**
_(Array)_ Gets the id:s of the added Tags.

- **sector_id**
_(Number)_ Gets the id of the attached Sector.

- **top_organisations**
_(String)_ The Case Top Organisations.

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
	_(String)_ The sourcefile file icon.

```javascript
/* Usage example. */

var post = mxs_get_case(id);

/* Get posts full content: */
var postcontent = post.content;

/*  Get posts full image: */ 
var postimage = post.caseimage.full;
 ```
 <details>
  <summary>Show post return value</summary>
	
  
```javascript
/* Usage example. Displaying return value of specific post */

var post = mxs_get_case(id);
console.log(post);
	
/* Output: */
	
{
    "id": 1918,
    "publish_date": "2021-04-08T12:55:40",
    "card_ids": [
        {
            "id": 183
        },
        {
            "id": 465
        }
    ],
    "title": "An X-ray look on an innovative steel",
    "permalink": "https://maxess.se/case/an-x-ray-look-on-an-innovative-steel/",
    "content": "\n<p>The company Ovako has developed the innovative Hybrid Steel and wants to gain a more thorough understanding of its composition at the nanometre level. Together with researchers from Chalmers University of Technology they performed X-ray experiments that can help refining the production process of their new proprietary material.</p>\n\n\n\n<h2><strong>A stronger and more efficient steel</strong></h2>\n\n\n\n<p>Ovako is a leading European manufacturer of engineering steel serving many industry sectors such as bearing, transportation, and manufacturing. Ovako developed and patented the Hybrid Steel, a type of steel that obtains its peculiar high strength by combining precipitation of intermetallic NiAl precipitates and carbides. Due to its unique composition, the precipitation process of Hybrid Steel is rather complex and still partially undescribed. By performing X-ray scattering, Ovako aims at gaining advanced in-depth understanding of the heat treatment used in the precipitation process. This additional</p>\n\n\n\n<figure class=\"wp-block-image size-large\"><img loading=\"lazy\" width=\"1024\" height=\"683\" src=\"https://maxess.se/wp-content/uploads/2021/04/ovako-bars-imatra-1024x683.jpg\" alt=\"\" class=\"wp-image-1919\" srcset=\"https://maxess.se/wp-content/uploads/2021/04/ovako-bars-imatra-1024x683.jpg 1024w, https://maxess.se/wp-content/uploads/2021/04/ovako-bars-imatra-300x200.jpg 300w, https://maxess.se/wp-content/uploads/2021/04/ovako-bars-imatra-768x512.jpg 768w, https://maxess.se/wp-content/uploads/2021/04/ovako-bars-imatra-1536x1024.jpg 1536w, https://maxess.se/wp-content/uploads/2021/04/ovako-bars-imatra-2048x1365.jpg 2048w, https://maxess.se/wp-content/uploads/2021/04/ovako-bars-imatra-1800x1200.jpg 1800w, https://maxess.se/wp-content/uploads/2021/04/ovako-bars-imatra-1200x800.jpg 1200w\" sizes=\"(max-width: 1024px) 100vw, 1024px\" /><figcaption>Steel bars in an Ovako factory. Source: ovako.com</figcaption></figure>\n\n\n\n<h2><strong>More data, faster</strong></h2>\n\n\n\n<p>The precipitates composing the Hybrid Steel are very small, usually on the scale of tens of nanometres. Identifying and characterising these precipitates with conventional techniques such as transmission electron microscopy (TEM) or atom probe tomography (APT) is a time-consuming process. In contrast, synchrotron X-rays allow to reach the same or even higher resolution and collect a significant amount of data in less time. Furthermore, the fast acquisition possible at synchrotron facilities also allows to study the precipitation process in situ. Thus, synchrotron light presents significant advantages that can facilitate Ovako’s mission of optimising their steel.</p>\n\n\n\n<h2><strong>New opportunities for the development of Hybrid Steel</strong></h2>\n\n\n\n<p>A team of researchers from Ovako in collaboration with scientists from Chalmers University of Technology performed simultaneous Wide-Angle X-ray Scattering (WAXS) and Small-Angle X-ray Scattering (SAXS) at the Petra III synchrotron in Hamburg, Germany. The in-situ measurements were carried out using a Linkam furnace with heat treatment times ranging from 1 to 20 hours. The researchers were able to acquire a large amount of data on the heat-treated samples and characterised the precipitates both in size and structure. In-situ experiments generated unprecedented observations of the development of the precipitates over time during the heat treatment.</p>\n\n\n\n<p>Overall, the experiments provided Ovako with precious information of their Hybrid Steel. This knowledge is instrumental for the company and can help not only to optimise heat treatment procedures, but also to refine and diversify the production of Hybrid Steel.</p>\n\n\n\n<figure class=\"wp-block-image size-large\"><img loading=\"lazy\" width=\"683\" height=\"1024\" src=\"https://maxess.se/wp-content/uploads/2021/04/production-smedjebacken-3-683x1024.jpg\" alt=\"\" class=\"wp-image-1920\" srcset=\"https://maxess.se/wp-content/uploads/2021/04/production-smedjebacken-3-683x1024.jpg 683w, https://maxess.se/wp-content/uploads/2021/04/production-smedjebacken-3-200x300.jpg 200w, https://maxess.se/wp-content/uploads/2021/04/production-smedjebacken-3-768x1152.jpg 768w, https://maxess.se/wp-content/uploads/2021/04/production-smedjebacken-3-1024x1536.jpg 1024w, https://maxess.se/wp-content/uploads/2021/04/production-smedjebacken-3-1365x2048.jpg 1365w, https://maxess.se/wp-content/uploads/2021/04/production-smedjebacken-3-1200x1800.jpg 1200w, https://maxess.se/wp-content/uploads/2021/04/production-smedjebacken-3-800x1200.jpg 800w\" sizes=\"(max-width: 683px) 100vw, 683px\" /><figcaption>Smedjebacken Steel mill Production.&nbsp; Photo: Ebba Persson&nbsp; Source: ovako.com</figcaption></figure>\n\n\n\n<p></p>\n",
    "short_desc": "<p>Ovako has developed the innovative Hybrid Steel and wants to gain a more thorough understanding of its composition at the nanometre level. Together with researchers from Chalmers University of Technology they performed X-ray experiments that can help refining the production process of their new proprietary material.</p>\n",
    "tag_ids": [
        200,
        106
    ],
    "sector_id": 3,
    "top_organisations": "Ovako",
    "start_date": "20181101",
    "end_date": "20200301",
    "caseimage": {
        "full": "https://maxess.se/wp-content/uploads/2021/04/ovako-top-image1-aspect-ratio-2700-1100.png",
        "medium": "https://maxess.se/wp-content/uploads/2021/04/ovako-top-image1-aspect-ratio-2700-1100-1024x417.png",
        "small": "https://maxess.se/wp-content/uploads/2021/04/ovako-top-image1-aspect-ratio-2700-1100-300x122.png",
        "thumbnail": "https://maxess.se/wp-content/uploads/2021/04/ovako-top-image1-aspect-ratio-2700-1100-150x150.png"
    },
    "sourcefiles": [
        {
            "id": 1922,
            "title": "Understanding heat-treatment of Hybrid Steel® using in-situ and ex-situ synchrotron X-ray diffraction",
            "url": "https://maxess.se/wp-content/uploads/2021/04/2018-04433_ovako.pdf",
            "filename": "2018-04433_ovako.pdf",
            "filesize": 432774,
            "filetype": "pdf",
            "icon": "https://maxess.se/wp-includes/images/media/document.png"
        }
    ]
}
 ```
</details>

### mxs_get_cases ( _number_of_cases_ ) 
Function to get the BEAMS cases.


```javascript
/* Usage example. */

var posts = mxs_get_cases(10);

for(let i = 0; i< posts.length; i++) {

	/* Get post id: */
	var postid = posts[i].id;

	/*  Get posts thumbnail image: */ 
	var postimage = posts[i].caseimage.thumbnail;

}
 ```
 
 
