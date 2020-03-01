## Attention! The answers are not perfect and many are missed. Do not copy completely!

:beer:[ Russian questions](docs/README_RU.md)
------
### Answers [English]

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

Example:
```
$userName = $_GET['name'];
$userName = htmlspecialchars($userName, ENT_QUOTES);
```

> You can shield symbols using the strip_tags().
SQL injection protection uses popular features to shield quotes from user data.
mysql_real_escape_string or mysqli_real_escape_string

> Using the PDO model improves protection by preventing multi-command queries.

7) If the site uses jQuery, then to work with DOM elements, what do you prefer more (jQuery and/or DOM API) and why?

> JQuery is undesirable due to performance degradation and javascript tools allow you not to use jquery. jQuery works with the DOM API, but in some cases uses its implementations.
JQuery is very slow but comfortable.
Concerning the question, if the whole project is written in jquery, why sso standard.
The code will only become confusing.

8) What is best to use in the JavaScript code to achieve as smooth an animation as possible? Given that the animation is not simple, the coordinates of the elements being animated are calculated using complex functions.

> There are 2 types of animations. Described with CSS and JavaScript.
If you create a smooth animation, there are keywords (ease-in, ease-out, linear, and so on).
The smoothness of animations works on Bezier curves, and you can customize them as needed.

Example:
```
transition: transform 100ms ease-in-out(0.2, 0.3, 0.4, 0.5);
```

> To prevent framerate from being low on devices, avoid animating feature properties.

9) In the JavaScript code, there is a for loop within which the setTimeout call is nested. At each iteration, the local variable i is incremented by one, and in the anonymous function that is called, setTimeout is the output of that variable i to the console. Which digits will appear in the console at 10 iterations of the loop?

> This example uses the work of closure and scope areas.
In this code, a timer within the body of the cycle will start 10 times when one timer expires, the cycle will perform 10 iterations and the final output i will be 10.

10) Write an asynchronous loop on the JavaScript, which will output digits from 1 to 10 to the console in order, and after 10 will output digits from 9 to 0

Code:
```
const j = 11;
for (let i = 1; i <= j; i++) {
    if (i == j) {
        for (let k = 9; k >= 0; k--) {
            asynchronousProcess(function() {
                console.log(k);
            });
        }
    } else {
        asynchronousProcess(function() {
            console.log(i);
        });
    }
}

var array = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
let i = 0;

function printInc(i) {
  console.log(array[i]);
  i++;
}

await new Promise(resolve => setTimeout(() => resolve(printInc(i)), 1));
```

11) How do I prevent RAM leakage in PHP code, and is there a memory leakage in JavaScript code?

> First, you need to determine the leak in the scripts.
The fastest solution will be to install a ready-made profiler to monitor memory.

The most popular:
1) [Xhprof](http://pecl.php.net/package/xhprof) + [Xhgui](https://github.com/perftools/xhgui)
2) [php-memprof](https://pecl.php.net/package/memprof)
3) [gperftools](https://github.com/gperftools/gperftools)

> A long option, but the capabilities of php, namely the use of memory_get_usage or memory_get_peak_usage functions.
But these features do not track dedicated memory within libraries.

> In javascript, leaks can also occur, although memory management automatically works there.
For example, the user does not close the tab and works continuously with the interface on javascript.
For javascript monitor scripts can be used on F12 in any browser, the Profiles tool and then look at Timeline memory.

12) By the link demonstration of various methods (tests) of layout (HTML, CSS) [tests](tests), please try them again. The Annotation.txt file contains a description of each receipt (test).

Task 1: [Video to show the finished solution](tests/task1/example.mp4)

Answer: [Script](tests/task1/code)


Task 2: [Video to show the finished solution](tests/task2/example.mp4)

Answer: [Script](tests/task2/code)


Task 3: [Video to show the finished solution](tests/task3/example.mp4)

Answer: [Script](tests/task3/code)


Task 4: [Video to show the finished solution](tests/task4/example.mp4)

Answer: [Script](tests/task4/code)


Task 5: [Video to show the finished solution](tests/task5/example.mp4)

Answer: [Script](tests/task5/code)


Task 6: [Video to show the finished solution](tests/task6/example.mp4)

Answer: [Script](tests/task6/code)


Task 7: [Video to show the finished solution](tests/task7/example.mp4)

Answer: [Script](tests/task7/code)


Task 8: [Video to show the finished solution](tests/task8/example.mp4)

Answer: [Script](tests/task8/code)

13) If you have a problem solving the problem, what will you do? Will you be looking for a solution yourself by reading forums/documentation and/or trying to ask other developers in a shared chat?

> First, you have to look for the right information on your own to solve the problem. If not found on open resources then ask.

14) If in practice your experience is not enough, are you ready for training? And how easy is it for you to learn new technologies?

> Given that modern and new technologies are now focused on simplicity. They are not difficult to study if an old but proven base has already been studied.
When learning C, Python is easier to teach, like any other.

15) Can you roughly predict the timing of a certain task? Simple to complex, which may take more than one business day to solve.

Typically, dates are calculated based on:
1. The quantity of work at the beginning and in the process (for example, editing a project).
2. Taking into account the use of certain tools for work (new or old).
3. The number of people resources allocated to the project.

16) Do you use the IDE to work with the code?

> IDE is desirable for large projects.

The following options are available from the IDE:
1) [NetBeans](https://netbeans.org)
2) [Eclipse](https://www.eclipse.org)
3) [Visual Studio Code](https://code.visualstudio.com)
