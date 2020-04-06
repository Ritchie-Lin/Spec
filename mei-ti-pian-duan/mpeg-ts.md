# MPEG-TS

MPEG-2 TS是由ISO\_13818规定的。

MPEG-2 TS的媒体初始化部分是节目关联表\(PAT\)，其后面跟着节目映射表\(PMT\)。

TS媒体片段必须包含一个单独的MPEG-2节目，多节目传输流没有在本文档中定义。每一个TS片段必须包含一个PAT和一个PMT，或者有一个适用于该ts片段的EXT-X-MAP标签。如果片段没有EXT-X-MAP标签，那么该TS片段的前两个包应该是一张PAT和一张PMT。









