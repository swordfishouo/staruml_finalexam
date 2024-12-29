# 利用"4+1視圖建模方法進行"精準扶貧管理系統"的軟件架構設計

<tr>
  <h3>10924251林旂宇</h3>
</tr>

<h2>
目錄:<br>
1."4+1"視圖建模方法<br>
2.利用"4+1"視圖建模方法進行"精準扶貧管理系統"的軟件架構設計過程<br>
  &nbsp;&nbsp;2-1.精準扶貧管理系統內容描述<br>
  &nbsp;&nbsp;2-2.需求分析<br>
  &nbsp;&nbsp;&nbsp;&nbsp;2-2-1.角色分類<br>
  &nbsp;&nbsp;&nbsp;&nbsp;2-2-2.系統需求分析<br>
  &nbsp;&nbsp;&nbsp;&nbsp;2-2-3.功能模塊圖<br>
  &nbsp;&nbsp;2-3.場景視圖之用例圖設計建模<br>
  &nbsp;&nbsp;&nbsp;&nbsp;2-3-1.精準扶貧管理系統用例圖<br>
  &nbsp;&nbsp;&nbsp;&nbsp;2-3-2.精準扶貧管理系統關鍵用例描述<br>
  &nbsp;&nbsp;2-4.邏輯試圖之類圖設計建模<br>
  &nbsp;&nbsp;&nbsp;&nbsp;2-4-1.精準扶貧管理系統實體及其屬性分析<br>
  &nbsp;&nbsp;&nbsp;&nbsp;2-4-2.精準扶貧管理系統邏輯視圖-類圖<br>
  &nbsp;&nbsp;&nbsp;&nbsp;2-4-3.精準扶貧管理系統關鍵類圖說明<br>
  &nbsp;&nbsp;2-5.開發視圖建模<br>
  &nbsp;&nbsp;&nbsp;&nbsp;2-5-1.包圖設計建模<br>
  &nbsp;&nbsp;&nbsp;&nbsp;2-5-2.組件圖設計建模<br>
  &nbsp;&nbsp;2-6.過程視圖之交互圖建模<br>
  &nbsp;&nbsp;&nbsp;&nbsp;2-6-1.注冊用戶順序圖<br>
  &nbsp;&nbsp;&nbsp;&nbsp;2-6-2.提交申請順序圖<br>
  &nbsp;&nbsp;&nbsp;&nbsp;2-6-3.查看貧困戶檔案順序圖<br>
  &nbsp;&nbsp;&nbsp;&nbsp;2-6-4.查詢公告順序圖<br>
  &nbsp;&nbsp;&nbsp;&nbsp;2-6-5.查詢系統數據信息順序圖<br>
  &nbsp;&nbsp;2-7.物理視圖之部署圖建模<br>
3.利用設計模式改進<br>
  &nbsp;&nbsp;3-1.消息通知模塊管理模塊的原設計方案類圖<br>
  &nbsp;&nbsp;3-2.消息通知模塊管理模塊采用工廠方法模型設計方案類圖<br>
  &nbsp;&nbsp;3-3.設計模式改進前後對比分析<br>
4.總結<br>
  &nbsp;&nbsp;4-1.內容總結<br>
  &nbsp;&nbsp;4-2.工作總結<br>

</h2>

<h1>1."4+1"視圖建模方法</h1>

<h3>
軟件架構常用模型就是視圖模型，類似於RM-ODP的視點模型，可以從多個角度描述一個覆雜的軟件系統。最流行的視圖模型就是"4+1"視圖模型，它由五個視圖組成，包括場景視圖、邏輯視圖、進程視圖、物理視圖和開發視圖，如圖所示。我們可以粗略地把"4+1"視圖模型看作是參照軟件生命周期五個階段建立的視圖模型，雖然實際上每個視圖描述的內容並不是局限於生命周期的一個階段，但顯而易見的是，除了結構要素之外，這種視圖模型也包含了流程要素。
</h3>

![image](https://github.com/swordfishouo/staruml_finalexam/blob/main/1.jpg)

<h3>
"4+1"視圖模型實際上使得有不同需求的人員能夠得到他們對於軟件體系結構想要了解的東西。系統工程師先從物理視圖，然後從過程視圖靠近體系結構。最終使用者、客戶、數據專家從邏輯視圖看體系結構；項目經理、軟件配置人員從開發視圖看體系結構。<br>

邏輯視圖也稱概念視圖，主要是支持系統功能需求的抽象描述，即系統最終將提供給用戶什麽樣的服務。邏輯視圖關注的是系統必須為用戶提供的功能，不僅包括用戶可見的功能，還包括為實現用戶功能而必須提供的系統功能。在UML中，邏輯視圖包含了類、接口和協作，它展現了系統的靜態或結構組成及特征，描述場景視圖提出的系統功能的實現。邏輯視圖在UML中通常表現為類圖、交互圖、順序圖和狀態圖。<br>

開發視圖也稱模塊視圖，主要側重於描述系統的組織，與邏輯視圖密切相關，都描述了系統的靜態結構。開發視圖關注的是程序包，不僅包括要編寫的源程序，還包括可以直接使用的第三份SDK和現成框架、類庫，以及開發的系統將運行於其上的系統軟件或中間件等。開發視圖關注軟件開發環境下實際模塊的組織，反映了開發難度、軟件管理、重用性和通用性及由工具集、編程語言所帶來的限制和約束等。開發視圖和邏輯視圖之間可能存在一定的映射關系。開發視圖在UML中通常表現為包圖。<br>

過程視圖主要側重於描述系統的動態行為，即系統運行時所表現出來的相關特性，著重解決系統的可靠性、吞吐量、並發性、分布性和容錯性。過程視圖的關注點是運行中的線程、進程和對象等概念，以及相關的並發、同步、通信等問題。過程視圖和開發視圖相比，開發視圖一般偏重程序包在編譯時的靜態依賴關系，而這些程序運行起來之後就會表現為對象、線程、進程以及它們之間的調用關系，過程視圖比較關心的正式這些運行時單元的交互問題。過程視圖在UML中通常表現為活動圖、交互圖和狀態圖。<br>

物理視圖描述如何把系統軟件元素映射到硬件上，通常要考慮系統的性能、規模和容錯等問題，展示了所需要的物理環境、硬件配置和分布狀況。物理視圖關注的是目標程序及其依賴的運行庫和系統軟件最終如何安裝和部署到物理機器上，以及如何部署機器和網絡來配置軟件系統的可靠性、可伸縮性等要求。物理視圖和過程視圖相比，過程視圖特別關注目標程序的動態執行情況，而物理視圖重視目標程序的靜態位置問題；物理視圖是綜合考慮軟件系統和整個IT系統相互影響的架構視圖。物理視圖在UML中通常表現為部署圖。<br>
</h3>

<h1>2.利用"4+1"視圖建模方法進行"精準扶貧管理系統"的軟件架構設計過程</h1>

<h2>2-1.精準扶貧管理系統內容描述</h2>

<h3>
精準扶貧信息化平台可實現全省貧困戶信息的全面、準確統計；對扶貧項目、扶貧資金的全面公開、監督管理；對扶貧過程進行有效跟蹤、管理；對扶貧結果進行實時查詢；為扶貧工作的更進一步開展積累有效的基礎數據，為全省扶貧的大數據趨勢分析奠定良好的基礎。精準扶貧信息化平台由精準扶貧管理系統支持，該系統適用於省級、市級扶貧主管部門對扶貧信息數據的及時準確統計，扶貧信息的精準推送，為扶貧工作提供互動溝通的平台，實現對扶貧工作的信息化管理。<br>
	
精準扶貧管理系統主要分為四個部分，精準識別、精準幫扶／管理、幫扶成效評價意見反饋和大數據分析。整個精準扶貧信息化平台的應用貫穿貧困戶精確識別、精確幫扶、精確管理、幫扶成效評價、意見反饋、大數據分析等整個扶貧全過程；在貧困戶精確識別階段可實現扶貧信息公示、評選結果反饋、建立貧困戶檔案和數據庫等功能；在幫扶階段，可為精確幫扶、精確管理提供信息化手段支撐，包括貧困戶信息管理、陽光操作管理、扶貧事權管理；在幫扶成效評估和意見反饋階段，可提供基於互聯網+的在線評價和網站在線反饋功能；通過對系統運行積累的大數據進行系統分析，可提供對貧困原因、幫扶措施、幫扶效果、貧困戶分布等的關聯性分析，趨勢分析、預測，綜合數據分析，數據挖掘，領導輔助決策，統計報表等功能。具體內容描述如圖所示。<br>
	
具體來講，基於"精準扶貧信息化平台"主要包括全省四級一體的數據平台、基於互聯網的外網網站、各級人員使用的手機APP客戶端、扶貧事權管理系統和扶貧大數據分析系統等主要內容，並建立相應的信息化支撐體系。<br>
</h3>

![image](https://github.com/swordfishouo/staruml_finalexam/blob/main/2.jpg)

<h2>2-2需求分析</h2>

<h3>
2-2-1.角色分類<br>
根據精準扶貧管理系統所有的內容描述，我們可以大致擬定和精準扶貧管理系統有關的角色為以下四種。<br>
</h3>

![image](https://github.com/swordfishouo/staruml_finalexam/blob/main/L1.jpg)

<h3>
2-2-2.系統需求分析<br>
精準扶貧信息化平台的應用貫穿貧困戶精確識別、精確幫扶、精確管理、幫扶成效評價、意見反饋、大數據分析等整個扶貧全過程；在貧困戶精確識別階段可實現扶貧信息公示、評選結果反饋、建立貧困戶檔案和數據庫等功能；在幫扶階段，可為精確幫扶、精確管理提供信息化手段支撐，包括貧困戶信息管理、陽光操作管理、扶貧事權管理；在幫扶成效評估和意見反饋階段，可提供基於互聯網+的在線評價和網站在線反饋功能；通過對系統運行積累的大數據進行系統分析，可提供對貧困原因、幫扶措施、幫扶效果、貧困戶分布等的關聯性分析，趨勢分析、預測，綜合數據分析，數據挖掘，領導輔助決策，統計報表等功能。<br>
。精準扶貧管理系統功能性分析<br>
精準扶貧管理系統的功能性分析可以反映這個系統能夠完成的各項功能，它能夠清晰、明確地把這個系統要完成的功能展示給後續的設計人員和使用者。精準扶貧管理系統的具體功能如下：<br>
&nbsp;&nbsp;。系統允許群眾注冊<br>
&nbsp;&nbsp;。系統允許群眾登錄系統<br>
&nbsp;&nbsp;。系統允許群眾查看個人基本信息<br>
&nbsp;&nbsp;。系統允許群眾修改個人基本信息<br>
&nbsp;&nbsp;。系統允許群眾在線提出貧困戶申請<br>
&nbsp;&nbsp;。系統允許群眾進行在線留言<br>
&nbsp;&nbsp;。系統允許群眾進行在線評價<br>
&nbsp;&nbsp;。系統允許群眾查看個人的貧困戶檔案<br>
&nbsp;&nbsp;。系統為群眾分配自己的賬戶和訪問權限<br>
&nbsp;&nbsp;。系統允許基層工作人員登陸系統<br>
&nbsp;&nbsp;。系統允許基層工作人員查看群眾用戶基本信息<br>
&nbsp;&nbsp;。系統允許基層工作人員新建貧困戶檔案<br>
&nbsp;&nbsp;。系統允許基層工作人員更新貧困戶檔案<br>
&nbsp;&nbsp;。系統允許基層工作人員查詢貧困戶檔案<br>
&nbsp;&nbsp;。系統允許基層工作人員刪除貧困戶檔案<br>
&nbsp;&nbsp;。系統為基層工作人員分配自己的賬戶和訪問權限<br>
&nbsp;&nbsp;。系統允許系統管理員登錄系統<br>
&nbsp;&nbsp;。系統允許系統管理員管理群眾用戶貧困申請<br>
&nbsp;&nbsp;。系統允許系統管理員公告通知"貧困戶"名額<br>
&nbsp;&nbsp;。系統允許系統管理員公告通知申請評選須知<br>
&nbsp;&nbsp;。系統允許系統管理員公告通知申請人名單信息<br>
&nbsp;&nbsp;。系統允許系統管理員公告通知貧困戶評選結果<br>
&nbsp;&nbsp;。系統允許系統管理員修改公告通知<br>
&nbsp;&nbsp;。系統允許系統管理員刪除公告通知<br>
&nbsp;&nbsp;。系統允許系統管理員查看公告通知<br>
&nbsp;&nbsp;。系統允許系統管理員查看群眾在線留言<br>
&nbsp;&nbsp;。系統允許系統管理員刪除群眾在線留言<br>
&nbsp;&nbsp;。系統允許系統管理員回覆群眾在線留言<br>
&nbsp;&nbsp;。系統允許系統管理員查看群眾在線評論<br>
&nbsp;&nbsp;。系統允許系統管理員刪除群眾在線評論<br>
&nbsp;&nbsp;。系統允許系統管理員回覆群眾在線評論<br>
&nbsp;&nbsp;。系統允許系統管理員查看用戶基本信息<br>
&nbsp;&nbsp;。系統允許系統管理員修改用戶基本信息<br>
&nbsp;&nbsp;。系統允許系統管理員管理用戶權限<br>
&nbsp;&nbsp;。系統為系統管理員分配自己的賬戶和訪問權限<br>
&nbsp;&nbsp;。系統允許主管領導登錄系統<br>
&nbsp;&nbsp;。系統允許主管領導查看貧困戶檔案<br>
&nbsp;&nbsp;。系統允許主管領導查看公告通知<br>
&nbsp;&nbsp;。系統允許主管領導查看群眾用戶基本信息<br>
&nbsp;&nbsp;。系統允許主管領導查看貧困戶信息數據庫分析統計報表<br>
&nbsp;&nbsp;。系統允許主管領導查看群眾留言評論<br>
&nbsp;&nbsp;。系統允許主管領導查看扶貧資金發放流程及進度<br>
&nbsp;&nbsp;。系統允許主管領導查看扶貧過程情況和進度<br>
。精準扶貧管理系統非功能性分析<br>
&nbsp;&nbsp;。網絡響應速度應該盡量快<br>
&nbsp;&nbsp;。用戶填寫的信息應該盡量少，盡量采用選擇和勾選方式<br>
&nbsp;&nbsp;。系統應該有預留接口，可以方便地連接到客服的電話<br>
</h3>

<h3>
2-2-3.功能模塊圖<br>
精準扶貧管理系統的功能模塊圖反映了精準扶貧管理系統的功能及各個功能之間的關係。總體分為"注冊"、"登錄"、"公告通知"、"檔案管理"、"消息管理"、"留言反饋"、"用戶管理"、"審查監督"八個模塊，具體內容如圖所示。<br>
</h3>

![image](https://github.com/swordfishouo/staruml_finalexam/blob/main/3.jpg)

<h3>
功能模塊圖說明：<br>
。註冊:<br>
【功能描述】<br>
群眾用戶在使用精準扶貧管理系統進行在線貧困申請、在線留言、在線評論之前，需要進行用戶注冊，並填寫相應的注冊信息。<br>
【操作者】群眾<br>
。登錄:<br>
【功能描述】<br>
系統所有用戶，包括群眾、基層工作人員、系統管理員以及主管領導，在本精準扶貧管理系統進行相應權限的操作之前都需要先登錄系統，以便系統為其分配操作權限。<br>
【操作者】群眾、基層工作人員、系統管理員、主管領導<br>
。公告通知:<br>
【功能描述】<br>
群眾用戶在公告通知面板上瀏覽查看由系統管理員發布最新通知公示信息。<br>
【操作者】群眾<br>
【功能描述】<br>
系統管理員在公告通知模塊新建公告通知，編輯公告通知內容，並發布到公告通知面板上，供群眾用戶瀏覽查看。<br>
【操作者】系統管理員<br>
。檔案管理:<br>
【功能描述】<br>
針對貧困申請通過的群眾用戶，需要對進行一系列的貧困戶檔案管理， 包括新建貧困戶檔案、查看貧困戶檔案、更新貧困戶檔案、刪除貧困戶檔案的操作，其中貧困戶檔案中，包含了貧困戶基本信息表、貧困戶需求情況表、貧困幫扶情況表、脫貧計劃、貧困戶台賬、幫扶結果、幫扶措施等內容。<br>
【操作者】基層工作人員<br>
。消息管理:<br>
【功能描述】<br>
主要針對群眾用戶對精準扶貧管理系統的一系列操作進行響應處理。包括群眾用戶的貧困申請、在線評論、在線留言等內容的查看、刪除、回覆等。<br>
【操作者】系統管理員<br>
。留言反饋:<br>
【功能描述】<br>
為了達到更好更準確的幫扶效果，精準扶貧管理系統為群眾用戶提供留言反饋功能模塊，群眾用戶可以針對公告通知、幫扶措施、幫扶結果、幫扶成效等內容進行在線留言、在線評價等操作。<br>
【操作者】群眾<br>
。用戶管理:<br>
【功能描述】<br>
精準扶貧管理系統的用戶有四種，系統為每個用戶分配了自己的賬戶和權限，系統管理員可對用戶的信心進行查看和修改，以及權限的設置。<br>
【操作者】系統管理員<br>
。審查監管:<br>
【功能描述】<br>
實現對扶貧資金、扶貧項目、項目審批的全流程監管。充分發揮省、市兩級政府的扶貧資金和項目監管作用，主管領導可在該功能模塊下查看扶貧項目進度，資金發放情況、扶貧審批情況以及貧困戶信息數據庫分析統計報表等內容。<br>
【操作者】主管領導<br>
</h3>

<h2>2-3場景視圖之用例圖設計建模<br><h2>
	
<h3>
2-3-1.精準扶貧管理系統用例圖<br>
群眾用例圖、基層工作人員用例圖、系統管理員用例圖以及主管領導用例圖分別如圖所示。<br>
</h3>

![image](https://github.com/swordfishouo/staruml_finalexam/blob/main/4.jpg)
![image](https://github.com/swordfishouo/staruml_finalexam/blob/main/5.jpg)
![image](https://github.com/swordfishouo/staruml_finalexam/blob/main/6.jpg)
![image](https://github.com/swordfishouo/staruml_finalexam/blob/main/7.jpg)

<h3>2-3-2.精準扶貧管理系統關鍵用例描述</h3>

![image](https://github.com/swordfishouo/staruml_finalexam/blob/main/L2.jpg)
![image](https://github.com/swordfishouo/staruml_finalexam/blob/main/L3.jpg)
![image](https://github.com/swordfishouo/staruml_finalexam/blob/main/L4.jpg)
![image](https://github.com/swordfishouo/staruml_finalexam/blob/main/L5.jpg)
![image](https://github.com/swordfishouo/staruml_finalexam/blob/main/L6.jpg)
![image](https://github.com/swordfishouo/staruml_finalexam/blob/main/L7.jpg)
![image](https://github.com/swordfishouo/staruml_finalexam/blob/main/L8.jpg)
![image](https://github.com/swordfishouo/staruml_finalexam/blob/main/L9.jpg)
![image](https://github.com/swordfishouo/staruml_finalexam/blob/main/L10.jpg)
![image](https://github.com/swordfishouo/staruml_finalexam/blob/main/L11.jpg)

<h2>2-4.邏輯試圖之類圖設計建模<br><h2>

<h3>
2-4-1.精準扶貧管理系統實體及其屬性分析<br>
根據前面的系統用例分析，我們抽象出系統實體，並對實體進行了輸入性分析，實體及其屬性分析圖如圖所示<br>
</h3>

![image](https://github.com/swordfishouo/staruml_finalexam/blob/main/8.jpg)

<h3>2-4-2.精準扶貧管理系統邏輯視圖-類圖<br></h3>

![image](https://github.com/swordfishouo/staruml_finalexam/blob/main/9.jpg)

<h3>
2-4-3.精準扶貧管理系統關鍵類圖說明<br>
。消息數據庫類:<br>
由申請單、評論、留言、公告通知組成，包含了公告通知模塊、留言反饋模塊和消息管理模塊。請申請單內容、評論內容、留言內容由群眾用戶產生，由系統管理員負責管理處理，包含了查看、刪除、修改等操作。通知公告內容由系統管理員產生，群眾用戶可查看。主管領導可查看消息數據庫類中的所有內容。<br>
。貧困戶信息數據庫類:<br>
由所有審核認證的貧困戶檔案組成，對應了功能模塊為檔案管理。內容由基層工作人員錄入，並進行管理，包括新建、查看、修改、刪除等操作。群眾用戶可查看自己的貧困戶檔案，主管領導可查看所有的貧困戶檔案。<br>
。用戶數據庫:<br>
由所有群眾用戶的基本信息組成，對應的功能模塊為用戶管理。內容由注冊群眾用戶產生，系統管理員可對內容進行管理，包括查看、修改用戶信息以及設置用戶權限。基礎工作人員和領導可查看用戶數據庫內容的用戶基本信息。<br>
。項目統計數據庫類:<br>
由扶貧項目、扶貧資金以及統計報表組成，對應的功能模塊為審查監管。內容有用戶數據庫、貧困戶信息數據庫和消息數據庫的數據統計生成。由主管領導負責管理，包括新建、查看、修改、刪除報表和查看項目及項目資金等等操作。<br>
</h3>

<h2>2-5.開發視圖建模</h2>

<h3>2-5-1.包圖設計建模</h3>

![image](https://github.com/swordfishouo/staruml_finalexam/blob/main/10.jpg)

<h3>
【說明】<br>
1.精準扶貧管理系統包圖主要由“業務相關人員”、“業務界面”、“後台管理”以及“系統數據信息”是四包組成。<br>
2.業務相關人員包包括群眾用戶類、系統管理員類、主管領導類以及基層管理人員類。群眾依賴業務界面，基層工作人員和系統管理員依賴後台管理。所有的數據內容都依賴於系統數據庫。<br>
3.業務界面包包括申請單類、評論類、留言類以及公告通知類。主要為群眾用戶涉及處理的一系列界面操作內容，依賴於後台管理。<br>
4.後台管理包包括了貧困戶檔案類、扶貧項目類、扶貧資金類以及統計報表類。主要為基層工作人員以及主管領導需要處理和查看的一系列內容，依賴於系統數據信息。<br>
系統數據信息包包括消息數據庫內、貧困戶信息數據庫類、用戶數據庫類以及項目統計數據庫類，其他包提供數據內容支持。<br>
</h3>

<h3>2-5-2.組件圖設計建模<br></h3>

![image](https://github.com/swordfishouo/staruml_finalexam/blob/main/11.jpg)

<h3>
【說明】<br>
1.精準扶貧管理系統組件圖主要包括圖2.5.2-1所示的13個組件。<br>
2.消息通知管理組件由消息管理、公告通知以及留言反饋組件組成。<br>
3.消息通知管理組件依賴與消息數據庫組件；檔案管理組件依賴於貧困戶信息數據庫組件；用戶管理組件依賴於用戶數據庫組件；審查監管組件依賴於項目統計數據庫組件。<br>
4.項目統計數據庫的數據內容由消息數據庫、貧困戶信息數據庫以及用戶數據庫生成，所以項目統計數據依賴於三者。<br>
</h3>

<h2>2-6.過程視圖之交互圖建模<br></h2>

<h3>
針對精準扶貧管理系統的部分關鍵用例作如下順序圖建模。<br>
2-6-1.注冊用戶順序圖<br>
</h3>

![image](https://github.com/swordfishouo/staruml_finalexam/blob/main/12.jpg)

<h3>2-6-2.提交申請順序圖<br></h3>

![image](https://github.com/swordfishouo/staruml_finalexam/blob/main/13.jpg)

<h3>2-6-3.查看貧困戶檔案順序圖<br></h3>

![image](https://github.com/swordfishouo/staruml_finalexam/blob/main/14.jpg)

<h3>2-6-4.查詢公告順序圖<br></h3>

![image](https://github.com/swordfishouo/staruml_finalexam/blob/main/15.jpg)

<h3>2-6-5.查詢系統數據信息順序圖<br></h3>

![image](https://github.com/swordfishouo/staruml_finalexam/blob/main/16.jpg)

<h2>2-7.物理視圖之部署圖建模<br></h2>

![image](https://github.com/swordfishouo/staruml_finalexam/blob/main/17.jpg)

<h3>
【說明】<br>
1.精準扶貧管理系統部署圖主要由客戶計算機、應用服務器以及數據庫服務器三個部分組成。<br>
2.客戶計算機主要包括方便攜帶查看的手機客戶端和方便操作處理的web瀏覽器端。<br>
3.消息通知管理、檔案管理、審查監管、用戶管理等一些列系統管理組件都部署在應用服務器上，以供系統管理員、基層工作人員以及主管領導操作管理。<br>
4.用戶數據庫、消息數據庫、貧困戶信息數據庫以及項目統計數據庫都部署在數據庫服務器上，為其他節點提供數據內容支持。<br>
</h3>

<h1>3.利用設計模式改進</h1>

<h2>3-1.消息通知模塊管理模塊的原設計方案類圖</h2>

![image](https://github.com/swordfishouo/staruml_finalexam/blob/main/18.jpg)

<h3>
【說明】<br>
1.精準扶貧管理系統的消息通知模塊主要包括用戶申請、用戶評論、用戶留言以及公告通知的管理。<br>
2.由於申請單、評論、留言和公告通知有共同的屬性，所以我們抽象出一個消息公告的抽象類，做為四者的父類，以供繼承。<br>
3.消息公告剛才類負責申請單、評論、留言以及公告通知的對象創建。<br>
</h3>

<h2>3-2.消息通知模塊管理模塊采用工廠方法模型設計方案類圖<br></h2>

<h3>
【說明】<br>
1.精準扶貧管理系統的消息通知模塊主要包括用戶申請、用戶評論、用戶留言以及公告通知的管理。<br>
2.申請單、評論、留言以及公告通知繼承於消息公告抽象類。<br>
3.分別創建留言工廠類、申請單工廠類、評論工廠類以及公告通知工廠類以實現對留言、申請單、評論以及公告通知的創建。<br>
4.創建消息公告工廠抽象類，以供留言工廠類、申請單工廠類、評論工廠類以及公告通知工廠類繼承。<br>
</h3>

<h2>3-3.設計模式改進前後對比分析<br></h2>

<h3>
在上例中可以看到，原模式最大的缺點是當有新產品要加入到系統中時，必須修改工廠類，加入必要的處理邏輯，這違背了“開閉原則”。在該模式中，所有的產品都是由同一個工廠創建，工廠類職責較重，業務邏輯較為覆雜，具體產品與工廠類之間的耦合度高，嚴重影響了系統的靈活性和擴展性，而工廠方法模式則可以很好地解決這一問題。<br>

工廠方法模式又稱為工廠模式，它屬於類創建型模式。在工廠方法模式中，工廠父類負責定義創建產品對象的公共接口，而工廠子類則負責生成具體的產品對象，這樣做的目的是將產品類的實例化操作延遲到工廠子類中完成，即通過工廠子類來確定究竟應該實例化哪一個具體產品類。<br>

在工廠方法模式中，抽象的的消息公告工廠類不再負責所有的消息公告的創建，而是將具體創建工作交給子類去做。這個抽象類僅僅負責給出具體工廠必須實現的接口，而不負責哪一個消息公告類被實例化這種細節，這使得工廠方法模式可以允許系統在不修改工廠角色的情況下引進新消息公告類型。<br>
</h3>

<h1>4.總結<br></h1>

<h2>4-1.內容總結<br></h2>

<h3>
本次課程設計利用"4+1"視圖建模方法進行“精準扶貧管理系統”的軟件架構設計。架構內容以及設計流程為精準扶貧管理系統內容描述、需求分析、場景視圖之用例圖設計建模、邏輯視圖之類圖設計建模、發開視圖設計建模、過程視圖之交互圖設計建模、物理視圖之部署圖設計建模。其中需求分析包括角色分析、系統需求分析以及系統公告了模塊圖三個部分；開發視圖設計建模包括包圖設計建模和組件圖設計建模。<br>

最有利用設計模式對設計進行改進。主要針對消息公告管理模塊來進行實現，利用工廠方法模式進行改進，並對兩種設計方法進行了對比分析。<br>
</h3>

<h2>4-2工作總結<br></h2>

<h3>
本次課程設計的完成主要依賴於軟件架構課程所學的相關知識，再加上適當的相關參考文獻的閱讀，才得以將整個軟件架構課程設計很好的完成。整個課程設計的過程中，除了對"4+1"視圖建模方法的具體使用以及對設計模式的理解，還非常考驗對整個軟件從需求的提出到整個架構建模實現的流程思路，和處理邏輯。<br>

根據提供的精準扶貧管理系統內容文檔，結合自己的理解，提煉出系統需求並設計出大概的功能模塊。在此基礎上按照"4+1"視圖建模方法的流程執行下來。其間可能會存在些許缺失或冗余的情況，不過重要的是在設計的過程中，加深了我對課堂所學知識的理解，通過實際的練習，熟練的掌握了整個軟件架構設計的思路、流程以及方法，收獲豐碩。<br>

總的來說，這次課程設計加深我對軟件系統架構基礎理論和基本知識的理解，掌握軟件系統架構設計的基本方法，達到進一步綜合運用所學知識和增強實際動手能力的目的。<br>
</h3>

<h2>資料來源 : https://www.cnblogs.com/joselynzhao/p/12850496.html</h2>
