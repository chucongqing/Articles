## WebRTC SDP 简介

### What is SDP， SDP 是什么 

SDP 的全称 是`Sessioin Description Protocol`。为会话通知、会话邀请和其它形式的多媒体会话初始化等目的提供了多媒体会话描述。  
SDP 最开始是SIP终端来交换媒体信息的协议。 后来IETF和W3C选择它用于WebRTC交换媒体信息。  
在WebRTC中对等端(Peer)使用SDP来将自己在媒体会话中使用的传输协议、端口、编码、和其他的参数通知其他终端。
用我自己理解的话来说就是，通信双方想要进行媒体通信，就需要让对方知道 1. 双方的媒体处理能力 2. 双方的网络地址等信息。  
当知道了这些信息之后，双方就可以进行协商，找到一个双方都可以处理的媒体类型，以及可以进行通信的网络。
当协商成功之后，就可以在网络上发送和接收媒体数据。

### 逐行解释WebRTC SDP
下面的例子是一个chrome生成的WebRTC SDP信息。每一行都是是一条单独的信息，接下来我们将逐行解释。

#### 全局属性行

```
o=- 4611731400430051336 2 IN IP4 127.0.0.1
s=-
t=0 0
a=group:BUNDLE 0 1
a=msid-semantic: WMS lgsCFqt9kN2fVKw5wg3NKqGdATQoltEwOdMS
```

* `o=- 4611731400430051336 2 IN IP4 127.0.0.1`  
第一个数字是会话ID，是该会话的唯一标识符。  
第二个位置的数字 `2` 是会话版本：如果在这个媒体会话中需要新的offer/answer协商(negotiation)，这个数字将增加一个。重协商通常发生在当媒体会话中的任何参数需要改变时，如on-hold、编解码器改变、添加-删除媒体轨道。
接下来的三个字段是网络类型（Internet）、IP地址类型（版本4）和创建SDP的机器的单播地址。这三个值与协商无关。  

* `s=-` 本行包含了一个文本的会话名称，通常不使用
* `t=0 0` 本行出了开始和结束的时间。当它们都被设置为0时，意味着会话将不受特定时间的限制，也就是说它是永久有效的。
* `a=group:BUNDLE 0 1` BUNDLE分组建立了SDP中包含的媒体信息之间的关系，通常是音频和视频。  在WebRTC中，它被用来在同一个RTP会话中复用几个媒体流，如草案-ietf-mmusic-sdp-bundle-negotiation所述。在本例中，浏览器提供多路复用MID 0和1，但这也必须得到对方的支持和接受。
* `a=msid-semantic: WMS lgsCFqt9kN2fVKw5wg3NKqGdATQoltEwOdMS`  
  本行为WebRTC媒体流（WMS）在PeerConnection的生命周期中提供了一个唯一的标识符。这个标识符将被用于特定媒体流（在我们的例子中为音频和视频媒体流）的每个媒体描述 m= 下的的a=msid属性。  
  这代表RTP媒体流（由每个RTP包中的SSRC字段识别）属于该媒体流，并且是该媒体流的一个轨道。  
  它将RTP媒体流与 MediaStream WebRTC 对象进行关联。关于这一点的更多信息请参考草案[draft-ietf-mmusic-msid](https://tools.ietf.org/html/draft-ietf-mmusic-msid-13)

#### Audio lines 音频属性行

##### Audio lines 音频属性

```
m=audio 58779 UDP/TLS/RTP/SAVPF 111 103 104 9 0 8 106 105 13 126
c=IN IP4 217.130.243.155
a=rtcp:51472 IN IP4 217.130.243.155
```
* `m=audio 58779 UDP/TLS/RTP/SAVPF 111 103 104 9 0 8 106 105 13 126`  
  `m` 代表它是媒体行，它浓缩了很多关于流的媒体属性的信息
	* `audio` 会话的媒体类型,（媒体类型在IANA注册）
	* `58779` 该端口将用于SRTP（如果另一个对等体支持RTCP复用，则用于RTCP） 
	* `UDP/TLS/RTP/SAVPF` 应用于会话的传输协议
	* `111 103 104 9 0 8 106 105 13 126` 浏览器支持的媒体格式描述，用于发送和接收媒体。  
  
  UDP/TLS/RTP/SAVPF 在RFC5764中定义。它需要使用SRTP和SRTCP以及RTCP反馈包。  
  最后的那些数字被称为`媒体格式描述`，与协议UDP/TLS/RTP/SAVPF一起，指明了使用不同媒体编码的RTP包的 `payload number`。 低于96的 payload number，由IANA定义并映射到对应的编码格式。在我们的SDP中，0映射到G711U，8映射到G711A。大于95的格式号是动态的，在后续的 `a=rtpmap:` 属性中将RTP payload number 映射到具体的媒体编码名称。 另外还有`a=fmtp:`属性，指定格式参数
* `c=IN IP4 217.130.243.155`  
  c 代表了连接信息，它指明了媒体发送和接收的地址。但是WebRTC强制使用ICE，所以c行中的IP并不会被使用
* `a=rtcp:51472 IN IP4 217.130.243.155`  
  这一行明确指定了用于RTCP的IP和端口，而不是从基本媒体端口派生的。请注意，由于支持RTCP复用，它和SRTP的端口相同。

##### Audio lines -> ICE Candidates

```
a=candidate:1467250027 1 udp 2122260223 192.168.0.196 46243 typ host generation 0
a=candidate:1467250027 2 udp 2122260222 192.168.0.196 56280 typ host generation 0
a=candidate:435653019 1 tcp 1845501695 192.168.0.196 0 typ host tcptype active generation 0
a=candidate:435653019 2 tcp 1845501695 192.168.0.196 0 typ host tcptype active generation 0
a=candidate:1853887674 1 udp 1518280447 47.61.61.61 36768 typ srflx raddr 192.168.0.196 rport 36768 generation 0
a=candidate:1853887674 2 udp 1518280447 47.61.61.61 36768 typ srflx raddr 192.168.0.196 rport 36768 generation 0
a=candidate:750991856 2 udp 25108222 237.30.30.30 51472 typ relay raddr 47.61.61.61 rport 54763 generation 0
a=candidate:750991856 1 udp 25108223 237.30.30.30 58779 typ relay raddr 47.61.61.61 rport 54761 generation 0
```
* ```
  a=candidate:1467250027 1 udp 2122260223 192.168.0.196 46243 typ host generation 0
  a=candidate:1467250027 2 udp 2122260222 192.168.0.196 56280 typ host generation 0
  ``` 
  ICE是WebRTC中选择用于穿越NAT的协议。详细的文档可以[参考这里](http://www.slideshare.net/saghul/ice-4414037)。ICE很复杂，无法简短的描述，我们这里简单描述下其SDP行。  
  UDP上RTP的candidate，在这个ICE行中，浏览器提供了本机的一条candidate(这个浏览器在本机上监听的IP）。浏览器可以在该IP上接收/发送SRTP和SRTCP，如果这个IP与远程Peer的某个candidate的IP可以联通，那么将选用这个candidate，例如：本机和对方计算机在同一局域网内。  
  协议（udp）后面的数字  2122260223  是候选人的优先级。注意，主机候选人的优先级比其他候选人高，因为使用主机候选人在使用资源方面更有效。
  第一行（组件=1）是RTP，
  第二行（组件=2）是RTCP。
  浏览器不知道对端是否支持 rtcp-mux，所以rtcp 的端口也发送过去了
* ```  
  a=candidate:435653019 1 tcp 1845501695 192.168.0.196 0 typ host tcptype active generation 0
  a=candidate:435653019 2 tcp 1845501695 192.168.0.196 0 typ host tcptype active generation 0
  ```
  使用TCP的本机候选，和前两行结构相同不过使用TCP通信，优先级低于UDP，因为TCP不适用于实时通信。
* ```
  a=candidate:1853887674 1 udp 1518280447 47.61.61.61 36768 typ srflx raddr 192.168.0.196 rport 36768 generation 0
  a=candidate:1853887674 2 udp 1518280447 47.61.61.61 36768 typ srflx raddr 192.168.0.196 rport 36768 generation 0
  ```
  通过STUN服务器反射的UDP候选，具体可以查看[STUN](http://webrtchacks.com/stun-helps-webrtc-traverse-nats)。
  在优先级后面包括一对公网IP端口。在 `typ srflx raddr`后面的IP端口是与将要接收流量的公网IP:端口关联的私人IP:端口（有一个NAT绑定）。
* ```
  a=candidate:750991856 2 udp 25108222 237.30.30.30 51472 typ relay raddr 47.61.61.61 rport 54763 generation 0
  a=candidate:750991856 1 udp 25108223 237.30.30.30 58779 typ relay raddr 47.61.61.61 rport 54761 generation 0
  ```
  通过TURN服务器中继的UDP候选,这些候选者是从TURN服务器获得的，必须在创建对等连接时提供。请注意，这里的优先级低于主机和反射候选者（25108222更高），所以只有在主机和反射候选者之间没有IP连接时才会使用中继。为了你的好奇心，我们在这个测试中使用了开源的coturn项目（见我们在这里的帖子）。第一对IP/端口对应的是TURN服务器为这个媒体会话分配的IP和端口，raddr和rport对应的是公共IP和公共端口，WebRTC enpoint通过这些端口到达互联网。

##### Audio lines -> ICE Parameters
  
```
a=ice-ufrag:Oyef7uvBlwafI3hT
a=ice-pwd:T0teqPLNQQOf+5W+ls+P2p16
```
在 ICE candidates 进行了交换之后， 浏览器开始使用所提供的 candidate 联系对方来进行验证。  
在这个过程中使用`ice-ufrag`和`ice-pwd`作为凭证，用来避免未授权的终端的建立媒体会话。

##### Audio lines -> DTLS Parameters

```
a=fingerprint:sha-256 49:66:12:17:0D:1C:91:AE:57:4C:C6:36:DD:D5:97:D2:7D:62:C9:9A:7F:B9:A3:F4:70:03:E7:43:91:73:23:5E
a=setup:actpass
```
* fingerprint: 这个指纹是DTLS-SRTP协商中使用的证书的哈希函数的结果（本例中使用sha-256）。  
这一行在信令和DTLS中使用的证书之间建立了一个绑定，如果指纹不匹配，那么会话应该被拒绝。
* setup: 这个参数意味着这个对等体(peer)可以是开始DTLS协商的服务器或客户端。这个参数最初是在RFC4145中定义的，已经被RFC4572更新。

##### Audio lines 音频属性

```
a=mid:0
a=extmap:1 urn:ietf:params:rtp-hdrext:ssrc-audio-level
a=extmap:3 http://www.webrtc.org/experiments/rtp-hdrext/abs-send-time
a=sendrecv
a=rtcp-mux

```
* `a=mid:0`: 这个标识符是我们在 BUNDLE 中使用的标识符。 如果包含不同的媒体，每个媒体需要有不同的标识符。
* `a=extmap:1 ...`: RFC3550定义了扩展RTP头的能力。这一行定义了将在RTP头中使用的扩展，以便接收器能够正确解码并提取元数据。在这种情况下，浏览器表示我们要在RTP头中加入RFC6464中定义的音频电平(audio level)信息。
* `a=extmap:3 ...`: 绝对发送时间扩展用于在RTP数据包上盖上一个时间戳，显示从将该数据包放在网上的系统出发的时间。更多细节请见：http://www.webrtc.org/experiments/rtp-hdrext/abs-send-time
* `a=sendrecv` : 这一行表示浏览器愿意在这个会话中同时发送和接收音频。其他值可以是sendonly、recvonly和inactive，这些值用于实现不同的场景，如将电话挂起。

##### Audio lines -> Codec Parameters 音频编码属性

```
a=rtpmap:111 opus/48000/2
a=fmtp:111 minptime=10; useinbandfec=1
a=rtpmap:103 ISAC/16000
a=rtpmap:104 ISAC/32000
a=rtpmap:9 G722/8000
a=rtpmap:0 PCMU/8000
a=rtpmap:8 PCMA/8000
a=rtpmap:106 CN/32000
a=rtpmap:105 CN/16000
a=rtpmap:13 CN/8000
a=rtpmap:126 telephone-event/8000
a=maxptime:60
```

* `a=trpmap:111 opus/4800/2`: 代表媒体格式111是 Opus，Opus是用于WebRTC的MTI音频编解码器之一。它的特点是比特率可变（6kbps-510kbps），而且不受任何版权限制，所以它可以在任何浏览器中自由实现（不像其他编解码器，如G.729）。对Opus的支持开始变得普遍。
* `a=ftmp:111 minpttime=10; useinbandfec=1`: 这一行包括Chrome浏览器对optus支持的特定有效载荷(payload-format-specific)格式参数，minipitime=10，指定打包时间的最低值（ptime：单个数据包传输的音频的毫秒数）。 useinbandfec=1，指定解码器有能力利用Opus带内FEC（前向纠错）。更多信息请查看RFC7587
* `a=rtpmap:103 ISAC/16000`: ISAC（Internet Speech Audio Codec）是一种用于高质量会议的宽带语音编解码器。16000表示ISAC将以16kbps的速度使用。因为这是第一个，所以16kbps将在下一行规定的32kbps的ISAC之前被考虑。
* `a=rtpmap:104 ISAC/32000`: 同上，32000表示ISAC将以32kbps的速率使用，但是因为本行在16kbps之后，所以优先级比16kpbs的更低。
* `a=rtpmap:9 G722/8000`: rtpmap 9 为 G722是一种宽带音频编解码器，工作速度为48、56和64 kbit/s，与G.711等窄带语音编解码器相比，由于有50-7000 Hz的更宽的语音带宽，因此可以提高语音质量。
* `a=rtpmap:0 PCMU/8000 a=rtpmap:8 PCMA/8000`:
 G711 mu和a-law，这是一个经典的电信64kbps脉冲编码调制（PCM）编解码器，使用不同的压缩法。0和8分别是PCMU和PCMA的静态有效载荷类型。从技术上讲，这些行不需要出现，因为这些信息可以通过媒体行中的编解码器列表推断出来--PCMU或PCMA(因为rtp payload type 95之前都是固定的参考 https://en.wikipedia.org/wiki/RTP_payload_formats)。
* ```
  a=rtpmap:106 CN/32000
  a=rtpmap:105 CN/16000
  a=rtpmap:13 CN/8000
  ```
  106,105 为动态RTP有效载荷类型（有效载荷类型13是静态的）表明，舒适噪声（CN）将被用于速率为48000、32000、16000和8000kb/s的编解码。
* `a=rtpmap:126 telephone-event/8000`: 这一行表示浏览器支持RFC4733，允许它在RTP中发送DTMF，而不是作为通常的数字化正弦波，而是作为一个特殊的有效载荷（在这种情况下，RTP数据包中的有效载荷为126）。这种DTMF机制确保DTMF的传输不受音频编解码器和信令协议的影响。
* `a=maxptime:60`: maxptime指定每个数据包可以封装的最大媒体量，以毫秒为单位表示。数据包的大小可能会对音频和BW的质量产生副作用。可以在SDP中修改这个值。

##### Audio lines -> SSRC Parameters
```
a=ssrc:3570614608 cname:4TOk42mSjXCkVIa6
a=ssrc:3570614608 msid:lgsCFqt9kN2fVKw5wg3NKqGdATQoltEwOdMS 35429d94-5637-4686-9ecd-7d0622261ce8
a=ssrc:3570614608 mslabel:lgsCFqt9kN2fVKw5wg3NKqGdATQoltEwOdMS
a=ssrc:3570614608 label:35429d94-5637-4686-9ecd-7d0622261ce8
```

* `a=ssrc:3570614608 cname`: cname源属性将媒体源与它的经典端点标识符联系起来，如果发现有冲突，即使ssrc标识符发生变化，它也会对RTP媒体流保持不变。这是媒体发送者将放在其RTCP SDES数据包中的值。
* `a=ssrc:3570614608 msid`: 这一行用来表示SSRC的RTP概念和WebRTC的 "媒体流 (media stream)"/"媒体流轨迹 (media stream track)"概念之间的关联，使用SDP信令[draft-ietf-mmusic-msid]。第一个参数对应于媒体流的id，第二个参数映射到媒体流轨迹的id。这些id是在WebRTC API中处理的。第一个数字是SSRC标识符，将包含在RTP数据包的SSRC字段中。
* `a=ssrc:3570614608 mslabel`: mslabel属性指的是媒体流对象的id。该参数已被废弃，由msid取代。保留mslabel是为了向后兼容。
* `a=ssrc:3570614608 label`: label属性也被msid弃用，在使用SDP的任意网络应用的背景下，它携带一个指向RTP媒体流的指针。这个标签与WebRTC API中的媒体流轨迹id相对应，它被包含在msid行中。

#### Video lines 视频属性行

```
m=video 60372 UDP/TLS/RTP/SAVPF 100 101 116 117 96
c=IN IP4 217.130.243.155
a=rtcp:64891 IN IP4 217.130.243.155
```

* `m=video 60372 UDP/TLS/RTP/SAVPF 100 101 116 117 96`: m 代表这是一个媒体行
    * `video` 代表这是个视频
    * `60372` 代表该端口将用于SRTP（如果另一个对等体支持RTCP复用，则用于RTCP）
    * `UDP/TLS/RTP/SAVPF` 这个session将要使用的传输协议
    * `100 101 116 117 96` 浏览器支持媒体格式描述，以发送和接收媒体。
* `c=IN IP4 217.130.243.155`: c 代表connection，这一行代表了使用这个IP地址来通信，但是由于ICE在WebRTC中是强制使用的，所以在WebRTC中这一行不会被使用。
* `a=rtcp:64891 IN IP4 217.130.243.155`: 如果对方不支持RTCP复用，这一行指定了用于RTCP的IP和端口。

##### Video lines -> ICE Candidates
```
a=candidate:1467250027 1 udp 2122260223 192.168.0.196 56143 typ host generation 0
a=candidate:1467250027 2 udp 2122260222 192.168.0.196 58874 typ host generation 0
a=candidate:435653019 1 tcp 1518280447 192.168.0.196 0 typ host tcptype active generation 0
a=candidate:435653019 2 tcp 1518280446 192.168.0.196 0 typ host tcptype active generation 0
a=candidate:1853887674 1 udp 1518280447 47.61.61.61 36768 typ srflx raddr 192.168.0.196 rport 36768 generation 0
a=candidate:1853887674 1 udp 1518280447 47.61.61.61 36768 typ srflx raddr 192.168.0.196 rport 36768 generation 0
a=candidate:750991856 1 udp 25108223 237.30.30.30 60372 typ relay raddr 47.61.61.61 rport 54765 generation 0
a=candidate:750991856 2 udp 25108222 237.30.30.30 64891 typ relay raddr 47.61.61.61 rport 54767 generation 0
```

Video ICE Candidates 参考Audio部分

##### Video lines -> ICE Parameters

```
a=ice-ufrag:Oyef7uvBlwafI3hT
a=ice-pwd:T0teqPLNQQOf+5W+ls+P2p16
```

Video ICE Parameters 参考Audio部分

##### Video lines ->  DTLS Parameters

```
a=fingerprint:sha-256 49:66:12:17:0D:1C:91:AE:57:4C:C6:36:DD:D5:97:D2:7D:62:C9:9A:7F:B9:A3:F4:70:03:E7:43:91:73:23:5E
a=setup:actpass
```
Video DTLS Parameters 参考 Audio 部分

##### Video lines  视频属性

```
a=mid:1
a=extmap:2 urn:ietf:params:rtp-hdrext:toffset
a=extmap:3 http://www.webrtc.org/experiments/rtp-hdrext/abs-send-time
a=extmap:4 urn:3gpp:video-orientation
a=sendrecv
a=rtcp-mux
```
* `a=mid:1`: 这是在BUNDLE行中使用的标识符。由于我们有不同的媒体，我们对每个媒体有不同的标识符。
* `a=extmap:2 ...`: Chrome提供了使用RFC 5450中定义的时间戳偏移头的扩展。
* `a=extmap:3 ...`: 绝对发送时间(absolute send time)扩展用于在RTP数据包上增加一个时间戳，显示从将该数据包放在网上的系统出发的时间。更多细节请见：http://www.webrtc.org/experiments/rtp-hdrext/abs-send-time
* `a=extmap:4 ...`: 这个extmap行（RTP头扩展在IETF RFC 5285中指定）代表Chrome支持SDP中的视频方向协调（Coordination of Video Orientation CVO），用于SDP中所有包含视频的媒体流。简而言之，该扩展允许告知对方摄像机的方向，以便正确显示。视频方向的协调包括向接收方发出信号，说明在发送方捕获的图像的当前方向，以便进行适当的渲染和显示。欲了解更多信息，请查阅3GPP文件3GPP TS 26.114。
* `a=sendrecv`: 这一行表示浏览器愿意在这个会话中同时发送和接收音频。其他值可以是sendonly、recvonly和inactive，这些值用于实现不同的场景，如将电话挂起。
* `a=rtcp-mux`: 这一行意味着该对等体(peer)支持RTCP与RTP的复用。

##### Video lines ->  Codec Parameters 视频编码

```
a=rtpmap:100 VP8/90000
a=rtcp-fb:100 ccm fir
a=rtcp-fb:100 nack
a=rtcp-fb:100 nack pli
a=rtcp-fb:100 goog-remb
a=rtpmap:101 VP9/90000
a=rtcp-fb:101 ccm fir
a=rtcp-fb:101 nack
a=rtcp-fb:101 nack pli
a=rtcp-fb:101 goog-remb
a=rtpmap:116 red/90000
a=rtpmap:117 ulpfec/90000
a=rtpmap:96 rtx/90000
a=fmtp:96 apt=100
```

* `a=rtpmap:100 VP8/90000`: 这一行说的是，VP8被分配到有效载荷类型100。这意味着在这个会话中包含VP8视频帧的RTP数据包的有效载荷类型(payload)字段的值将是100。这个RFC草案定义了VP8 PT的特殊性：http://tools.ietf.org/html/draft-ietf-payload-vp8 现在VP8是WebRTC中唯一的MPI编解码器。现在，VP8是视频的MTI编解码器，未来可能会发生变化。
* `a=rtcp-fb:100 ccm fir`: 该行要求使用FIR（全帧内请求 Full Intraframe Request），如RFC 5104中所示。它从Chrome M27开始包含。
* `a=rtcp-fb:100 nack`: 要求使用RFC 4585中指出的Negative ACKs（nack）。这可以使另一端了解到数据包的损失。
* `a=rtcp-fb:100 nack pli`: 该行说明支持PLI NACK RTCP消息。这允许在视频数据包丢失时要求另一终端提供一个新的VP8密钥帧。请参考RFC4585以了解更多信息。
* `a=rtcp-fb:100 goog-remb`: 该参数在 draft-alvestrand-rmcat-remb 中定义。它定义了接收器估计最大比特率的RTCP消息的使用。前缀goog-意味着这仍然是仅由谷歌实现的东西，而且是非标准的。
* `a=rtpmap:101 VP9/90000`: Chrome从48版开始支持VP9。你可以在Web M项目网站上了解这种视频编解码器的特点。默认情况下，它在SDP中出现在VP8之后的第二个选项。
* `a=rtpmap:116 red/90000`: 这一行要求使用RFC2198，它定义了一种有效载荷格式来编码多余的媒体数据。在WebRTC中，这被用来封装有效载荷VP8（视频有效载荷本身）和FEC（在下面的行中解释）。
* `a=rtpmap:117 ulpfec/90000`: 这条线要求使用ULP FEC（定义于RFC5109）。FEC（前向纠错）允许在数据传输中通过发送基于原始数据包的冗余信息来纠正不正确的某种错误。FEC在有数据包丢失时使用（在RTCP-RR数据包中报告）。
* `a=rtpmap:96 rtx/90000 `:参数rtx和apt是在RFC4588中定义的。这个RFC定义了一种RTP有效载荷格式(payload)，用来执行对方未收到的数据包的重传。数据包不能使用原始有效载荷(payload)进行重传，因为这将破坏RTP和RTCP机制，所以它们在重传流中以不同的有效载荷进行重传。90000指的是重传流的时钟速率，它与原始VP8流相同，与其他视频协议一样，是90000。
* `a=fmtp:96 apt=100`: 这一行说，有效载荷为96的RTP数据包将为该SDP（VP8）中被分配为有效载荷100的编解码器传输rtx信息。

##### Video lines -> SSRC Parameters

```
a=ssrc-group:FID 2231627014 632943048
a=ssrc:2231627014 cname:4TOk42mSjXCkVIa6
a=ssrc:2231627014 msid:lgsCFqt9kN2fVKw5wg3NKqGdATQoltEwOdMS daed9400-d0dd-4db3-b949-422499e96e2d
a=ssrc:2231627014 mslabel:lgsCFqt9kN2fVKw5wg3NKqGdATQoltEwOdMS
a=ssrc:2231627014 label:daed9400-d0dd-4db3-b949-422499e96e2d
a=ssrc:632943048 cname:4TOk42mSjXCkVIa6
a=ssrc:632943048 msid:lgsCFqt9kN2fVKw5wg3NKqGdATQoltEwOdMS daed9400-d0dd-4db3-b949-422499e96e2d
```

* `a=ssrc-group:FID 2231627014 632943048`: 这一行声明SSRC 632943048是2231627014的rtx修复流（RFC4588）(RFC5576）。
* `cname, msid mslabel, label`: 参考音频 ssrc 部分

### XSwitch 与 WebRTC 

  XSwitch 支持 WebRTC 通信，这就意味着可以通过在网页上呼叫和接听电话。 XSwitch 的WebRTC前端模块名为Verto，可以在包管理器中搜索下载 @xswitch/rtc 来使用。

### 总结

WebRTC 包含了音频与视频流相关的信息，掌握好了这些信息可以在日常使用中快速定位和解决问题。  
比如如果可以接通但是没有视频,那么我们可以查看视频的ICE是否协商成功，协商的地址是否可达。  
希望本文可以帮助你了解和学习WebRTC SDP。

### ref

1. [Anatomy of a WebRTC SDP](https://webrtchacks.github.io/sdp-anatomy/)
2. [Anatomy of WebRTC SDP post](https://webrtchacksstg.wpengine.com/update-anatomy-webrtc-sdp-anton-roman/)
2. [SIP SDP](https://www.tutorialspoint.com/session_initiation_protocol/session_initiation_protocol_sdp.htm)
3. [RFC 2327](https://www.ietf.org/rfc/rfc2327.txt)
4. [RFC 4566](http://tools.ietf.org/html/rfc4566)
5. [Draft SDP for WebRTC](https://datatracker.ietf.org/doc/html/draft-nandakumar-rtcweb-sdp)
