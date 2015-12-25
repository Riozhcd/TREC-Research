# TREC-Research

关于TREC数据集合构建索引查询分析的实验

## 调研
* [TREC Terabyte Track](http://www-nlpir.nist.gov/projects/terabyte/)

## 开源搜索引擎

### 参考博文

[开源搜索引擎性能比较研究](http://www.360doc.com/content/13/0316/20/4310958_271929743.shtml)

### 简要介绍

* ht://Dig, 提供一组工具可以索引和搜索一个站点。提供有一个命令行工具和CGI界面来执行搜索。
尽管已经有了更新的版本了， 但是根据项目的网站, 3.1.6版是最快的版本了。

* IXE Toolkit， 是模块化C++类集合， 有一组工具完成索引和查询。Tiscali（来自意大利）提供有商业版本， 同时提供了一个非商业版本仅用于科学研究。

* Indri,是基于Lemur的搜索引擎。Lemur是用来研究语言模型和信息检索的工具。这个项目是马萨诸塞大学和CMU的合作项目的产物。

* Lucene， 是Apache 软件基金会的一个文本搜索引擎库。由于它是一个库，所以很多项目基于这个库，例如Nutch项目。
在目前，它捆绑自带的最简单的应用是索引文档集合。

* MG4J（管理前兆数据Java语言）是针对大文本集合的一个全文索引工具。由米兰大学开发。他们提供了通用的字符串和位级别的I/O的优化的类库作为副产物。

* Omega， 基于Xapian的应用。Xapian是开源的统计信息检索库，由C++开 发，但是被移植到了Python Perl  php Java Tcl C#等多种语言。

* IBM Omnifind Yahoo! Edition， 非常适合内网 搜索的搜索软件。 他结合了基于Lucene索引的内网搜索，和利用Yahoo 实现的外网搜索。

* SWISH-E（简单网页索引系统—增强版）， 是开源的索引和检索引擎。是Kevin Hughes 开发的SWISH的增强版。

* SWISH++是基于SWISH-E的索引和检索工具。尽管经过C++全部重写， 但是 没有实现SWISH-E的全部功能。

* Terrier（太字节检索）， 由苏格兰的格拉斯哥大学开发的，模块化的平台，能够快速的构架互联网，内网，和 桌面的搜索引擎。它附带了索引，查询和评估标准TREC集合的功能。

* XMLSearch， C++开发的索引和检索的一组类。利用文本操作（相等，前缀，后缀，分段）来扩展了查询能力。 Barcino（来自智利）提供了一个商 业版， 同时也有个供学术研究的非商业版。

* Zettair，（先前称为Lucy），由皇家墨尔本理工大学的搜索引擎小组开发的文本检索引擎。
主要特征是能够处理超大量的文本。支持Html和TREC数据[zettair](http://www.seg.rmit.edu.au/zettair/doc/Readme.html)

### 实验结果：

![不同文档集合各检索引擎开销](https://github.com/Riozhcd/TREC-Research/blob/master/doc/indexer.jpg)
1. ht://Dig， Lucene和XMLSearch会有固定大小的内存开销，并且前两者的内存开销与数据集的大小没有关系(30MB~120MB);IXE，MG4J，Swish-E， Swish++ 和Terrier内存开销大，呈现线性增长；针对大的数据集合要1G以上的内存开销。

![不同搜索引擎生成文件大小](https://github.com/Riozhcd/TREC-Research/blob/master/doc/indexersize.jpg)
2. Lucene, MG4J, Swish-E, Swish++, XMLSearch 和Zettair的索引大小为数据集大小的25%~35%。Terrier建立索引文件大小为原来的50%。其他还增大了。

![WT10G实验结果](https://github.com/Riozhcd/TREC-Research/blob/master/doc/WT10G.jpg)
3. 在数据集合非常的时候，只有Indri, IXE, MTerrier和Zettair的索引性能不会大幅度下降，而Swish-E， Swish++ 在给定系统参数下，根本不能够对大数据集合进行索引。

总结：
1. Lucene, MG4J, Swish-E, Swish++, XMLSearch 和Zettair的索引大小为数据集大小的25%~35%。Terrier建立索引文件大小为原来的50%。其他还增大了。

2. ht://Dig， Lucene和XMLSearch会有固定大小的内存开销，并且前两者的内存开销与数据集的大小没有关系(30MB~120MB);IXE，MG4J，Swish-E， Swish++ 和Terrier内存开销大，呈现线性增长；针对大的数据集合要1G以上的内存开销。

3. 在数据集合非常的时候，只有Indri, IXE, MTerrier和Zettair的索引性能不会大幅度下降，而Swish-E， Swish++ 在给定系统参数下，根本不能够对大数据集合进行索引。

## WT10g 数据说明

### 数据概述
============

Contents of WT10g
-----------------

WT10g consists of data distributed on 5 CDs, numbered CD1 to CD5. The
data is split into individual directories, WTX001, WTX002 and so
on. Within each directory, documents are bundled together into files
of roughly 2MB in size, numbered B01, B02 .. B50. The bundle files are
all compressed using gzip, so exist as B01.gz etc.

CD1 contains data for the following: WTX001 .. WTX024, each directory contains 50 bundle files B01.gz .. B50.gz
CD2 contains data for the following: WTX024 .. WTX048, each directory contains 50 bundle files B01.gz .. B50.gz
CD3 contains data for the following: WTX049 .. WTX072, each directory contains 50 bundle files B01.gz .. B50.gz
CD4 contains data for the following: WTX073 .. WTX096, each directory contains 50 bundle files B01.gz .. B50.gz
CD5 contains data for the following: WTX097 .. WTX104, each directory contains 50 bundle files B01.gz .. B50.gz
                                                       except WTX104, containing 7 bundle files B01.gz .. B07.gz
CD5 also contains:                   info, which has additional information generated for WT10g data, described below.

Note well: The contents of this directory ( WT10g::CD5::info ) do not
constitute part of WT10g's data.


### Data Set info directory information
None of the files in this info directory should be indexed.



#### 文件列表
It contains the following files:
README -	this file
docid_to_url -	mappings: WT10g docid -> URL (*)
homepages -	mappings: server name -> WT10g docid
in_links -	mappings: WT10g docid -> set of WT10g docids, whose pages 
                          contain (incoming) links to this page (*)
out_links -	mappings: WT10g docid -> set of WT10g docids, whose pages 
                          are named by (outgoing) links from this page (*)
servers -       server names
url_to_docid -  mappings: URL -> WT10g docid 
wt10g_to_vlc2 - mappings: WT10g docid -> VLC2 docid (*)

URLs are of the form: 		http://server_name/path
Server names are of the form: 	www.foo.com:port_number
Port numbers are of the form: 	1234 (but are usually just 80)
WT10g docids are of the form: 	WTX123-B45-6789, where the final doc 
                                number in the bundle is numbered from 1
VLC2 docids are of the form: 	IA012-003456-B078-901, where the final 
                                doc number in the bundle is numbered from 1

(*) Note well:

All info files are sorted using the Linux sort routine, using the
first entry of each line as the sort key.  Since the last component of
a WT10g docid is numbered sequentially from 1 upwards, and the sort
order is alphabetical, these files have a slightly confusing ordering,
which is not identical to the numeric ordering of the documents within
each bundle.

For example, the first entries of docid_to_url are:

WTX001-B01-1 http://www.ram.org:80/ramblings/movies/jimmy_hollywood.html
WTX001-B01-10 http://sd48.mountain-inter.net:80/hss/teachers/Prothero.html
WTX001-B01-100 http://www.ccs.org:80/hc/9607/win95.html
WTX001-B01-101 http://www.cdc.net:80/~dejavu/scuba-spec.html
WTX001-B01-102 http://www.cdm.com:80/humanres/jobs/enevga.html

after which there are a number of other entires followed by:

WTX001-B01-198 http://www.cdc.net:80/~dupre/pharmacy/CD581.html
WTX001-B01-199 http://www.cdnemb-washdc.org:80/baltimor.html
WTX001-B01-2 http://www.radio.cbc.ca:80/radio/programs/current/quirks/archives/feb1796.htm
WTX001-B01-20 http://moe.med.yale.edu:80/mirror/vat/la.html
WTX001-B01-200 http://www.cdc.net:80/~dupre/pharmacy/pbsound.html
WTX001-B01-201 http://www.cdnemb-washdc.org:80/sanfran.html

and so on.

### Document format
---------------

The following is an example document contained within the collection.
All documents are delimited by *<DOC></DOC>* tags. The unique WT10g
document identifier is enclosed within *<DOCNO></DOCNO>* tags, and the
old VLC2 document identifier is contained on the next line between
*<DOCOLDNO></DOCOLDNO>* tags. Next comes a *<DOCHDR></DOCHDR>* section
which provides various bits of information about the document reported
by the http server which served the document to the original Internet
Archive crawler. Lastly the actual HTML source is given.

```
	<DOC>
	<DOCNO>WTX104-B01-1</DOCNO>
	<DOCOLDNO>IA097-001048-B043-338</DOCOLDNO>
	<DOCHDR>
	http://msfcinfo.msfc.nasa.gov:80/nmo/nmonasa.html 192.112.225.4 19970215104446 text/html 1014
	HTTP/1.0 200 Document follows
	Date: Sat, 15 Feb 1997 10:37:04 GMT
	Server: NCSA/1.5
	Content-type: text/html
	</DOCHDR>

	<HTML>
	<HEAD>
	<TITLE>Instructions to NASA Sponsors </TITLE> </HEAD>
	<BODY><H1><STRONG>Instructions to NASA Sponsors </STRONG></H1><P><H3>JPL is under the institutional management of 
	the Office of Space Science at NASA Headquarters.  NASA Centers or activities contemplating the placement of resea
	rch and development work at the Jet Propulsion Laboratory may contact the NASA Contracting Officer(<A href="mailto
	: vstickley@nmo.jpl.nasa.gov"> vstickley@nmo.jpl.nasa.gov)</a> at the  NMO  for more details or the Research and A
	dministration Division of the Office of Space Science, Code SP at NASA Headquarters.


	</H3><HR>[<A HREF="nmohome.html">NMO Procurement Home Page</A>]<P>Please send comments and questions to <A href="m
	ailto:kwolf@nmo.jpl.nasa.gov"> wolf@nmo.jpl.nasa.gov</a><BR>Curator and Owner:  Katherine M. Wolf<BR>Last update t
	o this page: September 15, 1995 @ 3:23 p.m. PDT


	</BODY>
	</HTML>

	</DOC>
```

### Disclaimer 
---------- 

While all reasonable attempts have been made to accurately identify
URLs and link references occurring in documents in this collection, we
make no guarantee as to the correctness or completeness of the
information contained in the files in this directory. In particular,
URL canonicalisation is a fiendishly problematic task, especially with
relative URLs and HTML tags such as base hrefs. Similarly, servers are
identified sometimes by IP addresses and sometimes by hostname. It may
be the case that some hostnames are aliases for others, and/or for IP
addresses represented within the collection. In all cases, do not rely
on the info files to be completely accurate.

If you encounter any major discrepancies within the info files, we 
would be very grateful to hear about them.


-----------------------------------
Web and Associated Research project
ACSys Cooperative Research Centre
http://pastime.anu.edu.au/WAR

2000/03/15
