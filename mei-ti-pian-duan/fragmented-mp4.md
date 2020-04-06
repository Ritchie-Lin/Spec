# Fragmented MP4

MP4片段由ISOBMFF规定，fMP4不像常规的MP4文件那样只有一个包含sample table的MOOV box和一个包含相应sample的MDAT box，每一个fMP4片段都有一个包含sample table子集的MOOV box和一个包含相应sample的MDAT box组成。使用FMP4确实需要MOOV进行初始化，但是其MOOV仅包含非sample特定的信息，比如track或sample的说明。

分段化MPEG-4\(fMP4\)段是\[ISOBMFF\]第3节定义的“段”，包括\[ISOBMFF\]第8.16节中对MADA box的约束。

fMP4的媒体初始化部分是一个可以初始化该段解析器的ISO基本媒体文件\(ISO Base Media File\)。

广义上讲，fMP4段和媒体初始化段是\[ISOBMFF\]文件，它们也满足本节中描述的约束。

fMP4媒体片段的媒体初始化部分必须包含ftyp box，其兼容iso 6及更高版本。ftyp box后面必须紧跟着MOOV box，MOOV box必须包含描述每一个track的trak box，并具有与track匹配的track\_ID。每一个trak box应该包含一个sample表，但是它的sample数量必须为0。mvhd box和tkhd box必须是0时长的。mvex box必须紧跟在最有一个trak box后面，另外，通用媒体应用程序格式（CMAF）标头\[CMAF\]满足上述所有要求。

在一个fMP4片段中，每一个trak bx必须包含一个tfdt box，fMP4片段必须采用movie-fragment-relative 寻址，fMP4段不得使用外部数据引用，请注意，CMAF段满足上述要求。

在一个包含EXT-X-I-FRAMES-ONLY标签的播放列表中，fMP4片段可以忽略I帧之后的MDAT box。



补充ISOBMFF格式：  
在ISOBMFF格式的文件中，所有的数据都存储在称为Box的数据块结构中，每个文件由若干个Box组成，每个Box有自己的类型和长度。在一个Box中还可以包含子Box，最终由一系列的Box组成完整的文件内容，结构如下图所示，图中每个方块即代表一个Box。

![ISOBMFF&#x683C;&#x5F0F;&#x793A;&#x610F;&#x56FE;](../.gitbook/assets/image%20%282%29.png)





