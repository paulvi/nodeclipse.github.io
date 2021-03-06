---
layout: share
title: JavaScript SpreadSheet/DataGrid
---

### {{ page.title }}

<p class="meta">20 August 2013</p> by Paul Verest

NOTE: This is [open-source article you can contribute and extend](https://github.com/Nodeclipse/www.nodeclipse.org/tree/gh-pages/_posts).

### Looking closely

> Advice: When started search never, never stop on the first finding, but use it as base for search and comparison.
When it is the best it is connected with other solutions more then any.

I started my search from DHTMLX, then googling. When a got several results, I asked friend.
Then I went to StackOverflow.com that revealed a bit different picture.

Popular free open-source grids jqGrid, Flexigrid, SlickGrid, DataTables are all dependent on jQuery.

#### Handsontable

added 2013-08-29.

<http://handsontable.com/> <https://github.com/warpech/jquery-handsontable> 2200 stars Marcin Warpechowski

![](/img/share/grid-handontable.PNG) 

Live example

<script src="http://handsontable.com/lib/jquery.min.js"></script>
<script src="http://handsontable.com/dist/jquery.handsontable.full.js"></script>
<link rel="stylesheet" media="screen" href="http://handsontable.com/dist/jquery.handsontable.full.css">
<link rel="stylesheet" media="screen" href="http://handsontable.com/demo/css/samples.css">

<style type="text/css">
body {background: white; margin: 20px;}
h2 {margin: 20px 0;}
.handsontable .currentRow {
  background-color: #E7E8EF;
}

.handsontable .currentCol {
  background-color: #F9F9FB;
}
</style>

<script type='text/javascript'>//<![CDATA[ 

$(document).ready(function () {

  function getCarData() {
    return [
      ["Nissan", 2009, "black", "black"],
      ["Nissan", 2006, "blue", "blue"],
      ["Chrysler", 2004, "yellow", "black"],
      ["Volvo", 2012, "white", "gray"]
    ];
  }
  
  var data = [
    ["", "Kia", "Nissan", "Toyota", "Honda"],
    ["2008", 10, 11, 12, 13],
    ["2009", 20, 11, 14, 13],
    ["2010", 30, 15, 12, 13]
  ];
  
  $("#example1").handsontable({
    data: data,
    minRows: 5,
    minCols: 6,
    minSpareRows: 1,
    currentRowClassName: 'currentRow',
    currentColClassName: 'currentCol',
    autoWrapRow: true,
    colHeaders: true,
    rowHeaders: true
  });
  
  $("#example1").handsontable('selectCell', 3, 3);
  
  function bindDumpButton() {
      $('body').on('click', 'button[name=dump]', function () {
        var dump = $(this).data('dump');
        var $container = $(dump);
        console.log('data of ' + dump, $container.handsontable('getData'));
      });
    }
  bindDumpButton();

});
//]]>  

</script>

<div class="handsontable" id="example1"></div>



##### Similar projects

> I want to stay motivated to keep Handsontable the best possible editable datagrid on the Web. Therefore, I invite you to check out alternative projects. I would love to receive feedback if you would like to import some of their features to Handsontable.

 - [DataTables](http://datatables.net/)
 - [SlickGrid](https://github.com/mleibman/SlickGrid)
 - [jqGrid](http://www.trirand.com/blog/)
 - [jTable](http://www.jtable.org/)
 - [jui_datagrid](http://www.pontikis.net/labs/jui_datagrid/)
 - [ParamQuery](http://paramquery.com/)
 - [Ember Table](http://addepar.github.io/ember-table/)
 - [Backgrid.js](http://backgridjs.com/)
 - [dgrid](http://dojofoundation.org/packages/dgrid/)

#### SlickGrid

A friend of mine advised me [SlickGrid](https://github.com/mleibman/slickgrid), that was great help because I could not find it.
 (Now I added it into Wikipedia, so maybe you have already found this way).
 
It is just 1 year old project hosted on GitHub, that grew popular (3000+ stars).
 However it is personal projects and the author seems to be overwhelmed with issues and Pull Requests stream. 

[project wiki](https://github.com/mleibman/SlickGrid/wiki), [online examples](https://github.com/mleibman/SlickGrid/wiki/Examples)

![](/img/share/grid-slickgrid-grouping.PNG) 

SlickGrid seems to focus on performance from the very beginning. 50k+ rows is quite normal.

#### jqGrid

> jQuery Grid 1.0 beta
May 5th, 2007
jQuery Grid is my first jQuery plugin...

[project home](http://www.trirand.com/blog/), [sources](https://github.com/tonytomov/jqGrid),
 [online examples](http://www.trirand.com/blog/jqgrid/jqgrid.html)

![](/img/share/grid-jqgrid-subgrid.PNG) 

jqGrid is oldie, with a lot of online [info](http://www.trirand.com/blog/?p=1125) and maybe some dust.
It supports data from XML sources, it is likely has started from XML then added JSON.

jqGrid is foundation for commercial offering Trirand jqSuite <http://www.trirand.net>.

#### Flexigrid

Very lean web site <http://flexigrid.info/> has  examples, and all links. [code on GitHub](https://github.com/paulopmx/Flexigrid) 400 stars 

![](http://flexigrid.info/images/flash.png)

Last code update 4 month ago, seems a bit quiet.   

#### DataTables

DataTables <https://datatables.net>

![](/img/share/grid-datatables.PNG) 

> In order for DataTables to be able to function correctly, the HTML for the target table must be laid out
 in a well formed manner with the 'thead' and 'tbody' sections declared.
 
[sources on GitHub](https://github.com/DataTables) 900 stars

The development went plugin way: Core DataTabled is now stable for a year, while development goes in additiona features. 

#### Other 

- Long list of jQuery UI plugings: 
[jQuery UI Frameworks To Improve Visitors’ User Experience – 25 Plugins]
(http://www.designyourway.net/blog/resources/jquery-ui-frameworks-to-improve-visitors-user-experience-25-plugins/)

[SlickGrid Vs JQGrid](http://stackoverflow.com/questions/7000048/slickgrid-vs-jqgrid)
 
### Googling 

What I could find in the very beginning by googling (P.S. was not actually the best way to start):

#### DHTMLX

[site](http://www.dhtmlx.com/docs/company.shtml), [wikipedia](http://en.wikipedia.org/wiki/Dhtmlx)

<http://www.dhtmlx.com/docs/products/dhtmlxSpreadsheet/>

> dhtmlxSpreadsheet is an open source spreadsheet widget written in JavaScript and PHP that allows you
 to quickly add an Excel-like, editable data table on a web page. It is also available as a plugin for WP, Joomla, etc. 

![](http://www.dhtmlx.com/docs/products/dhtmlxSpreadsheet/images/spreadsheet_math.png)

Free for only GPL-ed projects, then $149 or $449

It exists since 2005 and grow popular, there are some plugins. However it is not fully free, and not pure JavaScript.
Though it is the closest approximation to Excel.

#### jQuery.sheet

<http://jqueryplugins.weebly.com/jquerysheet.html> by Visopdev <http://visop-dev.com/Project+jQuery.sheet>

[online demo](http://jquerysheet.googlecode.com/svn/branches/3.x/jquery.sheet.html)

Was not tried yet.

#### Simple Spreadsheet

http://www.simple-groupware.de/cms/spreadsheet/home

[company site](http://www.simple-groupware.de/cms/), [wikipedia](http://en.wikipedia.org/wiki/Simple_Groupware)

http://en.wikipedia.org/wiki/Simple_Spreadsheet

<tbody><tr><td align="center"><a class="urllink" href="http://www.simple-groupware.de/cms/ext/files/SpreadsheetThumbs/simple_spreadsheet_05_en.jpg" rel="nofollow">
<img src="http://www.simple-groupware.de/cms/ext/files/SpreadsheetThumbs/simple_spreadsheet_05_en.jpg" alt=""></a><br>Simple Spreadsheet (0.5)</td><td align="center">
<a class="urllink" href="http://www.simple-groupware.de/cms/ext/files/Spreadsheet/simple_spreadsheet_05_en_charts.jpg" rel="nofollow">
<img src="http://www.simple-groupware.de/cms/ext/files/SpreadsheetThumbs/simple_spreadsheet_05_en_charts.jpg" alt=""></a><br>Simple Spreadsheet (0.5) - Charts</td></tr>
<tr><td>&nbsp;</td><td>&nbsp;</td></tr>
<tr><td align="center"><a class="urllink" href="http://www.simple-groupware.de/cms/ext/files/Spreadsheet/simple_spreadsheet_04_en_offline.jpg" rel="nofollow">
<img src="http://www.simple-groupware.de/cms/ext/files/SpreadsheetThumbs/simple_spreadsheet_04_en_offline.jpg" alt=""></a><br>Simple Spreadsheet (0.4)</td>
</tbody>

Was not tried yet.

#### Sheetster

<http://en.wikipedia.org/wiki/Sheetster> <http://sourceforge.net/projects/sheetster/>

> 0 Downloads (This Week)  
> Last Update: 2012-12-13  

Seems to be dead. I have not tried.

#### EditGrid

![](http://feed.editgrid.com/wordpress/wp-content/uploads/2008/09/MarketMonitor2.png)

http://www.editgrid.com/

Was not tried yet.

#### jqwidgets

Nice commercial widgets based on jQuery. http://www.jqwidgets.com/

<http://www.jqwidgets.com/jquery-widgets-demo/demos/jqxgrid/index.htm#demos/jqxgrid/spreadsheet.htm>

### Other lists

- [List of Online Spreadsheets](http://en.wikipedia.org/wiki/List_of_online_spreadsheets)
- [Comparison of spreadsheet software](http://en.wikipedia.org/wiki/Comparison_of_spreadsheet_software)

### Conclusion

There are a lot of commercial tools with varying degree of quality.  
Popular free open-source grids jqGrid, Flexigrid, SlickGrid, DataTables are all dependent on jQuery.  
I am going to try open-source SlimGrid first. It is the newest projetc with ideas for performance optimization from the very beginning, and more closer to Excel experience.
