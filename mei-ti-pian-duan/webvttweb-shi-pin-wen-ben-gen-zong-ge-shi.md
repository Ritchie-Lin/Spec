# WebVTT\(web视频文本跟踪格式\)

WebVTT片段是WebVTT文件的一部分，WebVTT媒体片段携带字幕。

WebVTT片段的媒体初始化部分是WebVTT的头部信息。

每个WebVTT媒体片段必须要包含EXTINF标签规定的时长内显示的字幕提示时间，每个字幕提示时间的开始时间偏移和结束时间偏移必须指示该字幕提示时间的总显示时间，即使部分提示时间范围超出了段时长。WebVTT片段可能不包含任何提示，这表示在此期间内不会显示任何字幕。

每个WebVTT区段必须以WebVTT头部信息开头或对其应用EXT-X-MAP标签。

为了在音频/视频和字幕之间同步时间戳，应该将X-TIMESTAMP-MAP元数据添加到每个WebVTT头部信息中。头部信息极爱那个WebVTT提示时间戳映射到其他媒体流中，它的格式是：  
`X-TIMESTAMP-MAP=LOCAL:<cue time>,MPEGTS:<MPEG-2 time>`  
比如：  
`X-TIMESTAMP-MAP=LOCAL:00:00:00.000,MPEGTS:900000`

LOCAL属性中的提示时间戳可能不在该段所覆盖的时间范围内。

如果WebVTT段不具有X-TIMESTAMP-MAP`标签`，则客户端必须假定WebVTT提示时间0映射到MPEG-2时间戳0。

在将WebVTT与PES时间戳同步时，客户端应考虑33位PES时间戳已包装而WebVTT提示时间未包装的情况。

