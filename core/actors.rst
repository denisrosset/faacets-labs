Actors
======

The FolderCrawler hierarchy minics the folder hierarchy of data.

A 

.. graphviz::

  digraph foo {
  "Manager" -> "Watcher";
  "Manager" -> "Crawler";
  "Crawler" -> "Crawler1";
  "Crawler" -> "Crawler2";
  "Crawler" -> "Crawler3";
   "Manager" -> "Processor";
   "Processor" -> "Processor1";
   "Processor" -> "Processor2";
   "Processor" -> "Processor3";
   "Crawler1" -> "Watcher" [style = dotted];
   "Crawler2" -> "Watcher" [style = dotted];
   "Crawler3" -> "Watcher" [style = dotted];
   "Crawler1" -> "Processor" [style = dotted];
   "Crawler2" -> "Processor" [style = dotted];
   "Crawler3" -> "Processor" [style = dotted];
   "Processor1" -> "Watcher" [style = dotted];
   "Processor2" -> "Watcher" [style = dotted];
   "Processor3" -> "Watcher" [style = dotted];
   "Watcher" -> "Manager" [style = dotted];
  }
