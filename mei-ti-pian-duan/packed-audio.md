# Packed Audio

封包化音频包含编码的音频sample和ID3标签，这些音频sample和ID3被简单的以最小帧和无时间戳的形式被打包起来。支持封包化音频的格式有AVC with ADTS\[ISO\_13818\_7\]，MP3\[ISO\_13818\_3\]，AC-3和EAC-3.

封包化音频的媒体片段没有媒体初始化部分。

每个封包化音频媒体片段必须在段的开头用ID3专用帧\(PRIV\)标签\[ID3\]发出其第一个采样的时间戳信号，ID3 PRIV的所有者必须是"com.apple.streaming.transportStreamTimestamp"。ID3的有效负载必须是一个33位的MPEG-2节目基本流\(ES\)时间戳，该时间戳用高31位为0的大端八个字节表示。客户端不应该播放没有ID3标签的封包化音频媒体片段。







补Packed audio和Planer audio格式：  
PCM数据有Packed和Planar两种存储方式，对于双声道音频来说，Packed方式为两个声道的数据交错存储，交织在一起；Planar方式为两个声道分开存储，也就是平铺分开。假设一个L/R为一个采样点的话（一个采样点可能是8位16位32位等），可以这么表示：   
Packed: L R L R L R L R   
Planar:   L L L L R R R R   


