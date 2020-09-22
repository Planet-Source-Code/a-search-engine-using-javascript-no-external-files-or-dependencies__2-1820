<div align="center">

## A Search Engine using JavaScript\! No external files or dependencies


</div>

### Description

This code allows you to search an amphorus database

that is built into the page.
 
### More Info
 
You need to make the database (it is a hidden field)

The user needs to input a search string

You need to know HTML

The pages, naturally

None known, however, if you find any cantact me at:

thundersoft@hotmail.com


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[N/A](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/empty.md)
**Level**          |Advanced
**User Rating**    |5.0 (15 globes from 3 users)
**Compatibility**  |
**Category**       |[Internet/ Browsers/ HTML](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/internet-browsers-html__2-68.md)
**World**          |[Java](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/java.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/a-search-engine-using-javascript-no-external-files-or-dependencies__2-1820/archive/master.zip)

### API Declarations

The HTML is within the code


### Source Code

```
<html>
<title>JavaScript Search Engine Script with Descriptions</title>
<!--This code is originally from Infohiway.com, however, it has been modified-->
<body bgcolor=white>
<FORM NAME="database">
<INPUT TYPE="hidden" NAME="list" VALUE='your_first_page.htm~Your First Page Title|keywords for first file go here separated by spaces^First page description here!*http://you.can.use.full.urls.com/your_second_page.htm~Your Second Page Title|keywords for second file go here separated by spaces^Second page description here!*your_third_page.htm~Your Third Page Title|keywords for third file go here separated by spaces^Third page description here!*your_fourth_page.htm~Your Fourth Page Title|keywords for fourth file go here separated by spaces^Fourth page description here!*'>
</FORM>
<script language="JavaScript">
<!--
function Page(url,title,keywords,description) {
 while ((url.length > 0) && (url.charAt(0) == " ")) {
 url = url.substring(1,url.length);
 }
 this.url = url;
 while ((title.length > 0) && (title.charAt(0) == " ")) {
 title = title.substring(1,title.length);
 }
 this.title = title;
 this.keywords = keywords;
 this.description = description;
 return this;
}
function Database() {
 var pos = 0;
 while ((pos1 = amorphous.indexOf("~",pos)) != -1) {
 pos2 = amorphous.indexOf("|",pos1+1);
 pos3 = amorphous.indexOf("^",pos2+1);
 pos4 = amorphous.indexOf("*",pos3+1);
 if ((pos2 != -1)
 && (pos2 < pos3) && (pos3 < pos4)
 && (pos4 <= amorphous.indexOf("*",pos))) {
  this[database_length++] = new Page(amorphous.substring(pos,pos1),
  amorphous.substring(pos1+1,pos2),
  amorphous.substring(pos2+1,pos3),
  amorphous.substring(pos3+1,pos4));
  pos = pos4+1;
 } else { // error reading amorphous database
  if (pos+30 <= amorphous.length)
  alert('Error reading in amorphous database around "'
   + amorphous.substring(pos,pos+30) + '"');
  pos = amorphous.indexOf("*",pos) + 1;
 }
 }
 return this;
}
function search(str) {
 menu_length = 0;
 temp = new Object();
 temp_length = 0;
 words_length = 0;
 words = new Object();
 pos = 0;
 while ((pos = str.indexOf(" ")) != -1
 && and_search != "exact") {
 words[words_length] = str.substring(0,pos);
 if (words[words_length].length > 0)
  words_length++;
 if (str.length == 1)
  str="";
 else
  str = str.substring(pos+1,str.length);
 }
 if (str.length > 0)
 words[words_length++] = str;
 for (q=0;q<words_length;q++) {
 temp_length = 0;
 str = words[q].toLowerCase();
 len = (and_search=="and"&&q>0?menu_length:database_length);
 for (n=0; n<len; n++) {
  if (and_search=="and"&&q>0) {
  combo = (menu[n].title + " " + menu[n].description
   + " " + menu[n].keywords).toLowerCase();
  } else {
  combo = (database[n].title + " " + database[n].description
   + " " + database[n].keywords).toLowerCase();
  }
  if (combo.indexOf(str) != -1) // found
  temp[temp_length++] = (and_search=="and"&&q>0?menu[n]:database[n]);
 }
 if (and_search!="and" && q>0) {
  added = 0;
  for (i=0;i<temp_length;i++) {
  duplicate = false;
  for (j=0;j<menu_length&&!duplicate;j++) {
   if (menu[j] == temp[i]) {
   duplicate = true;
   }
  }
  if (!duplicate)
   menu[menu_length+(added++)] = temp[i];
  }
  menu_length += added;
 } else {
  for(h=0;h<temp_length;h++)
  menu[h] = temp[h];
  menu_length = temp_length;
 }
 }
}
function entry() {
 if ((document.entryform.keyword.value.length == 0)
 || (document.entryform.keyword.value == " ")) {
 alert("First you must enter a keyword to search for.");
 return false;
 }
 and_search = (document.entryform.and_or.selectedIndex == 0?"and":"or");
 if (document.entryform.and_or.selectedIndex == 2)
 and_search = "exact";
 location.href = location.pathname + "?"
 + escape(document.entryform.keyword.value)
 + (and_search != "or"?"&"+and_search:"");
 return false;
}
function redWord(str) {
 for(r=0; r<words_length; r++) {
 pos = -3;
 word = words[r].toLowerCase();
 while ((pos = str.toLowerCase().indexOf(word,pos+3)) != -1) {
  val = pos+word.length;
  str = str.substring(0,pos) + "*"
  + str.substring(pos,val) + "|"
  + str.substring(val,str.length);
 }
 }
 pos = -16;
 while ((pos = str.toLowerCase().indexOf("*",pos+16)) != -1)
 str = str.substring(0,pos) + "<font color=red>"
  + str.substring(pos+1,str.length);
 pos = -7;
 while ((pos = str.toLowerCase().indexOf("|",pos+7)) != -1)
 str = str.substring(0,pos) + "</font>"
  + str.substring(pos+1,str.length);
 return str;
}
var amorphous = document.database.list.value;
temp_str = amorphous.substring(amorphous.length-2,amorphous.length);
if (temp_str.indexOf("*") == -1)
 amorphous += "* ";
else
 amorphous += " "; // amorphous database must have characters after last asterisk
database_length = 0; // Netscape 2 fix
var database = new Database(); // read in from amorphous database
menu_length = 0; // Netscape 2 fix
var menu = new Object();
string = "";
and_search = "or";
if (location.search.length > 1) {
 string = unescape(location.search.substring(1,location.search.length));
 pos = 0;
 while ((pos = string.indexOf('"',pos)) != -1) {
 string = string.substring(0,pos) + '\\"' + string.substring(pos+1,string.length);
 pos += 2;
 }
 if (string.substring(string.length-4,string.length) == "&and") {
 string = string.substring(0,string.length-4);
 and_search = "and";
 } else if (string.substring(string.length-6,string.length) == "&exact") {
 string = string.substring(0,string.length-6);
 and_search = "exact";
 } else if (string.substring(string.length-3,string.length) == "&or") {
 string = string.substring(0,string.length-3);
 and_search = "or";
 }
 search(string);
}
document.write('<form name="entryform" onSubmit="return entry()">'
 +'<b>Search for:</b><br><input type="text" size=20 '
 +'name="keyword" value="'+string+'"> '
 +'<input type="button" value="Search" onClick="entry()"><br><select name="and_or" '
 +'size=1><option'+(and_search=="and"?" selected":"")+'>find all words '
 +'(AND)<option'+(and_search=="or"?" selected":"")+'>find any word '
 +'(OR)<option'+(and_search=="exact"?" selected":"")+'>exact '
 +'match</select></form><br>');
if (location.search.length > 1)
 document.write('<b>Results:</b><br><br>\n');
// eliminate the keywords portion of the statement below to eliminate them from your display
for (n=0; n<menu_length; n++)
 document.write('<b><a href="'+menu[n].url+'">'+menu[n].title
 +'</a></b><br>'+redWord(menu[n].description)+'<br>Keywords: '
 +redWord(menu[n].keywords)+'<br><br>\n');
if ((menu_length == 0) && (location.search.length > 1))
 document.write('Keyword "'+string+'" not found!\n');
// -->
</script>
<hr noshade>
<br><br>
The following is just a demonstration of how you would link to search.htm from other pages:<br><br>
<!-- if you want to link from another page, just copy the JavaScript code below
   and paste it into your other page -->
<script language="JavaScript">
<!--
// enter full or relative URL to your search page
var search_htm_url = "your_search_page_name.htm";
function searchPage() {
 if ((document.searchpage.keyword.value.length == 0)
 || (document.searchpage.keyword.value == " ")) {
 alert("First you must enter a keyword to search for.");
 } else {
 sel = document.searchpage.and_or.selectedIndex;
 location.href = search_htm_url + "?"
  + escape(document.searchpage.keyword.value)
  + (sel==0?"&and":(sel==2?"&exact":"&or"));
 }
 return false;
}
document.write('<form name="searchpage" onSubmit="return searchPage()">'
 +'Search for: <input type="text" size=15 name="keyword"> '
 +'<input type="button" value="Search" onClick="searchPage()"><br>'
 +'<select name="and_or" size=1><option>find all words (AND)<option>find any word '
 +'(OR)<option>exact match</select><br>"*" wildcards are valid</form>');
// -->
</script>
<br><br>
Or you can just use direct links. For instance, if you wanted to search for the keyword "javascript", then you would link to <a href="search.htm?javascript">search.htm?javascript</a>. Or search for "javascript" or "perl": <a href="search.htm?javascript%20perl&or">search.htm?javascript%20perl&or</a>. Or for "javascript" and "perl": <a href="search.htm?javascript%20perl&and">search.htm?javascript%20perl&and</a>. Or for the exact phrase "javascript perl": <a href="search.htm?javascript%20perl&exact">search.htm?javascript%20perl&exact</a>. (note that %20 is the URL escaped form of a space).
</body>
</html>
```

