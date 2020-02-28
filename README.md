## Attention! The answers are not perfect and many are missed. Do not copy completely!
## Внимание! Ответы не идеальны и многие пропущены, не копируйте полностью.

### Questions [English]

1) For example in the database MySQL we have tables posts and post_ext_attributes, with typical columns.
Tables have a relationship posts.id = post_ext_attributes.post_id.
The Laravel framework is used to extract data, and the Laravel model can be used for each table.
The task is to get the last 100 entries from the posts table along with additional fields in the post_ext_attributes.
How is it best to do that? Write the code.

> The fastest solution is to install through Composer Corcel a set of model classes for working with the Wordpress database.
Make the config setting and call the Post class method via php script:

Example:
```
$resultPosts = Post::status('publish')->type('post')->newest()->paginate(100);

foreach ($resultPosts as $post) {
	echo $post->title; // post title
	echo $post->content; // post content
	echo $post->excerpt; // post quote
}
```

2) How useful is column indexing in the MySQL?

> For example, indexing id columns in posts occurs automatically because they are primary keys,
but recommend indexing columns that reference id in other tables. In that case, these will become external keys.

3) If, when adding a function, you find similar functionality/block of code (which is already on the site), how will you do?

> If duplicate code is detected, the problem must be solved immediately after detection.
As this may result in a problem in the future. Similar code which is more than 3-5 lines already has to be reduced to separate functions.
If the methods of the class are too large, divide into small private methods and then use them in public methods.
Encapsulation is common to use everywhere for safe work on code.

4) PHP usually does not allow more than one class to inherit using the extensions statement,
but if you want to inherit methods from different parts of code, how can you do this?

> ok boomer

5) If on the site the form of applications was attacked by bots, how can you protect against it?

> 1) Connect the site to a CDN that provides protection against ddos.
> 2) Put on the form the current version of the captch from Google, etc.
> 3) Configure a spam filter for the mail server.

6) How do I prevent SQL injections and XSS attacks?

> There are two types of XSS attacks (reflected and stored).
Reflected xss occurs when filtering of data received from the user.
Stored xss occurs when filtering the data load from the user.
Backdoor script, which is stored on the server and when the script page is opened, is valid on the server.
The easiest protection against XSS is to shield all incoming characters.
ENT_QUOTES converts all kinds of quotation marks.

```
$userName = $_GET['name'];
$userName = htmlspecialchars($userName, ENT_QUOTES);
```

> You can shield symbols using the strip_tags().
SQL injection protection uses popular features to shield quotes from user data.
mysql_real_escape_string or mysqli_real_escape_string

> Using the PDO model improves protection by preventing multi-command queries.
