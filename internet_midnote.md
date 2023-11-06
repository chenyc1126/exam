# 企網期中筆記
網路好無聊 zzz
## 第一章/第二章 
### **雲端服務的三大模式**
1.SaaS:Software as a service，服務供應商提供完整的產品，software指的是最終使用者應用程式，如電子郵件、google docs等，使用者只須要考慮如何使用即可

2.PaaS:Platform as a service，服務供應商提供平台，使用者只需專注在規劃應用程式和資料，剩下由服務供應商管理

3.IaaS:Infrastructure as a service，服務供應商提供伺服器、網路、硬碟等基礎處設施，作業系統、應用程式、資料等由使用者管理

-----
### <font color="#f00">(103)</font>Network Message分為Header、Data Field、Trailer，分別說明。
消息頭（Header）：有助於網絡設備確定消息的去向，並確保消息在傳輸過程中被正確處理。

數據字段（Data Field）：數據字段包含實際的信息或數據，這是消息的主要內容。根據消息的類型和目的，它可以有不同的格式和結構。

尾部（Trailer）：尾部通常包含錯誤檢查和校驗信息，以確保消息在傳輸過程中未被損壞或竄改。
![image.png](https://hackmd.io/_uploads/rkVc9wfXT.png)

**但不是每個message都須遵守這種結構，視協議內容而定！！！！**

### 第一類與第二類電信業者的差異比較
第一類：指有架設實體線路固網或實體無線基地台用以經營電話或網際網路業務的業者。通常較大家，如中華電信、台哥大等

第二類：沒有架設實體線路固網或實體無線基地台，而是以向第一類電信業者承租固網或無線基地台一定數量的門號或頻寬來經營自己的電話或網際網路業務的業者。如家樂福電信

------
:::info
**OSI vs ISO**

ISO（International Organization for Standardization）：ISO是一個國際標準制定組織

OSI（Open Systems Interconnection）：OSI是網路的七層架構
:::

### [OSI七層架構 和 TCP/IP通訊協定 的比較](https://hackmd.io/@Pang-Chang/BkQK8_tjF#%E7%9B%AE%E9%8C%84)

<font color="#f00">(103)</font>現今的網絡架構通常被視為混合的 TCP/IP-OSI 架構，主要原因是為了更好地滿足不同網絡和應用程序的需求，以確保通信的互操作性和效能。

#### 開放式系統互聯模型（Open System Interconnection Model）， 簡稱為OSI模型
1. 由國際標準化組織 ISO 所提出的概念模型
2. 整體資料流程分為 7 個分層
3. 越高層越偏向軟體，低層則偏向硬體
4. 每個中間層為其上一層提供功能，自身功能則由其下一層提供

### 各分層的定義
#### 1. 實體層(Physical Layer):
> 負責處理原始資料的傳輸，傳輸的媒介可以是有線的，比如透過同軸電纜或是光纖；也可以是無線的，比如透過電磁波。\
> 功能:1.讓資料可經由傳輸媒介 2.兩個實際相連的機器間傳送

<font color="#f00">(104)</font>**Access Line 連結switches與hosts之間的傳輸通道，使用UTP \
Trunk Line 連結switches之間的傳輸通道，使用光纖**

#### 2. 資料連結層(Data Link Layer):
> 負責網路尋址、錯誤偵測和改錯，為網路之間建立邏輯連結。
> 將實體層的數位訊號封裝成一組符合邏輯傳輸資料，這組訊號稱為資料訊框（Data Frame）。
> 訊框內包含媒體存取控制（Media Access Control，MAC）位址、
> 邏輯鏈路控制(Logical Link Control, LLC) 兩部分。而資料在傳輸時，這兩項資訊可讓對方主機辨識資料來源。 \
> EUI-48(extended unique identifier) address is the new name for media access control  address.
#### 3. 網路層(Network Layer)／IP層
> 提供路由及定址功能，將網路表頭加至數據包，形成封包，以便在網路間傳遞。
> 主要的通訊協定是網際網路協定（Internet Protocol，IP）目的主要是為這筆資料定下傳送目的地的位址 \
> 資料在傳輸時，該協定將IP位址加入傳輸資料內，並把資料組成封包（Packet）。
> 在網路上傳輸時，封包裡面的IP位址會告訴網路設備這筆資料的來源及目的地。
> 由於網路層主要以IP運作為主，故又稱為「IP層」。
:::success
**Frame vs Packet**\
message:frames and packets \
frame是Data Link Layer的訊號，Frame 包含來源和目標 MAC 地址，用於同一網路設備間傳遞數據\
packet是Network Layer的訊號，用於不同網路之間傳輸數據，包含來源和目標的IP地址\
Frames are carried OUTSIDE packet that have delivery information
![image.png](https://hackmd.io/_uploads/rkldcBM7T.png)

:::
:::success
**路由器(router)的功能for網路層**
路由器簡單來說是連接2個以上個別網路的裝置，決定資料封包（檔案、訊息、網路互動等資料）傳輸的路徑，用來連接桌上型電腦、印表機等連網裝置。
:::
:::success
**<font color="#f00">(104)</font>Ethernet switch（乙太網交換器）和路由器(router)的差別?**
![](https://hackmd.io/_uploads/By1fXk6MT.png)\
Ethernet switch(交換器):它在data link layer（第二層）操作，主要負責在局域網(LAN)中交換數據幀（frame）。\
Router（路由器）： 路由器是一種用於連接不同網絡的設備，它在Network Layer（第三層）操作，主要負責在不同網絡之間轉發數據包（packet）。路由器能夠決定數據包的最佳路徑，以實現數據包在不同網絡之間的傳輸。
:::
#### 4. 傳輸層(Transport Layer)
> 將傳輸表頭併入資料形成封包，負責整體電腦整體的資料傳輸及控制提供可靠或不可靠的遞送，重傳之前先校正錯誤
功能 ：封包順序、資料流量控制、偵測重複的封包、緊急資料的傳送、複雜的錯誤與回復處理、以及安全方面的課題。
例子 ：TCP、UDP
:::success
<font color="#f00">(100)</font>**TCP (傳輸控制協議)** 是網際網路上最常用的協定，這種協定較為可靠，可靠性指的是可以正確地傳送訊息到目的。
![](https://hackmd.io/_uploads/Sk3zmwWM6.png)
1.在收到訊息時，回傳(Acknowledgement, ACK)讓對方確認訊息已被接收 \
2.若訊息在傳送途中遺失，傳送方會因為沒有收到ACK，而判斷對方沒有接收到訊息故重新送一次 \
3.TCP為連接導向，在訊息傳送前先開啟一個連結，傳送後回結束此連結
> *優點*  \
> 經由 TCP 發送的資料能完全到達目的地。即使網路阻塞，傳輸的資料也不會出問題。\
> *缺點*\
> 發送端和接收端之間有很多往來的通訊，因此建立連線和交換資料需要更多的時間。

**Q.為什麼不讓每層都reliable?** \
A.只讓TCP可靠的原因以下
\
一 TCP就位於application layer下，可以讓TCP傳送正確的資料給應用層，就算資料在下方有錯也都已被TCP更正。\
二 因為error correction 會很耗資源，所以應盡量少，講求分工 \
三 並非所有的應用都需要可靠性ex VoIP即不需要可靠性

**UDP**
以串流方式傳送資料，發送端不會等待接收端的確認信號，會繼續不斷發送封包資料。
>*優點*\
>傳輸速度比 TCP 更快。\
>*缺點*\
> UDP 幾乎沒有錯誤修正功能，也不在乎封包遺失，因此很容易出錯
> 
> 但串流媒體、VoIP 語音、網路遊戲等服務經常使用 UDP 協定，這網路應用不太需要可靠性機制，封包遺失不會導致服務中斷。


 **從cost, reliability, connection-oriented 與否等面向比較TCP/UDP之區別，同時能解釋何以TCP/UDP的header中都有『port』欄位**
> 
> ![](https://hackmd.io/_uploads/S1Bl2SGfT.png)

"port"欄位的存在使TCP和UDP能夠實現多路復用、唯一標識、雙向通信，並為網絡通信提供了靈活性和可擴展性，確保數據包能夠在網絡上正確地傳遞到它們的目標應用程序或服務。
:::
#### 5. 會話層(Session Layer)
> 負責建立網路連線，等到資料傳輸結束時，再將連線中斷，運作過程有點像召集多人開會（建立連線），然後彼此之間意見交換（資料傳輸），完成後，宣布散會（中斷連線）。
#### 6.展示層（Presentation Layer）
> 處理不同資料格式之間的字碼轉換及編碼及解碼
功能：字元碼轉換  資料形態轉換  對資料進行壓縮和加密﹐以提高速度和增加安全性
例子：ASCII 碼和 EDCDIC 碼之間的轉換
#### 7.應用層
> 應用層主要功能是處理應用程式，進而提供使用者網路應用服務。
:::success
> 常見的通訊協議
1. DHCP（Dynamic Host Configuration Protocol）
2. FTP（File Transfer Protocol）
3. HTTP（HyperText Transfer Protocol）
4. POP3（Post Office Protocol-Version 3）
:::
> 第七層的應用軟體（網路瀏覽器、電子郵件、線上遊戲、即時通訊等）透過單一或多種通訊協定傳達資料，依據不同的網路服務方式，這些協定能定義各自的功能及使用規範等細部規則，像是網路瀏覽器藉由HTTP的溝通，即可呈現出完整的網頁。
這些和使用者最貼近且直接的應用軟體就屬於第七層應用層的規範。

#### TCP/IP 分層
TCP/IP 模型合併了 OSI 模型的三個層級，將應用層、表示層和會話層合併為一個應用層，因此它更加簡化。
#### 1.實體層(Physical Layer):
> 這一層涉及連接硬件設備，例如電纜、光纖、無線天線等。它定義了數據的傳輸方式，如電壓、光信號或無線信號。
#### 2.資料連結層(Data Link Layer):
> 這一層處理硬件細節，如網卡、以太網和Wi-Fi。它不僅包括標準以太網協議，還包括各種物理介質和協議，如802.11（Wi-Fi）和Bluetooth。
#### 3.網路層(Network Layer)／IP層
> 該層處理路由和數據包轉發。IP（互聯網協議）是網絡層的標準協議，它包括IPv4和IPv6，用於定義數據包的路由和交付。
#### 4.傳輸層(Transport Layer)
> 傳輸層是一個提供應用程式和網路之間的介面。通常使用TCP（傳輸控制協議）和UDP（用戶數據報協議）等協議。TCP用於可靠的數據傳輸，而UDP用於快速但不可靠的數據傳輸。
#### 5.應用層（Application Layer）：
> 這是最高層，用於應用程序之間的通信。常見的標準協議包括HTTP（超文本傳輸協議）用於網頁傳輸，SMTP（簡單郵件傳輸協議）用於電子郵件，FTP（文件傳輸協議）用於文件傳輸，以及DNS（域名系統）用於域名解析。

:::success
**能熟練說出TCP/IP五層協定的名稱並在各層舉一個常見的standard protocol。**\
Physical   DSL, ISDN\
Data Link Layer   wifi, ethernet\
Network   IP\
Transport   TCP\
Application  HTTP
:::

--------
### PPP（Point-to-Point Protocol）VS Switched Network
PPP是一種通信協議，用於建立點對點連接，而交換式網絡是一種網絡架構，通常在多個設備之間實現數據交換。
#### PPP（Point-to-Point Protocol）
> PPP是一種通信協議，用於建立點對點連接，通常是在兩個單獨的設備之間建立連接，例如一台計算機和一個路由器之間的連接。
#### 交換式網絡（Switched Network）
> 交換式網絡是一種網絡架構，其中數據通常通過交換機（Switch）進行路由，以便將數據包從源設備傳送到目標設備。
交換式網絡通常用於局域網（LAN）或廣域網（WAN）中，其中多個設備需要彼此通信，並且數據需要在網絡中進行路由。
:::success
**局域網（LAN, Local Area Network）VS廣域網（WAN, Wide Area Network）** \
LAN是有限的大小 例如校園、辦公大樓\
WAN是指較大的範圍，如多棟建築物間\
LAN由於範圍較小，速度會較快，維護費用較便宜，更容易維護
:::

## 第三章
#### APT（Advanced Persistent Threats）
> 高度專業的、長期存在並持續對特定目標或組織進行攻擊的計算機安全威脅。APTs 的目標通常是政府機構、軍事機構、大型企業、關鍵基礎設施或其他機構，因為它們通常擁有重要的敏感信息和資源。

#### <font color="#f00">(104) </font>**SSL/TLS VPN：(Secure Sockets Layer/Transport Layer Security)**
>  是一種虛擬私人網絡（VPN）技術，它使用安全套接層（SSL）或傳輸層安全性（TLS）協議來加密數據流，以確保在互聯網上的數據傳輸安全和私密。這種類型的 VPN 常用於遠程訪問和遠程工作，以提供用戶安全的遠程連接到內部網絡和資源。\
> **優點**\
> SSL VPN避開了部署及管理必要客戶軟件的復雜性和人力需求;SSL在Web的易用性和安全性方面架起了一座橋梁，目前對SSL VPN公認的三大好處是:
> 1. 安全性： SSL VPN 提供了強大的安全性，通過使用SSL/TLS協議來加密數據流，確保在互聯網上的數據傳輸是安全的。。
> 2. 方便性： SSL VPN 不需要安裝專用的客戶端軟體，通常可以在任何支援SSL/TLS的Web瀏覽器上運行。
> 3. 多層身份驗證： SSL VPN 支援多層身份驗證，這意味著用戶需要提供多個身份驗證因素才能訪問 VPN。這增加了安全性，因為除了密碼之外，可能需要令牌、智慧卡、生物識別信息或其他身份驗證方式。這確保只有授權的用戶可以訪問 VPN。
>
>  **缺點**
> 1. 不適用於所有使用情境： SSL VPN 可能不適用於所有使用情境。例如，對於需要特定應用程序層級控制或更高安全性水平的一些組織，其他 VPN 解決方案如 IPsec VPN 可能更合適。
> 2. 只有中等的強度
> 
>  **實際應用** \
> 遠程訪問企業內部網絡： SSL/TLS VPN 是遠程工作和遠程訪問企業內部資源的理想方式。遠程用戶可以透過網絡瀏覽器訪問公司的內部網絡，從而安全地訪問文件、應用程序、郵件系統和其他資源。

#### **Two-Factor Authentication**
> 需要兩階段驗證
> 如刷卡需要卡片與pin碼

#### **security planning的四個原則**
![](https://hackmd.io/_uploads/rJWXzkTMp.png)

#### <font color="#f00">(101)(106)(110)(111)</font>數位憑證驗證（Digital Certificate Authentication）
> 最安全的憑證機制
> ![](https://hackmd.io/_uploads/Hkia6fzma.png)

> 特點： \
> 1.數位證書的驗證方式不需要使用者的敏感資料（如身分證字號、帳號密碼等)，就可以進行驗證 \
2.可以防範網路釣魚等攻擊，故認為數位證書較其他方式安全。

#### <font color="#f00">(111) </font>kill chain
> Kill chain 為駭客一步步攻擊的手法
> 1. 偵查：觀察目標對象，取得目標相關資料。
> 
> 2. 武裝：透過開源軟體或自行開發惡意程式。
> 
> 3. 遞迭：想辦法將惡意程式迭入企業內部。
>  
> 4. 漏洞利用：利用目標公司的漏洞。
> 
> 5. 安裝：將程式安裝好或安裝後門以便下載其他惡意程式。
> 
> 6. 發令與控制：持續控制目標公司網路。
> 
> 7.行動：持續做出行動以達到最初目的，如竊取密碼、信用卡資料等

- [以kill chain的角度分析ch3的target個案](#killchain+traget個案)

> 

## 第四章
#### **<font color="#f00">(103)(106)(110)</font> QoS（Quality of Service）是一種網絡管理和控制"技術"，旨在確保在計算機網絡中實現特定的服務質量水平。**
![](https://hackmd.io/_uploads/SJ7bIkpzT.png)
:::success
**簡單說明QoS跟SLAs的關聯。**

**SLAs（Service Level Agreements）**:消費者和網路供應商間的協定，可以根據QoS訂出合約內容，來確保供應商的服務有達到訂定的標準，當供應商沒有達到時消費者可以提出求償。


例子：
在線遊戲：當您玩多人在線遊戲時，您希望網絡具有低延遲和最小的丟包率，以確保流暢的遊戲體驗。遊戲提供商通常會有一個SLA，其中規定了他們應該提供的服務質量水平，如每個遊戲回合的最大延遲時間或丟包率。QoS技術可以通過確保遊戲數據包在網絡上具有高優先級，以滿足SLA中的性能指標，從而確保遊戲的流暢性和响应性。
:::

#### momentary traffic peaks(瞬時流量高峰)
> 網絡或服務上突然出現的短期、高強度的流量峰值，通常持續時間很短，但可能對網絡和服務造成壓力和影響。 \
> **solution 1: Overprovision 超額配置**\
> 提供遠多於網絡通常所需的容量。\
> **solution 2: Priority 優先配置**\
> 將重要服務的優先級提高，以確保關鍵業務功能能夠繼續運行，即使有高峰。\
> **solution 3: Reservation 預留**\
> QoS保證了某些流量的預留容量，因此這些流量總是能夠通過。

#### <font color="#f00">(102)(106)(110)</font> Threat environment, Plan, Protect, Response 之間的關係
![](https://hackmd.io/_uploads/ByzlbeTfT.png)
> **Threat Environment（威脅環境）：**
威脅環境是指潛在威脅和風險的狀態和條件，可能對組織或系統造成損害。這包括外部和內部威脅，如惡意攻擊、自然災害、技術故障等 \
**Plan（計劃）：**
計劃是組織為應對威脅環境而制定的策略和行動計劃。在計劃階段，組織評估潛在風險，確定關鍵資產和需求，並制定相應的應對策略。
:::success
<font color="#f00">(100)(101)</font>**Security Planning Principle**
> 1. Risk Analysis 權衡風險與防護成本的一個過程
> 2. Comprehensive Security 全面性防禦，沒有任何漏洞
> 3. Defense in Depth 建議在安全策略中實施多層次的安全措施，以應對多個安全威脅。
> 4. Minimum Permissions 要求限制人員、資源和操作的權限，並實行全面的存取控制。
:::
> **Protect（保護）：**
進行保護措施(eg.限制存取權、防火牆等)\
**Response（應對）：**
雖然有了上述的保護措施，但仍不可能做到100%的阻擋，仍有被攻擊的風險，因此需要制定良好的回應機制，遇到狀況方能即刻反映。



#### <font color="#f00">世哲說會考 </font>**SNMP, Simple Network Management Protocol (簡單網絡管理協議)**
> SNMP（Simple Network Management Protocol，簡單網絡管理協議）它是一個應用層協議，通常用於網絡管理系統（NMS）與許多不同類型的網絡設備之間的通信。 \
> SNMP管理器：管理者使用SNMP管理器來發送請求以獲取信息\
> SNMP agent：負責回應管理器的請求，提供相關的信息和數據。\
> Trap：是一種事件通知機制，當偵測到事件的異常狀態，會發送訊Manager
> ![](https://hackmd.io/_uploads/HkREvl6za.png)

####  **SDN (Software-Defined Networking)**
> SDN (Software-Defined Networking) 將網路分為控制層（Control Plane）與資料層（Data Plane）
將網路的管理權限交由控制層的控制器（Controller）軟體負責，採用集中控管的方式，同時也負責決定傳輸路徑，以讓網路變得更加集中與容易管理

![image.png](https://hackmd.io/_uploads/BJ3WbSUQp.png)

> 簡單來說，就是把網路分成控制層跟資料層，並在中間設立一個控制器，讓這個控制器去管理每個switch要做什麼。
> 
#### <font color="#f00">(107)(110)</font> **Jitter**
> **Latency**：資料傳遞的延遲時間
> 
> **Jitter**：資料傳遞時間的變動量，要降低Jitter需要很大的成本
> 
> **High Jitter**：資料傳輸時間的變動量很大，如看影片一下很順一下很卡
> 
> **Low Jitter** ：資料傳輸時間的變動量很小，如看影片一直都很順 
> 
> **Aggregate Throughput（總吞吐量）**：Aggregate Throughput 是指在一個網絡連接或系統中的總數據傳輸能力


## 第五章

#### **IEEE 802.x 由  IEEE LAN/MAN Standards Committee 制定的一系列網路標準**
> **802.1**：這是一個通用標準，用於支援多個工作組的標準化工作。\
> **802.3**：這一系列標準涵蓋了乙太網技術，包括有線區域網絡的各種方面 \
>  **802.11**：這一系列標準用於無線區域網絡（Wi-Fi）技術
:::info
### 乙太網in實體層
UTP(for 乙太網的電纜)最多只能100m，超過的話訊號就會降級，導致無法正確讀取 \
PS. 光纖可以到500m

:::

#### **Baseband（基頻） vs Broadband（寬頻）** Transmission
> **Baseband（基頻）**：使用單一頻帶寬傳輸數據信號，通常在較低的頻率範圍內。常用於數位訊號和基本數據傳輸應用，如乙太網（Ethernet）。
> 因為baseband便宜又簡單，所以現在的LAN多採用此技術。
> 
> **Broadband（寬頻）**：使用多個頻帶以同時傳輸多個信號。它通常在較高的頻率範圍內工作，允許同時傳輸多個不同頻段的數據。用於多媒體應用，如有線電視、有線寬頻互聯網。
> 如果運用擴大器(amplifier)就可以傳得更遠。

#### **Terminal Crosstalk Interferenc (終端串擾干擾)**
> **串擾干擾（Crosstalk Interference）** 通信或電線系統中的一種干擾現象。這種干擾是由信號在電纜、導線或其他媒介中相互影響而產生的。當電流通過一條線時，它可以產生磁場，這個磁場可以影響附近的其他線路，導致其中的信號受到影響或干擾。
因為通常wire是纏繞的，但在終端的時候會是直的放入RJ-45("Registered Jack"（註冊插孔）)中，所以在終端的時候crosstalk interference最嚴重。
![](https://hackmd.io/_uploads/ryW6dAg7T.png)

#### **光纖傳輸（Optical Fiber Transmission）**
> 通過使用光學纖維來傳輸數據、聲音和視頻信號。光學纖維是一種由玻璃或塑料製成的非常細的纖維，可以將數據信號轉換為光信號，並通過光纖將信號傳送到目的地。
> 
> ![](https://hackmd.io/_uploads/Skya11Z7a.png)

:::info
### 乙太網in data link 層

![](https://hackmd.io/_uploads/Sy0s4yWQp.png)
:::

### Advanced Ethernet Capabilities

![](https://hackmd.io/_uploads/rkdfLJ-7a.png)

控制器（Controller）：控制器是 SDN 架構的核心元件，負責制定網絡策略以及指導數據層（Data Plane）上的網絡設備 \
控制層（Control Plane）：控制層位於 SDN 架構的頂部，主要功能是網絡管理、策略制定和流量工程。\
數據層（Data Plane）：數據層包括實際的網絡設備，如交換機和路由器。這些設備根據來自控制層的指示，將數據包從一個地方傳送到另一個地方，實現網絡數據的傳輸。


#### <font color="#f00">世哲說會考 </font>UTP類別
![image.png](https://hackmd.io/_uploads/SJPGd4I7p.png)
在Ethernet網絡中，100BASE-XX是一種以太網簡稱，其中的「BASE」代表基地帶（baseband）。 \
Baseband使用整個頻譜範圍來傳輸單一數據信號，而Broadband則在較大的頻譜範圍內同時傳輸多個信號或通道


## 第六章

### <font color="#f00">(103)(107)(111)</font>Wireless Propagation Problem(5個)
1.**電磁干擾(EMI, Electromagneic Interference)**：因電磁感應效應對周遭的其他設備造成干擾。
![image.png](https://hackmd.io/_uploads/H1WZj7Gm6.png)

2.**陰影區(Shadow Zone)**:訊號傳遞過程中被障礙物干擾而無法傳遞
![image.png](https://hackmd.io/_uploads/HkC4hQfmp.png)

3.**平方反比效應(Inverse Square Law Attenuation)**：距離越遠，訊號強度會快速下降，下降至1/r^2

eg. 10公尺時有9的強度，30公尺時就會下降為1的強度
![image.png](https://hackmd.io/_uploads/S1RR67M7p.png)

4.**吸收衰減**：訊號會被空氣和水所吸收，因此訊號傳遞範圍有限

5.**多重路徑干擾**：直線傳送的訊號與反射訊號會互相干擾，為同頻率的波最糟狀況可能會沒有訊號
![image.png](https://hackmd.io/_uploads/By-OJ4GXp.png)
![image.png](https://hackmd.io/_uploads/r1POJVzmp.png)

------

### 頻譜（Frequency Spectrum）, 服務頻段（Service Band）, 通道（Channel）
頻譜（Frequency Spectrum）：頻譜是整個無線通信頻率範圍的總和，通常以赫茲（Hz）為單位。從0到無限

服務頻段（Service Band）：頻譜裡會有很多Service Band，如FM、GPS、電信等等

頻道（Channel）：Service Band中又會畫分多個Channel，比方說FM中會有不同的Channel

### transmission speed vs bandwith
帶寬（Bandwidth）：指在通信和信號處理領域中用來描述一個信號的頻率範圍或能夠傳輸的數據量。帶寬通常以赫茲（Hz）為單位，直接將訊號送出
![image.png](https://hackmd.io/_uploads/ByEstVMQp.png)
高速的訊號需要較寬的帶寬
* Boardband channel：較寬的訊號帶寬，速度較快，需要經由電路處理將訊號送出，傳輸boardband
* Narrowband channel：較窄的訊號帶寬，用於傳輸Baseband信號

**Baseband（基頻） vs Broadband（寬頻）** Transmission
> **Baseband（基頻）**：使用單一頻帶寬傳輸數據信號，通常在較低的頻率範圍內。常用於數位訊號和基本數據傳輸應用，如乙太網（Ethernet）。
> 因為baseband便宜又簡單，所以現在的LAN多採用此技術。
> 
> **Broadband（寬頻）**：使用多個頻帶以同時傳輸多個信號。它通常在較高的頻率範圍內工作，允許同時傳輸多個不同頻段的數據。用於多媒體應用，如有線電視、有線寬頻互聯網。
> 如果運用擴大器(amplifier)就可以傳得更遠。


### <font color="#f00">(107)</font>golden zone
> 高頻區可能會有傳遞問題，低頻區可能會有不夠的帶寬
![image.png](https://hackmd.io/_uploads/H18fj4zQp.png)


**說明何者為「Golden Zone」並且與Wireless Propagation Problem有何關聯性？** \
優化無線通信系統的設計和部署，以實現 Golden Zone，對於解決無線傳播問題至關重要。

### 是非題考古區
<font color="#f00">(107)</font>
> (O) 01.	The Internet is a ‘best effort’ delivery system.
> \
> (X) 02.	Frames are carried ~~inside~~<font color="#f00">Outside</font> packet that have delivery information.<font color="#0000ff">(106)</font>
\
> (O) 03.	EUI-48 address is the new name for Media Access Control (MAC) address.<font color="#0000ff">(106)</font>
\
> (O) 04.	There are two reasons for message fragmentation: error correction and multiplexing.<font color="#0000ff">(106)</font>
\
> (O) 05.	It is possible that a single network exists with some devices using different standards.<font color="#0000ff">(106)</font>
\
(X) 06.	A ~~link~~ <font color="#f00">route</font> is the path that a packet takes from the source host to the destination host across an internet.<font color="#0000ff">(106)</font>
\
(O) 07.	TCP is reliable protocol, while Ethernet is not.<font color="#0000ff">(106)</font>
\
(O) 08.	Not all messages have all three parts of Header, Data Field and Trailer.<font color="#0000ff">(106)</font>\
<font color="#f00"> It depends on the protocol type. This message structure is typically used for specific communication protocols, such as the Ethernet protocol.</font>
\
(X) 09.	Converting outgoing analog signals into digital ones is call ‘decoding’.<font color="#0000ff">(106)</font> <font color="#f00"> 類比轉數位>encodeing</font>
\
(X) 10.	~~OSI~~ <font color="#f00"> ISO </font> is the standard agency while ~~ISO~~ <font color="#f00"> OSI </font>is a standard framework.<font color="#0000ff">(106)</font> \
<font color="#f00"> ISO（International Organization for Standardization）：ISO是一個國際標準制定組織\
OSI（Open Systems Interconnection）：OSI是網路的七層架構</font> \
(X) 11.	Phishing is the use of programs that disguise themselves as system file.<font color="#0000ff">(106)</font> \
<font color="#f00"> Phishing(釣魚)指看似真實的網站or郵件去騙你的個資。假裝自己是系統檔案的是木馬病毒 </font>
\
(X) 12.	Trojan horse is a vulnerability-specific attack that occurs before a patch is available.
<font color="#f00"> 假裝自己是系統檔案的是木馬病毒</font>
\
(O) 13.	Security is primarily a management issue, not a technology issue.<font color="#0000ff">(106)</font>\
(O) 14.	RSTP is designed to solve the problem of single point failure in the hierarchical Ethernet switch network. \
<font color="#f00">RSTP（Rapid Spanning Tree Protocol）是為了解決階層式乙太網交換網路中單點故障的問題而設計的。RSTP是一種網路協議，它的主要功能是在一個以太網交換網路中建立冗余路徑，以確保數據通信的可靠性和容錯能力。當網路中的某個交換機或連接失故障時，RSTP可以迅速重新計算網路拓撲，找到新的最佳路徑，從而繼續提供連接，而不會造成網路中斷。\
RSTP的主要目標是減少網路中的單點故障帶來的影響，確保數據的連通性和可用性。</font>
\
(O) 15.	In baseband transmission, the signal is injected directly into the medium.<font color="#0000ff">(106)</font> \
<font color="#f00"> bathband是直接將訊號發出，boardband才是經過電路處理才發出 </font>
\
(O) 16.	Transmission lines that connect switches to other switches are called ‘trunk line’.<font color="#0000ff">(106)</font> \
(X) 17.	A switch has to know the frame’s entire path through the network.<font color="#0000ff">(106)</font> <font color="#f00"> switch只要知道接下來下一步在哪 </font>\
(X) 18.	Wireshark is useful network diagnostic tool, but it can ~~only~~ look at the content of Ethernet frames.<font color="#0000ff">(106)</font>\
(X) 19.	The maximum distance in LANs using UTP lines is usually 500 meters<font color="#0000ff">(106)</font><font color="#f00"> UTP是100，光纖才是500 </font>\
(O) 20.	Transmission systems that are very fast are usually called broadband systems even when they do not use radio channels.

<font color="#f00">(106)</font> 
> 1.(O) The internet is a best effort delivery system.\
> 12.(X) an APT is a vulnerability-specifie attack that occurs before a patch is available. \
> <font color="#f00">高級持續性威脅（APT，Advanced Persistent Threat）是一種針對特定目標的長期和高度專業的網絡攻擊，通常不一定發生在安全漏洞的修補程序（patch）之前。</font> \
> 13.	(O) A Trojan Horse cannot spread from one computer to another by itself. \
>  <font color="#f00">可以這樣的是worm(蠕蟲)</font> \
>  20.(X) in a connectionless protocol, each message is given a sequence number to ensure on message is missing and allow the receiving process to deal with duplicated segment.
>  <font color="#f00">connectionless protocol通常不使用序列號（sequence number）來確保消息不丟失或處理重複段（duplicated segment）。無連接協議主要用於簡單的數據傳輸，其中每個數據包或消息都是獨立的，沒有建立持久的連接或通道。</font>

### 考古有出現但我不知道放哪裡好
#### <font color="#f00">(100)(101)(103)</font> **什麼是OMAP?** 
- **Operations（運營）**：涉及實際運行和管理網路的日常工作，確保網路正常運作和處理故障。
- **Maintenance（維護）**：包括維持網路設施的正常狀態，進行預防性和修復性維護，以確保網路的穩定性和效能。
- **Administration（管理）**：指的是管理網路資源，包括資源配置、安全性、授權以及監控使用情況等。
- **Provisioning（配置）**：涉及新資源或服務的設置和配置，以滿足使用者需求。

### 課本的個案

#### <font color="#f00">(111)</font>CH3.Target Breach 遭到信用盜刷案
攻擊者使用了釣魚的方式，誘使員工下載惡意軟體，且該惡意軟體擷取了第三方供應商的憑證，並利用此憑證進入Target內部網路，接下來在pos機系統上下載惡意軟體，該惡意軟體會蒐集信用卡資訊，並傳送給攻擊者。

![S__69836802 (2).jpg](https://hackmd.io/_uploads/rJx5Ium76.jpg)

**從Target事件中學到的教訓?** \
1.不應該相信外部供應商的安全性，在這個案例裡的供應商使用了免費的防毒軟體，安全性差。 \
2.這個案例還將惡意軟體裝到pos機上，這種高敏感低安全的部分應該被隔離。

### **killchain+traget個案**
Target因為沒有把顧客敏感資料和公司內部網路分開，並錯信外部供應商的安全性，讓駭客有機可趁，以kill chain的角度來說，Target可以在kill chain的任一步驟讓駭客打退堂鼓。\
**1～3階段可以透過教育訓練員工，甚至是合作供應商不點擊來路不明郵件或使用來路不明USB\
3～4階段可以透過防火牆阻擋不信任連線或封包\
5～7階段可透過防毒軟體不讓惡意程式進入或下載惡意軟體等**


#### **考古錯題**
* Access Line 連結switches與hosts之間的傳輸通道，使用UTP \
Trunk Line 連結switches之間的傳輸通道，使用光纖 

* 無連接協議(connectionless protocol)主要用於簡單的數據傳輸，其中每個數據包或消息都是獨立的，沒有建立持久的連接或通道。
* A ~~link~~ <font color="#f00">route</font> is the path that a packet takes from the source host to the destination host across an internet
