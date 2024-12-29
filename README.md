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

<h2>

<h3>
軟件架構常用模型就是視圖模型，類似於RM-ODP的視點模型，可以從多個角度描述一個覆雜的軟件系統。最流行的視圖模型就是"4+1"視圖模型，它由五個視圖組成，包括場景視圖、邏輯視圖、進程視圖、物理視圖和開發視圖，如圖1-1所示。我們可以粗略地把"4+1"視圖模型看作是參照軟件生命周期五個階段建立的視圖模型，雖然實際上每個視圖描述的內容並不是局限於生命周期的一個階段，但顯而易見的是，除了結構要素之外，這種視圖模型也包含了流程要素。
</h3>

![image](https://github.com/swordfishouo/staruml_finalexam/blob/main/aHR0cDovL2ltZy5ibG9nLmNzZG4ubmV0LzIwMTcwNTA3MTcyMDM2NTUz.jpg)

<h3>
"4+1"視圖模型實際上使得有不同需求的人員能夠得到他們對於軟件體系結構想要了解的東西。系統工程師先從物理視圖，然後從過程視圖靠近體系結構。最終使用者、客戶、數據專家從邏輯視圖看體系結構；項目經理、軟件配置人員從開發視圖看體系結構。<br>

邏輯視圖也稱概念視圖，主要是支持系統功能需求的抽象描述，即系統最終將提供給用戶什麽樣的服務。邏輯視圖關注的是系統必須為用戶提供的功能，不僅包括用戶可見的功能，還包括為實現用戶功能而必須提供的系統功能。在UML中，邏輯視圖包含了類、接口和協作，它展現了系統的靜態或結構組成及特征，描述場景視圖提出的系統功能的實現。邏輯視圖在UML中通常表現為類圖、交互圖、順序圖和狀態圖。<br>

開發視圖也稱模塊視圖，主要側重於描述系統的組織，與邏輯視圖密切相關，都描述了系統的靜態結構。開發視圖關注的是程序包，不僅包括要編寫的源程序，還包括可以直接使用的第三份SDK和現成框架、類庫，以及開發的系統將運行於其上的系統軟件或中間件等。開發視圖關注軟件開發環境下實際模塊的組織，反映了開發難度、軟件管理、重用性和通用性及由工具集、編程語言所帶來的限制和約束等。開發視圖和邏輯視圖之間可能存在一定的映射關系。開發視圖在UML中通常表現為包圖。<br>

過程視圖主要側重於描述系統的動態行為，即系統運行時所表現出來的相關特性，著重解決系統的可靠性、吞吐量、並發性、分布性和容錯性。過程視圖的關注點是運行中的線程、進程和對象等概念，以及相關的並發、同步、通信等問題。過程視圖和開發視圖相比，開發視圖一般偏重程序包在編譯時的靜態依賴關系，而這些程序運行起來之後就會表現為對象、線程、進程以及它們之間的調用關系，過程視圖比較關心的正式這些運行時單元的交互問題。過程視圖在UML中通常表現為活動圖、交互圖和狀態圖。<br>

物理視圖描述如何把系統軟件元素映射到硬件上，通常要考慮系統的性能、規模和容錯等問題，展示了所需要的物理環境、硬件配置和分布狀況。物理視圖關注的是目標程序及其依賴的運行庫和系統軟件最終如何安裝和部署到物理機器上，以及如何部署機器和網絡來配置軟件系統的可靠性、可伸縮性等要求。物理視圖和過程視圖相比，過程視圖特別關注目標程序的動態執行情況，而物理視圖重視目標程序的靜態位置問題；物理視圖是綜合考慮軟件系統和整個IT系統相互影響的架構視圖。物理視圖在UML中通常表現為部署圖。<br>
</h3>
