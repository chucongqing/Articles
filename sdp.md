## WebRTC SDP 绠€浠?
### What is SDP锛?SDP 鏄粈涔?

SDP 鐨勫叏绉?鏄痐Sessioin Description Protocol`銆備负浼氳瘽閫氱煡銆佷細璇濋個璇峰拰鍏跺畠褰㈠紡鐨勫濯掍綋浼氳瘽鍒濆鍖栫瓑鐩殑鎻愪緵浜嗗濯掍綋浼氳瘽鎻忚堪銆? 
SDP 鏈€寮€濮嬫槸SIP缁堢鏉ヤ氦鎹㈠獟浣撲俊鎭殑鍗忚銆?鍚庢潵IETF鍜學3C閫夋嫨瀹冪敤浜嶹ebRTC浜ゆ崲濯掍綋淇℃伅銆? 
鍦╓ebRTC涓绛夌(Peer)浣跨敤SDP鏉ュ皢鑷繁鍦ㄥ獟浣撲細璇濅腑浣跨敤鐨勪紶杈撳崗璁€佺鍙ｃ€佺紪鐮併€佸拰鍏朵粬鐨勫弬鏁伴€氱煡鍏朵粬缁堢銆?鐢ㄦ垜鑷繁鐞嗚В鐨勮瘽鏉ヨ灏辨槸锛岄€氫俊鍙屾柟鎯宠杩涜濯掍綋閫氫俊锛屽氨闇€瑕佽瀵规柟鐭ラ亾 1. 鍙屾柟鐨勫獟浣撳鐞嗚兘鍔?2. 鍙屾柟鐨勭綉缁滃湴鍧€绛変俊鎭€? 
褰撶煡閬撲簡杩欎簺淇℃伅涔嬪悗锛屽弻鏂瑰氨鍙互杩涜鍗忓晢锛屾壘鍒颁竴涓弻鏂归兘鍙互澶勭悊鐨勫獟浣撶被鍨嬶紝浠ュ強鍙互杩涜閫氫俊鐨勭綉缁溿€?褰撳崗鍟嗘垚鍔熶箣鍚庯紝灏卞彲浠ュ湪缃戠粶涓婂彂閫佸拰鎺ユ敹濯掍綋鏁版嵁銆?
### 閫愯瑙ｉ噴WebRTC SDP
涓嬮潰鐨勪緥瀛愭槸涓€涓猚hrome鐢熸垚鐨刉ebRTC SDP淇℃伅銆傛瘡涓€琛岄兘鏄槸涓€鏉″崟鐙殑淇℃伅锛屾帴涓嬫潵鎴戜滑灏嗛€愯瑙ｉ噴銆?
#### 鍏ㄥ眬灞炴€ц

```
o=- 4611731400430051336 2 IN IP4 127.0.0.1
s=-
t=0 0
a=group:BUNDLE 0 1
a=msid-semantic: WMS lgsCFqt9kN2fVKw5wg3NKqGdATQoltEwOdMS
```

* `o=- 4611731400430051336 2 IN IP4 127.0.0.1`  
绗竴涓暟瀛楁槸浼氳瘽ID锛屾槸璇ヤ細璇濈殑鍞竴鏍囪瘑绗︺€? 
绗簩涓綅缃殑鏁板瓧 `2` 鏄細璇濈増鏈細濡傛灉鍦ㄨ繖涓獟浣撲細璇濅腑闇€瑕佹柊鐨刼ffer/answer鍗忓晢(negotiation)锛岃繖涓暟瀛楀皢澧炲姞涓€涓€傞噸鍗忓晢閫氬父鍙戠敓鍦ㄥ綋濯掍綋浼氳瘽涓殑浠讳綍鍙傛暟闇€瑕佹敼鍙樻椂锛屽on-hold銆佺紪瑙ｇ爜鍣ㄦ敼鍙樸€佹坊鍔?鍒犻櫎濯掍綋杞ㄩ亾銆?鎺ヤ笅鏉ョ殑涓変釜瀛楁鏄綉缁滅被鍨嬶紙Internet锛夈€両P鍦板潃绫诲瀷锛堢増鏈?锛夊拰鍒涘缓SDP鐨勬満鍣ㄧ殑鍗曟挱鍦板潃銆傝繖涓変釜鍊间笌鍗忓晢鏃犲叧銆? 

* `s=-` 鏈鍖呭惈浜嗕竴涓枃鏈殑浼氳瘽鍚嶇О锛岄€氬父涓嶄娇鐢?* `t=0 0` 鏈鍑轰簡寮€濮嬪拰缁撴潫鐨勬椂闂淬€傚綋瀹冧滑閮借璁剧疆涓?鏃讹紝鎰忓懗鐫€浼氳瘽灏嗕笉鍙楃壒瀹氭椂闂寸殑闄愬埗锛屼篃灏辨槸璇村畠鏄案涔呮湁鏁堢殑銆?* `a=group:BUNDLE 0 1` BUNDLE鍒嗙粍寤虹珛浜哠DP涓寘鍚殑濯掍綋淇℃伅涔嬮棿鐨勫叧绯伙紝閫氬父鏄煶棰戝拰瑙嗛銆? 鍦╓ebRTC涓紝瀹冭鐢ㄦ潵鍦ㄥ悓涓€涓猂TP浼氳瘽涓鐢ㄥ嚑涓獟浣撴祦锛屽鑽夋-ietf-mmusic-sdp-bundle-negotiation鎵€杩般€傚湪鏈緥涓紝娴忚鍣ㄦ彁渚涘璺鐢∕ID 0鍜?锛屼絾杩欎篃蹇呴』寰楀埌瀵规柟鐨勬敮鎸佸拰鎺ュ彈銆?* `a=msid-semantic: WMS lgsCFqt9kN2fVKw5wg3NKqGdATQoltEwOdMS`  
  鏈涓篧ebRTC濯掍綋娴侊紙WMS锛夊湪PeerConnection鐨勭敓鍛藉懆鏈熶腑鎻愪緵浜嗕竴涓敮涓€鐨勬爣璇嗙銆傝繖涓爣璇嗙灏嗚鐢ㄤ簬鐗瑰畾濯掍綋娴侊紙鍦ㄦ垜浠殑渚嬪瓙涓负闊抽鍜岃棰戝獟浣撴祦锛夌殑姣忎釜濯掍綋鎻忚堪 m= 涓嬬殑鐨刟=msid灞炴€с€? 
  杩欎唬琛≧TP濯掍綋娴侊紙鐢辨瘡涓猂TP鍖呬腑鐨凷SRC瀛楁璇嗗埆锛夊睘浜庤濯掍綋娴侊紝骞朵笖鏄濯掍綋娴佺殑涓€涓建閬撱€? 
  瀹冨皢RTP濯掍綋娴佷笌 MediaStream WebRTC 瀵硅薄杩涜鍏宠仈銆傚叧浜庤繖涓€鐐圭殑鏇村淇℃伅璇峰弬鑰冭崏妗圼draft-ietf-mmusic-msid](https://tools.ietf.org/html/draft-ietf-mmusic-msid-13)

#### Audio lines 闊抽灞炴€ц

##### Audio lines 闊抽灞炴€?
```
m=audio 58779 UDP/TLS/RTP/SAVPF 111 103 104 9 0 8 106 105 13 126
c=IN IP4 217.130.243.155
a=rtcp:51472 IN IP4 217.130.243.155
```
* `m=audio 58779 UDP/TLS/RTP/SAVPF 111 103 104 9 0 8 106 105 13 126`  
  `m` 浠ｈ〃瀹冩槸濯掍綋琛岋紝瀹冩祿缂╀簡寰堝鍏充簬娴佺殑濯掍綋灞炴€х殑淇℃伅
	* `audio` 浼氳瘽鐨勫獟浣撶被鍨?锛堝獟浣撶被鍨嬪湪IANA娉ㄥ唽锛?	* `58779` 璇ョ鍙ｅ皢鐢ㄤ簬SRTP锛堝鏋滃彟涓€涓绛変綋鏀寔RTCP澶嶇敤锛屽垯鐢ㄤ簬RTCP锛?
	* `UDP/TLS/RTP/SAVPF` 搴旂敤浜庝細璇濈殑浼犺緭鍗忚
	* `111 103 104 9 0 8 106 105 13 126` 娴忚鍣ㄦ敮鎸佺殑濯掍綋鏍煎紡鎻忚堪锛岀敤浜庡彂閫佸拰鎺ユ敹濯掍綋銆? 
  
  UDP/TLS/RTP/SAVPF 鍦≧FC5764涓畾涔夈€傚畠闇€瑕佷娇鐢⊿RTP鍜孲RTCP浠ュ強RTCP鍙嶉鍖呫€? 
  鏈€鍚庣殑閭ｄ簺鏁板瓧琚О涓篳濯掍綋鏍煎紡鎻忚堪`锛屼笌鍗忚UDP/TLS/RTP/SAVPF涓€璧凤紝鎸囨槑浜嗕娇鐢ㄤ笉鍚屽獟浣撶紪鐮佺殑RTP鍖呯殑 `payload number`銆?浣庝簬96鐨?payload number锛岀敱IANA瀹氫箟骞舵槧灏勫埌瀵瑰簲鐨勭紪鐮佹牸寮忋€傚湪鎴戜滑鐨凷DP涓紝0鏄犲皠鍒癎711U锛?鏄犲皠鍒癎711A銆傚ぇ浜?5鐨勬牸寮忓彿鏄姩鎬佺殑锛屽湪鍚庣画鐨?`a=rtpmap:` 灞炴€т腑灏哛TP payload number 鏄犲皠鍒板叿浣撶殑濯掍綋缂栫爜鍚嶇О銆?鍙﹀杩樻湁`a=fmtp:`灞炴€э紝鎸囧畾鏍煎紡鍙傛暟
* `c=IN IP4 217.130.243.155`  
  c 浠ｈ〃浜嗚繛鎺ヤ俊鎭紝瀹冩寚鏄庝簡濯掍綋鍙戦€佸拰鎺ユ敹鐨勫湴鍧€銆備絾鏄疻ebRTC寮哄埗浣跨敤ICE锛屾墍浠琛屼腑鐨処P骞朵笉浼氳浣跨敤
* `a=rtcp:51472 IN IP4 217.130.243.155`  
  杩欎竴琛屾槑纭寚瀹氫簡鐢ㄤ簬RTCP鐨処P鍜岀鍙ｏ紝鑰屼笉鏄粠鍩烘湰濯掍綋绔彛娲剧敓鐨勩€傝娉ㄦ剰锛岀敱浜庢敮鎸丷TCP澶嶇敤锛屽畠鍜孲RTP鐨勭鍙ｇ浉鍚屻€?
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
  ICE鏄疻ebRTC涓€夋嫨鐢ㄤ簬绌胯秺NAT鐨勫崗璁€傝缁嗙殑鏂囨。鍙互[鍙傝€冭繖閲宂(http://www.slideshare.net/saghul/ice-4414037)銆侷CE寰堝鏉傦紝鏃犳硶绠€鐭殑鎻忚堪锛屾垜浠繖閲岀畝鍗曟弿杩颁笅鍏禨DP琛屻€? 
  UDP涓奟TP鐨刢andidate锛屽湪杩欎釜ICE琛屼腑锛屾祻瑙堝櫒鎻愪緵浜嗘湰鏈虹殑涓€鏉andidate(杩欎釜娴忚鍣ㄥ湪鏈満涓婄洃鍚殑IP锛夈€傛祻瑙堝櫒鍙互鍦ㄨIP涓婃帴鏀?鍙戦€丼RTP鍜孲RTCP锛屽鏋滆繖涓狪P涓庤繙绋婸eer鐨勬煇涓猚andidate鐨処P鍙互鑱旈€氾紝閭ｄ箞灏嗛€夌敤杩欎釜candidate锛屼緥濡傦細鏈満鍜屽鏂硅绠楁満鍦ㄥ悓涓€灞€鍩熺綉鍐呫€? 
  鍗忚锛坲dp锛夊悗闈㈢殑鏁板瓧  2122260223  鏄€欓€変汉鐨勪紭鍏堢骇銆傛敞鎰忥紝涓绘満鍊欓€変汉鐨勪紭鍏堢骇姣斿叾浠栧€欓€変汉楂橈紝鍥犱负浣跨敤涓绘満鍊欓€変汉鍦ㄤ娇鐢ㄨ祫婧愭柟闈㈡洿鏈夋晥銆?  绗竴琛岋紙缁勪欢=1锛夋槸RTP锛?  绗簩琛岋紙缁勪欢=2锛夋槸RTCP銆?  娴忚鍣ㄤ笉鐭ラ亾瀵圭鏄惁鏀寔 rtcp-mux锛屾墍浠tcp 鐨勭鍙ｄ篃鍙戦€佽繃鍘讳簡
* ```  
  a=candidate:435653019 1 tcp 1845501695 192.168.0.196 0 typ host tcptype active generation 0
  a=candidate:435653019 2 tcp 1845501695 192.168.0.196 0 typ host tcptype active generation 0
  ```
  浣跨敤TCP鐨勬湰鏈哄€欓€夛紝鍜屽墠涓よ缁撴瀯鐩稿悓涓嶈繃浣跨敤TCP閫氫俊锛屼紭鍏堢骇浣庝簬UDP锛屽洜涓篢CP涓嶉€傜敤浜庡疄鏃堕€氫俊銆?* ```
  a=candidate:1853887674 1 udp 1518280447 47.61.61.61 36768 typ srflx raddr 192.168.0.196 rport 36768 generation 0
  a=candidate:1853887674 2 udp 1518280447 47.61.61.61 36768 typ srflx raddr 192.168.0.196 rport 36768 generation 0
  ```
  閫氳繃STUN鏈嶅姟鍣ㄥ弽灏勭殑UDP鍊欓€夛紝鍏蜂綋鍙互鏌ョ湅[STUN](http://webrtchacks.com/stun-helps-webrtc-traverse-nats)銆?  鍦ㄤ紭鍏堢骇鍚庨潰鍖呮嫭涓€瀵瑰叕缃慖P绔彛銆傚湪 `typ srflx raddr`鍚庨潰鐨処P绔彛鏄笌灏嗚鎺ユ敹娴侀噺鐨勫叕缃慖P:绔彛鍏宠仈鐨勭浜篒P:绔彛锛堟湁涓€涓狽AT缁戝畾锛夈€?* ```
  a=candidate:750991856 2 udp 25108222 237.30.30.30 51472 typ relay raddr 47.61.61.61 rport 54763 generation 0
  a=candidate:750991856 1 udp 25108223 237.30.30.30 58779 typ relay raddr 47.61.61.61 rport 54761 generation 0
  ```
  閫氳繃TURN鏈嶅姟鍣ㄤ腑缁х殑UDP鍊欓€?杩欎簺鍊欓€夎€呮槸浠嶵URN鏈嶅姟鍣ㄨ幏寰楃殑锛屽繀椤诲湪鍒涘缓瀵圭瓑杩炴帴鏃舵彁渚涖€傝娉ㄦ剰锛岃繖閲岀殑浼樺厛绾т綆浜庝富鏈哄拰鍙嶅皠鍊欓€夎€咃紙25108222鏇撮珮锛夛紝鎵€浠ュ彧鏈夊湪涓绘満鍜屽弽灏勫€欓€夎€呬箣闂存病鏈塈P杩炴帴鏃舵墠浼氫娇鐢ㄤ腑缁с€備负浜嗕綘鐨勫ソ濂囧績锛屾垜浠湪杩欎釜娴嬭瘯涓娇鐢ㄤ簡寮€婧愮殑coturn椤圭洰锛堣鎴戜滑鍦ㄨ繖閲岀殑甯栧瓙锛夈€傜涓€瀵笽P/绔彛瀵瑰簲鐨勬槸TURN鏈嶅姟鍣ㄤ负杩欎釜濯掍綋浼氳瘽鍒嗛厤鐨処P鍜岀鍙ｏ紝raddr鍜宺port瀵瑰簲鐨勬槸鍏叡IP鍜屽叕鍏辩鍙ｏ紝WebRTC enpoint閫氳繃杩欎簺绔彛鍒拌揪浜掕仈缃戙€?
##### Audio lines -> ICE Parameters
  
```
a=ice-ufrag:Oyef7uvBlwafI3hT
a=ice-pwd:T0teqPLNQQOf+5W+ls+P2p16
```
鍦?ICE candidates 杩涜浜嗕氦鎹箣鍚庯紝 娴忚鍣ㄥ紑濮嬩娇鐢ㄦ墍鎻愪緵鐨?candidate 鑱旂郴瀵规柟鏉ヨ繘琛岄獙璇併€? 
鍦ㄨ繖涓繃绋嬩腑浣跨敤`ice-ufrag`鍜宍ice-pwd`浣滀负鍑瘉锛岀敤鏉ラ伩鍏嶆湭鎺堟潈鐨勭粓绔殑寤虹珛濯掍綋浼氳瘽銆?
##### Audio lines -> DTLS Parameters

```
a=fingerprint:sha-256 49:66:12:17:0D:1C:91:AE:57:4C:C6:36:DD:D5:97:D2:7D:62:C9:9A:7F:B9:A3:F4:70:03:E7:43:91:73:23:5E
a=setup:actpass
```
* fingerprint: 杩欎釜鎸囩汗鏄疍TLS-SRTP鍗忓晢涓娇鐢ㄧ殑璇佷功鐨勫搱甯屽嚱鏁扮殑缁撴灉锛堟湰渚嬩腑浣跨敤sha-256锛夈€? 
杩欎竴琛屽湪淇′护鍜孌TLS涓娇鐢ㄧ殑璇佷功涔嬮棿寤虹珛浜嗕竴涓粦瀹氾紝濡傛灉鎸囩汗涓嶅尮閰嶏紝閭ｄ箞浼氳瘽搴旇琚嫆缁濄€?* setup: 杩欎釜鍙傛暟鎰忓懗鐫€杩欎釜瀵圭瓑浣?peer)鍙互鏄紑濮婦TLS鍗忓晢鐨勬湇鍔″櫒鎴栧鎴风銆傝繖涓弬鏁版渶鍒濇槸鍦≧FC4145涓畾涔夌殑锛屽凡缁忚RFC4572鏇存柊銆?
##### Audio lines 闊抽灞炴€?
```
a=mid:0
a=extmap:1 urn:ietf:params:rtp-hdrext:ssrc-audio-level
a=extmap:3 http://www.webrtc.org/experiments/rtp-hdrext/abs-send-time
a=sendrecv
a=rtcp-mux

```
* `a=mid:0`: 杩欎釜鏍囪瘑绗︽槸鎴戜滑鍦?BUNDLE 涓娇鐢ㄧ殑鏍囪瘑绗︺€?濡傛灉鍖呭惈涓嶅悓鐨勫獟浣擄紝姣忎釜濯掍綋闇€瑕佹湁涓嶅悓鐨勬爣璇嗙銆?* `a=extmap:1 ...`: RFC3550瀹氫箟浜嗘墿灞昍TP澶寸殑鑳藉姏銆傝繖涓€琛屽畾涔変簡灏嗗湪RTP澶翠腑浣跨敤鐨勬墿灞曪紝浠ヤ究鎺ユ敹鍣ㄨ兘澶熸纭В鐮佸苟鎻愬彇鍏冩暟鎹€傚湪杩欑鎯呭喌涓嬶紝娴忚鍣ㄨ〃绀烘垜浠鍦≧TP澶翠腑鍔犲叆RFC6464涓畾涔夌殑闊抽鐢靛钩(audio level)淇℃伅銆?* `a=extmap:3 ...`: 缁濆鍙戦€佹椂闂存墿灞曠敤浜庡湪RTP鏁版嵁鍖呬笂鐩栦笂涓€涓椂闂存埑锛屾樉绀轰粠灏嗚鏁版嵁鍖呮斁鍦ㄧ綉涓婄殑绯荤粺鍑哄彂鐨勬椂闂淬€傛洿澶氱粏鑺傝瑙侊細http://www.webrtc.org/experiments/rtp-hdrext/abs-send-time
* `a=sendrecv` : 杩欎竴琛岃〃绀烘祻瑙堝櫒鎰挎剰鍦ㄨ繖涓細璇濅腑鍚屾椂鍙戦€佸拰鎺ユ敹闊抽銆傚叾浠栧€煎彲浠ユ槸sendonly銆乺ecvonly鍜宨nactive锛岃繖浜涘€肩敤浜庡疄鐜颁笉鍚岀殑鍦烘櫙锛屽灏嗙數璇濇寕璧枫€?
##### Audio lines -> Codec Parameters 闊抽缂栫爜灞炴€?
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

* `a=trpmap:111 opus/4800/2`: 浠ｈ〃濯掍綋鏍煎紡111鏄?Opus锛孫pus鏄敤浜嶹ebRTC鐨凪TI闊抽缂栬В鐮佸櫒涔嬩竴銆傚畠鐨勭壒鐐规槸姣旂壒鐜囧彲鍙橈紙6kbps-510kbps锛夛紝鑰屼笖涓嶅彈浠讳綍鐗堟潈闄愬埗锛屾墍浠ュ畠鍙互鍦ㄤ换浣曟祻瑙堝櫒涓嚜鐢卞疄鐜帮紙涓嶅儚鍏朵粬缂栬В鐮佸櫒锛屽G.729锛夈€傚Opus鐨勬敮鎸佸紑濮嬪彉寰楁櫘閬嶃€?* `a=ftmp:111 minpttime=10; useinbandfec=1`: 杩欎竴琛屽寘鎷珻hrome娴忚鍣ㄥoptus鏀寔鐨勭壒瀹氭湁鏁堣浇鑽?payload-format-specific)鏍煎紡鍙傛暟锛宮inipitime=10锛屾寚瀹氭墦鍖呮椂闂寸殑鏈€浣庡€硷紙ptime锛氬崟涓暟鎹寘浼犺緭鐨勯煶棰戠殑姣鏁帮級銆?useinbandfec=1锛屾寚瀹氳В鐮佸櫒鏈夎兘鍔涘埄鐢∣pus甯﹀唴FEC锛堝墠鍚戠籂閿欙級銆傛洿澶氫俊鎭鏌ョ湅RFC7587
* `a=rtpmap:103 ISAC/16000`: ISAC锛圛nternet Speech Audio Codec锛夋槸涓€绉嶇敤浜庨珮璐ㄩ噺浼氳鐨勫甯﹁闊崇紪瑙ｇ爜鍣ㄣ€?6000琛ㄧずISAC灏嗕互16kbps鐨勯€熷害浣跨敤銆傚洜涓鸿繖鏄涓€涓紝鎵€浠?6kbps灏嗗湪涓嬩竴琛岃瀹氱殑32kbps鐨処SAC涔嬪墠琚€冭檻銆?* `a=rtpmap:104 ISAC/32000`: 鍚屼笂锛?2000琛ㄧずISAC灏嗕互32kbps鐨勯€熺巼浣跨敤锛屼絾鏄洜涓烘湰琛屽湪16kbps涔嬪悗锛屾墍浠ヤ紭鍏堢骇姣?6kpbs鐨勬洿浣庛€?* `a=rtpmap:9 G722/8000`: rtpmap 9 涓?G722鏄竴绉嶅甯﹂煶棰戠紪瑙ｇ爜鍣紝宸ヤ綔閫熷害涓?8銆?6鍜?4 kbit/s锛屼笌G.711绛夌獎甯﹁闊崇紪瑙ｇ爜鍣ㄧ浉姣旓紝鐢变簬鏈?0-7000 Hz鐨勬洿瀹界殑璇煶甯﹀锛屽洜姝ゅ彲浠ユ彁楂樿闊宠川閲忋€?* `a=rtpmap:0 PCMU/8000 a=rtpmap:8 PCMA/8000`:
 G711 mu鍜宎-law锛岃繖鏄竴涓粡鍏哥殑鐢典俊64kbps鑴夊啿缂栫爜璋冨埗锛圥CM锛夌紪瑙ｇ爜鍣紝浣跨敤涓嶅悓鐨勫帇缂╂硶銆?鍜?鍒嗗埆鏄疨CMU鍜孭CMA鐨勯潤鎬佹湁鏁堣浇鑽风被鍨嬨€備粠鎶€鏈笂璁诧紝杩欎簺琛屼笉闇€瑕佸嚭鐜帮紝鍥犱负杩欎簺淇℃伅鍙互閫氳繃濯掍綋琛屼腑鐨勭紪瑙ｇ爜鍣ㄥ垪琛ㄦ帹鏂嚭鏉?-PCMU鎴朠CMA(鍥犱负rtp payload type 95涔嬪墠閮芥槸鍥哄畾鐨勫弬鑰?https://en.wikipedia.org/wiki/RTP_payload_formats)銆?* ```
  a=rtpmap:106 CN/32000
  a=rtpmap:105 CN/16000
  a=rtpmap:13 CN/8000
  ```
  106,105 涓哄姩鎬丷TP鏈夋晥杞借嵎绫诲瀷锛堟湁鏁堣浇鑽风被鍨?3鏄潤鎬佺殑锛夎〃鏄庯紝鑸掗€傚櫔澹帮紙CN锛夊皢琚敤浜庨€熺巼涓?8000銆?2000銆?6000鍜?000kb/s鐨勭紪瑙ｇ爜銆?* `a=rtpmap:126 telephone-event/8000`: 杩欎竴琛岃〃绀烘祻瑙堝櫒鏀寔RFC4733锛屽厑璁稿畠鍦≧TP涓彂閫丏TMF锛岃€屼笉鏄綔涓洪€氬父鐨勬暟瀛楀寲姝ｅ鸡娉紝鑰屾槸浣滀负涓€涓壒娈婄殑鏈夋晥杞借嵎锛堝湪杩欑鎯呭喌涓嬶紝RTP鏁版嵁鍖呬腑鐨勬湁鏁堣浇鑽蜂负126锛夈€傝繖绉岲TMF鏈哄埗纭繚DTMF鐨勪紶杈撲笉鍙楅煶棰戠紪瑙ｇ爜鍣ㄥ拰淇′护鍗忚鐨勫奖鍝嶃€?* `a=maxptime:60`: maxptime鎸囧畾姣忎釜鏁版嵁鍖呭彲浠ュ皝瑁呯殑鏈€澶у獟浣撻噺锛屼互姣涓哄崟浣嶈〃绀恒€傛暟鎹寘鐨勫ぇ灏忓彲鑳戒細瀵归煶棰戝拰BW鐨勮川閲忎骇鐢熷壇浣滅敤銆傚彲浠ュ湪SDP涓慨鏀硅繖涓€笺€?
##### Audio lines -> SSRC Parameters
```
a=ssrc:3570614608 cname:4TOk42mSjXCkVIa6
a=ssrc:3570614608 msid:lgsCFqt9kN2fVKw5wg3NKqGdATQoltEwOdMS 35429d94-5637-4686-9ecd-7d0622261ce8
a=ssrc:3570614608 mslabel:lgsCFqt9kN2fVKw5wg3NKqGdATQoltEwOdMS
a=ssrc:3570614608 label:35429d94-5637-4686-9ecd-7d0622261ce8
```

* `a=ssrc:3570614608 cname`: cname婧愬睘鎬у皢濯掍綋婧愪笌瀹冪殑缁忓吀绔偣鏍囪瘑绗﹁仈绯昏捣鏉ワ紝濡傛灉鍙戠幇鏈夊啿绐侊紝鍗充娇ssrc鏍囪瘑绗﹀彂鐢熷彉鍖栵紝瀹冧篃浼氬RTP濯掍綋娴佷繚鎸佷笉鍙樸€傝繖鏄獟浣撳彂閫佽€呭皢鏀惧湪鍏禦TCP SDES鏁版嵁鍖呬腑鐨勫€笺€?* `a=ssrc:3570614608 msid`: 杩欎竴琛岀敤鏉ヨ〃绀篠SRC鐨凴TP姒傚康鍜學ebRTC鐨?"濯掍綋娴?(media stream)"/"濯掍綋娴佽建杩?(media stream track)"姒傚康涔嬮棿鐨勫叧鑱旓紝浣跨敤SDP淇′护[draft-ietf-mmusic-msid]銆傜涓€涓弬鏁板搴斾簬濯掍綋娴佺殑id锛岀浜屼釜鍙傛暟鏄犲皠鍒板獟浣撴祦杞ㄨ抗鐨刬d銆傝繖浜沬d鏄湪WebRTC API涓鐞嗙殑銆傜涓€涓暟瀛楁槸SSRC鏍囪瘑绗︼紝灏嗗寘鍚湪RTP鏁版嵁鍖呯殑SSRC瀛楁涓€?* `a=ssrc:3570614608 mslabel`: mslabel灞炴€ф寚鐨勬槸濯掍綋娴佸璞＄殑id銆傝鍙傛暟宸茶搴熷純锛岀敱msid鍙栦唬銆備繚鐣檓slabel鏄负浜嗗悜鍚庡吋瀹广€?* `a=ssrc:3570614608 label`: label灞炴€т篃琚玬sid寮冪敤锛屽湪浣跨敤SDP鐨勪换鎰忕綉缁滃簲鐢ㄧ殑鑳屾櫙涓嬶紝瀹冩惡甯︿竴涓寚鍚慠TP濯掍綋娴佺殑鎸囬拡銆傝繖涓爣绛句笌WebRTC API涓殑濯掍綋娴佽建杩筰d鐩稿搴旓紝瀹冭鍖呭惈鍦╩sid琛屼腑銆?
#### Video lines 瑙嗛灞炴€ц

```
m=video 60372 UDP/TLS/RTP/SAVPF 100 101 116 117 96
c=IN IP4 217.130.243.155
a=rtcp:64891 IN IP4 217.130.243.155
```

* `m=video 60372 UDP/TLS/RTP/SAVPF 100 101 116 117 96`: m 浠ｈ〃杩欐槸涓€涓獟浣撹
    * `video` 浠ｈ〃杩欐槸涓棰?    * `60372` 浠ｈ〃璇ョ鍙ｅ皢鐢ㄤ簬SRTP锛堝鏋滃彟涓€涓绛変綋鏀寔RTCP澶嶇敤锛屽垯鐢ㄤ簬RTCP锛?    * `UDP/TLS/RTP/SAVPF` 杩欎釜session灏嗚浣跨敤鐨勪紶杈撳崗璁?    * `100 101 116 117 96` 娴忚鍣ㄦ敮鎸佸獟浣撴牸寮忔弿杩帮紝浠ュ彂閫佸拰鎺ユ敹濯掍綋銆?* `c=IN IP4 217.130.243.155`: c 浠ｈ〃connection锛岃繖涓€琛屼唬琛ㄤ簡浣跨敤杩欎釜IP鍦板潃鏉ラ€氫俊锛屼絾鏄敱浜嶪CE鍦╓ebRTC涓槸寮哄埗浣跨敤鐨勶紝鎵€浠ュ湪WebRTC涓繖涓€琛屼笉浼氳浣跨敤銆?* `a=rtcp:64891 IN IP4 217.130.243.155`: 濡傛灉瀵规柟涓嶆敮鎸丷TCP澶嶇敤锛岃繖涓€琛屾寚瀹氫簡鐢ㄤ簬RTCP鐨処P鍜岀鍙ｃ€?
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

Video ICE Candidates 鍙傝€傾udio閮ㄥ垎

##### Video lines -> ICE Parameters

```
a=ice-ufrag:Oyef7uvBlwafI3hT
a=ice-pwd:T0teqPLNQQOf+5W+ls+P2p16
```

Video ICE Parameters 鍙傝€傾udio閮ㄥ垎

##### Video lines ->  DTLS Parameters

```
a=fingerprint:sha-256 49:66:12:17:0D:1C:91:AE:57:4C:C6:36:DD:D5:97:D2:7D:62:C9:9A:7F:B9:A3:F4:70:03:E7:43:91:73:23:5E
a=setup:actpass
```
Video DTLS Parameters 鍙傝€?Audio 閮ㄥ垎

##### Video lines  瑙嗛灞炴€?
```
a=mid:1
a=extmap:2 urn:ietf:params:rtp-hdrext:toffset
a=extmap:3 http://www.webrtc.org/experiments/rtp-hdrext/abs-send-time
a=extmap:4 urn:3gpp:video-orientation
a=sendrecv
a=rtcp-mux
```
* `a=mid:1`: 杩欐槸鍦˙UNDLE琛屼腑浣跨敤鐨勬爣璇嗙銆傜敱浜庢垜浠湁涓嶅悓鐨勫獟浣擄紝鎴戜滑瀵规瘡涓獟浣撴湁涓嶅悓鐨勬爣璇嗙銆?* `a=extmap:2 ...`: Chrome鎻愪緵浜嗕娇鐢≧FC 5450涓畾涔夌殑鏃堕棿鎴冲亸绉诲ご鐨勬墿灞曘€?* `a=extmap:3 ...`: 缁濆鍙戦€佹椂闂?absolute send time)鎵╁睍鐢ㄤ簬鍦≧TP鏁版嵁鍖呬笂澧炲姞涓€涓椂闂存埑锛屾樉绀轰粠灏嗚鏁版嵁鍖呮斁鍦ㄧ綉涓婄殑绯荤粺鍑哄彂鐨勬椂闂淬€傛洿澶氱粏鑺傝瑙侊細http://www.webrtc.org/experiments/rtp-hdrext/abs-send-time
* `a=extmap:4 ...`: 杩欎釜extmap琛岋紙RTP澶存墿灞曞湪IETF RFC 5285涓寚瀹氾級浠ｈ〃Chrome鏀寔SDP涓殑瑙嗛鏂瑰悜鍗忚皟锛圕oordination of Video Orientation CVO锛夛紝鐢ㄤ簬SDP涓墍鏈夊寘鍚棰戠殑濯掍綋娴併€傜畝鑰岃█涔嬶紝璇ユ墿灞曞厑璁稿憡鐭ュ鏂规憚鍍忔満鐨勬柟鍚戯紝浠ヤ究姝ｇ‘鏄剧ず銆傝棰戞柟鍚戠殑鍗忚皟鍖呮嫭鍚戞帴鏀舵柟鍙戝嚭淇″彿锛岃鏄庡湪鍙戦€佹柟鎹曡幏鐨勫浘鍍忕殑褰撳墠鏂瑰悜锛屼互渚胯繘琛岄€傚綋鐨勬覆鏌撳拰鏄剧ず銆傛浜嗚В鏇村淇℃伅锛岃鏌ラ槄3GPP鏂囦欢3GPP TS 26.114銆?* `a=sendrecv`: 杩欎竴琛岃〃绀烘祻瑙堝櫒鎰挎剰鍦ㄨ繖涓細璇濅腑鍚屾椂鍙戦€佸拰鎺ユ敹闊抽銆傚叾浠栧€煎彲浠ユ槸sendonly銆乺ecvonly鍜宨nactive锛岃繖浜涘€肩敤浜庡疄鐜颁笉鍚岀殑鍦烘櫙锛屽灏嗙數璇濇寕璧枫€?* `a=rtcp-mux`: 杩欎竴琛屾剰鍛崇潃璇ュ绛変綋(peer)鏀寔RTCP涓嶳TP鐨勫鐢ㄣ€?
##### Video lines ->  Codec Parameters 瑙嗛缂栫爜

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

* `a=rtpmap:100 VP8/90000`: 杩欎竴琛岃鐨勬槸锛孷P8琚垎閰嶅埌鏈夋晥杞借嵎绫诲瀷100銆傝繖鎰忓懗鐫€鍦ㄨ繖涓細璇濅腑鍖呭惈VP8瑙嗛甯х殑RTP鏁版嵁鍖呯殑鏈夋晥杞借嵎绫诲瀷(payload)瀛楁鐨勫€煎皢鏄?00銆傝繖涓猂FC鑽夋瀹氫箟浜哣P8 PT鐨勭壒娈婃€э細http://tools.ietf.org/html/draft-ietf-payload-vp8 鐜板湪VP8鏄疻ebRTC涓敮涓€鐨凪PI缂栬В鐮佸櫒銆傜幇鍦紝VP8鏄棰戠殑MTI缂栬В鐮佸櫒锛屾湭鏉ュ彲鑳戒細鍙戠敓鍙樺寲銆?* `a=rtcp-fb:100 ccm fir`: 璇ヨ瑕佹眰浣跨敤FIR锛堝叏甯у唴璇锋眰 Full Intraframe Request锛夛紝濡俁FC 5104涓墍绀恒€傚畠浠嶤hrome M27寮€濮嬪寘鍚€?* `a=rtcp-fb:100 nack`: 瑕佹眰浣跨敤RFC 4585涓寚鍑虹殑Negative ACKs锛坣ack锛夈€傝繖鍙互浣垮彟涓€绔簡瑙ｅ埌鏁版嵁鍖呯殑鎹熷け銆?* `a=rtcp-fb:100 nack pli`: 璇ヨ璇存槑鏀寔PLI NACK RTCP娑堟伅銆傝繖鍏佽鍦ㄨ棰戞暟鎹寘涓㈠け鏃惰姹傚彟涓€缁堢鎻愪緵涓€涓柊鐨刅P8瀵嗛挜甯с€傝鍙傝€僐FC4585浠ヤ簡瑙ｆ洿澶氫俊鎭€?* `a=rtcp-fb:100 goog-remb`: 璇ュ弬鏁板湪 draft-alvestrand-rmcat-remb 涓畾涔夈€傚畠瀹氫箟浜嗘帴鏀跺櫒浼拌鏈€澶ф瘮鐗圭巼鐨凴TCP娑堟伅鐨勪娇鐢ㄣ€傚墠缂€goog-鎰忓懗鐫€杩欎粛鐒舵槸浠呯敱璋锋瓕瀹炵幇鐨勪笢瑗匡紝鑰屼笖鏄潪鏍囧噯鐨勩€?* `a=rtpmap:101 VP9/90000`: Chrome浠?8鐗堝紑濮嬫敮鎸乂P9銆備綘鍙互鍦╓eb M椤圭洰缃戠珯涓婁簡瑙ｈ繖绉嶈棰戠紪瑙ｇ爜鍣ㄧ殑鐗圭偣銆傞粯璁ゆ儏鍐典笅锛屽畠鍦⊿DP涓嚭鐜板湪VP8涔嬪悗鐨勭浜屼釜閫夐」銆?* `a=rtpmap:116 red/90000`: 杩欎竴琛岃姹備娇鐢≧FC2198锛屽畠瀹氫箟浜嗕竴绉嶆湁鏁堣浇鑽锋牸寮忔潵缂栫爜澶氫綑鐨勫獟浣撴暟鎹€傚湪WebRTC涓紝杩欒鐢ㄦ潵灏佽鏈夋晥杞借嵎VP8锛堣棰戞湁鏁堣浇鑽锋湰韬級鍜孎EC锛堝湪涓嬮潰鐨勮涓В閲婏級銆?* `a=rtpmap:117 ulpfec/90000`: 杩欐潯绾胯姹備娇鐢║LP FEC锛堝畾涔変簬RFC5109锛夈€侳EC锛堝墠鍚戠籂閿欙級鍏佽鍦ㄦ暟鎹紶杈撲腑閫氳繃鍙戦€佸熀浜庡師濮嬫暟鎹寘鐨勫啑浣欎俊鎭潵绾犳涓嶆纭殑鏌愮閿欒銆侳EC鍦ㄦ湁鏁版嵁鍖呬涪澶辨椂浣跨敤锛堝湪RTCP-RR鏁版嵁鍖呬腑鎶ュ憡锛夈€?* `a=rtpmap:96 rtx/90000 `:鍙傛暟rtx鍜宎pt鏄湪RFC4588涓畾涔夌殑銆傝繖涓猂FC瀹氫箟浜嗕竴绉峈TP鏈夋晥杞借嵎鏍煎紡(payload)锛岀敤鏉ユ墽琛屽鏂规湭鏀跺埌鐨勬暟鎹寘鐨勯噸浼犮€傛暟鎹寘涓嶈兘浣跨敤鍘熷鏈夋晥杞借嵎(payload)杩涜閲嶄紶锛屽洜涓鸿繖灏嗙牬鍧廟TP鍜孯TCP鏈哄埗锛屾墍浠ュ畠浠湪閲嶄紶娴佷腑浠ヤ笉鍚岀殑鏈夋晥杞借嵎杩涜閲嶄紶銆?0000鎸囩殑鏄噸浼犳祦鐨勬椂閽熼€熺巼锛屽畠涓庡師濮媀P8娴佺浉鍚岋紝涓庡叾浠栬棰戝崗璁竴鏍凤紝鏄?0000銆?* `a=fmtp:96 apt=100`: 杩欎竴琛岃锛屾湁鏁堣浇鑽蜂负96鐨凴TP鏁版嵁鍖呭皢涓鸿SDP锛圴P8锛変腑琚垎閰嶄负鏈夋晥杞借嵎100鐨勭紪瑙ｇ爜鍣ㄤ紶杈搑tx淇℃伅銆?
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

* `a=ssrc-group:FID 2231627014 632943048`: 杩欎竴琛屽０鏄嶴SRC 632943048鏄?231627014鐨剅tx淇娴侊紙RFC4588锛?RFC5576锛夈€?* `cname, msid mslabel, label`: 鍙傝€冮煶棰?ssrc 閮ㄥ垎

### XSwitch 涓?WebRTC 

  XSwitch 鏀寔 WebRTC 閫氫俊锛岃繖灏辨剰鍛崇潃鍙互閫氳繃鍦ㄧ綉椤典笂鍛煎彨鍜屾帴鍚數璇濄€?XSwitch 鐨刉ebRTC鍓嶇妯″潡鍚嶄负Verto锛屽彲浠ュ湪鍖呯鐞嗗櫒涓悳绱笅杞?@xswitch/rtc 鏉ヤ娇鐢ㄣ€?
### 鎬荤粨

WebRTC 鍖呭惈浜嗛煶棰戜笌瑙嗛娴佺浉鍏崇殑淇℃伅锛屾帉鎻″ソ浜嗚繖浜涗俊鎭彲浠ュ湪鏃ュ父浣跨敤涓揩閫熷畾浣嶅拰瑙ｅ喅闂銆? 
姣斿濡傛灉鍙互鎺ラ€氫絾鏄病鏈夎棰?閭ｄ箞鎴戜滑鍙互鏌ョ湅瑙嗛鐨処CE鏄惁鍗忓晢鎴愬姛锛屽崗鍟嗙殑鍦板潃鏄惁鍙揪銆? 
甯屾湜鏈枃鍙互甯姪浣犱簡瑙ｅ拰瀛︿範WebRTC SDP銆?
### ref

1. [Anatomy of a WebRTC SDP](https://webrtchacks.github.io/sdp-anatomy/)
2. [Anatomy of WebRTC SDP post](https://webrtchacksstg.wpengine.com/update-anatomy-webrtc-sdp-anton-roman/)
2. [SIP SDP](https://www.tutorialspoint.com/session_initiation_protocol/session_initiation_protocol_sdp.htm)
3. [RFC 2327](https://www.ietf.org/rfc/rfc2327.txt)
4. [RFC 4566](http://tools.ietf.org/html/rfc4566)
5. [Draft SDP for WebRTC](https://datatracker.ietf.org/doc/html/draft-nandakumar-rtcweb-sdp)
