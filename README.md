# SASS
SAAS Tuotorial
---------------

Installation of SASS:
----------------------

System Requirements for SASS:
------------------------------
Operating System : Cross-platform
Browser Support : IE (Internet Explorer 8+), Firefox, Google Chrome, Safari, Opera
Programming Language: Ruby

Windows
------------
Before you start using Sass you will need to install Ruby. 
The fastest way to get Ruby on your Windows computer is to use Ruby Installer. It's a single-click installer that will get everything set up for you super fast.
The installer will also install a Ruby command line powershell application that will let you use the Ruby libraries.

Installation of Ruby:
----------------------
Step(1):Open the link https://www.ruby-lang.org/en/downloads/ and download the setup.exe as per your system requirement

Step(2): Next, run the setup to install the Ruby on the System

Step(3): Next, add Ruby bin folder to your PATH User Variable and System Variable to work with gem command. you can also set this varaible at time of installation.

If not set at time of installation then follow the below steps:

Path User Variable:

--Right Click on My Computer.

--Select Properties.

--Next, select Advanced tab and click on Environment Variables. 

--Under Environment Variables window, double click on the PATH.

--You will get an Edit User Variable box. Add ruby bin folder path in the Variable value field as C:\Ruby\bin. If path is already set for other files then put semicolon after that and add the Ruby folder path. 

System Variable:

--Click on New Button.

--Next, New System Variable block gets displayed.

--Enter RubyOpt in the Variable name field and rubygems in the Variable value field. After writing the Variable name and value, click on OK button.


step(4): Go in Ruby installed folder with cmd and install sass with gem
		c:/Ruby> gem install sass

if SASS is not sucessfull and getting error related to TCP/IP then set proxy with following command and after that repeat step:4

SET HTTP_PROXY=http://%USER%:%PASSWORD%@%SERVER%:%PORT%

if got following error :

ERROR:  Could not find a valid gem 'sass' (>= 0), here is why:
              Unable to download data from https://rubygems.org/ - SSL_connect retur
    ned=1 errno=0 state=SSLv3 read server certificate B: certificate verify failed (
    https://rubygems.org/latest_specs.4.8.gz)

then use following command:
		c:/Ruby>  gem source -a http://rubygems.org/
and after that repeat step:4

Reason:The error has something to do with being vulnerable to the Poodle SSL bug, it will not be verified for that reason. If there's a way to upgrade to a better certificate, but at the time of writing this answer, I could not find the upgraded certificate.
I used the non-SSL host instead, altough I should note that this is not the best nor a permanent solution, it lacks security.

Double-check. You should now have Sass installed, but it never hurts to double-check. In your terminal application you can type:
sass -v

Starting your first app with SASS:
------------------------------------
For creating your first app with SASS, you need to follow with below steps:
Step1:Create a project folder under root directory of your local server.
Step2:Create a Html page,css and sass-css folder inside project folder.
Step3:Create a .scss extention file in your sass-css folder : This folder will keep your all .scss file.
	  css : folder will be used for actual css code as output
Step4: Add css file in your html page as normal way like other css files are included.
	   The name of css file will bed used as output of SASS file.
Step5: For running your sass file use following command, it will take your preprocessed Sass file and save it as a normal CSS file that you can use in your web site .
[c:\project_folder> sass sass-css/input.scss css/output.css  ] where input.scss is your sass file and  output.css is your normal css file

For dynamic edit we can set watch on folder/file 
[c:\project_folder> sass --watch sass-css/input.scss:css/output.css  ] as file
[c:\project_folder> sass --watch sass-css:css  ] as folder

Varaible Declaration in SASS:
-------------------------------
The most straightforward way to use SassScript is to use variables. Variables begin with dollar signs, and are set like CSS properties:

$font-stack:    Helvetica, sans-serif;
$primary-color: #333;

body {
  font: 100% $font-stack;
  color: $primary-color;
}

Data Types
-----------

SassScript supports seven main data types:

numbers (e.g. 1.2, 13, 10px)
strings of text, with and without quotes (e.g. "foo", 'bar', baz)
colors (e.g. blue, #04a3f9, rgba(255, 0, 0, 0.5))
booleans (e.g. true, false)
nulls (e.g. null)
lists of values, separated by spaces or commas (e.g. 1.5em 1em 0 2em, Helvetica, Arial, sans-serif)
maps from one value to another (e.g. (key1: value1, key2: value2))
SassScript also supports all other types of CSS property value, such as Unicode ranges and !important declarations. However, it has no special handling for these types. They’re treated just like unquoted strings.



Nesting in SASS:
-------------------------------

Sass will let you nest your CSS selectors in a way that follows the same visual hierarchy of your HTML.
Note : Be aware that overly nested rules will result in over-qualified CSS that could prove hard to maintain and is generally considered bad practice.

nav {
  ul {
    margin: 0;
    padding: 0;
    list-style: none;
  }

  li { display: inline-block; }

  a {
    display: block;
    padding: 6px 12px;
    text-decoration: none;
  }
}

Mixin in SASS:
---------------
A mixin lets you make groups of CSS declarations that you want to reuse throughout your site. You can even pass in values to make your mixin more flexible. 
@mixin border-radius($radius) {
  -webkit-border-radius: $radius;
     -moz-border-radius: $radius;
      -ms-border-radius: $radius;
          border-radius: $radius;
}

.box { @include border-radius(10px); }
To create a mixin you use the @mixin directive and give it a name. We've named our mixin border-radius. We're also using the variable $radius inside the parentheses so we can pass in a radius of whatever we want. After you create your mixin, you can then use it as a CSS declaration starting with @include followed by the name of the mixin. 

Extend/Inheritance in SASS
--------------------------
This is one of the most useful features of Sass. Using @extend lets you share a set of CSS properties from one selector to another.
.message {
  border: 1px solid #ccc;
  padding: 10px;
  color: #333;
  margin:10px;
}

.success {
  @extend .message;
  border-color: green;
}

.error {
  @extend .message;
  border-color: red;
}

.warning {
  @extend .message;
  border-color: yellow;
}

Operator in SASS:
------------------
Doing math in your CSS is very helpful. Sass has a handful of standard math operators like +, -, *, /, and %.

.container { width: 100%; }


article[role="main"] {
  float: left;
  width: 600px / 960px * 100%;
}

aside[role="complementary"] {
  float: right;
  width: 300px / 960px * 100%;
}


Partials in SASS:
-----------------
You can create partial Sass files that contain little snippets of CSS that you can include in other Sass files. This is a great way to modularize your CSS and help keep things easier to maintain. A partial is simply a Sass file named with a leading underscore. You might name it something like _partial.scss. The underscore lets Sass know that the file is only a partial file and that it should not be generated into a CSS file. Sass partials are used with the @import directive.


Import in SASS:
---------------
CSS has an import option that lets you split your CSS into smaller, more maintainable portions. The only drawback is that each time you use @import in CSS it creates another HTTP request. Sass builds on top of the current CSS @import but instead of requiring an HTTP request, Sass will take the file that you want to import and combine it with the file you're importing into so you can serve a single CSS file to the web browser.
Let's say you have a couple of Sass files, _reset.scss and base.scss. We want to import _reset.scss into base.scss.

// _reset.scss

html,
body,
ul,
ol {
   margin: 0;
  padding: 0;
}

// base.scss

@import 'reset';

body {
  font: 100% Helvetica, sans-serif;
  background-color: #efefef;
}


