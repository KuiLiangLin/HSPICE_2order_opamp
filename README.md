# HSPICE_2order_opamp

<hr>

1. Circuit :

    M3、M4為使M1、M2有固定電流比例的OP對，M1、M2為第一階放大器，M5為用M10偏壓的電流源，M6、M7為第二階放大器，其中密勒補償電容跨於M6的source與drain端。
    
    <img src="https://raw.githubusercontent.com/KuiLiangLin/HSPICE_2order_opamp/master/Circuit.jpg" height="100%" width="100%" >
    
2. Design Flow:

   設計SR>30V/us，Vip-Vin=1V~2V，unit-gain bandwidth>4MHz，phase margin>600，voltage gain>70dB。
   VDD=3V，Cc=3pF，CL=10pF。

   2.1 SR=min{I5/Cc , (I7-I5)/CL}= I5/Cc

   2.2 SR=2π*GBW*Vout max

   2.3 PM>600，gm6>10gm1，Vgs4=Vgs6

   2.4 (W/L)7= (W/L)5*(I6/I5)

   2.5 gain=gm1(ro2//ro4)gm6(ro6//ro7)

3. Result:

   3.1 未頻率補償 --> 圖中有用白線標記0dB所對應的相位為188o，PM<0為不穩定系統，可能在相位等於180o之頻率點產生震盪現象。相位部分，1MHz附近稍為的抖動是因為經過零點相位會+90o/decade，但由於還未頻率補償，每個極點的位置很接近，故相位持續-90o　/decade。   
   
    <img src="https://raw.githubusercontent.com/KuiLiangLin/HSPICE_2order_opamp/master/Waveform.jpg" height="100%" width="100%" >

   3.2 加入密勒電容 --> 使極點分離，進而使零點頻率的特徵維持久一點，故可使第二極點往更高頻移動，延緩相位變化。圖中有用白線標記0dB所對應的相位為127o，PM=53o為穩定系統。   
   
    <img src="https://raw.githubusercontent.com/KuiLiangLin/HSPICE_2order_opamp/master/Waveform_CC.jpg" height="100%" width="100%" >

   3.3 加入零點電阻 --> 使轉移函數的零點與極點相消，使相位曲線的下降幅度趨緩。
   
    <img src="https://raw.githubusercontent.com/KuiLiangLin/HSPICE_2order_opamp/master/Waveform_ZR.jpg" height="100%" width="100%" >

   3.4 迴轉率 -->輸入步階函數並用暫態響應所得到的SR，右邊為局部放大，從圖可知SR約為30v/us左右，與計算min{I5/Cc , (I7-I5)/CL}所得結果相同。
   
    <img src="https://raw.githubusercontent.com/KuiLiangLin/HSPICE_2order_opamp/master/Waveform_SR.jpg" height="100%" width="100%" >

4. Conclusion:

   加入密勒電容補償穩定度是一個蠻有效的方法，在一開始沒加密勒補償電容的相位與增益圖中可看到此二階OP電路的系統屬於不穩定系統，在加入密勒補償電容之後可看出第一極點從100kHz移動到1kHz，且第二極點從10MHz移動到100MHz，並使phase margin從-8o提升到60o。

   加入零點電阻並適當選擇電阻值使第二極點與零點電阻產生的零點相消，在加入零點電阻後由於第二極點被相消，故相位在-90o持續距離比較長，進而提高系統的phase margin與穩定度。

<hr>
<p> END </p>
<p> Codes are <em><a href="https://github.com/KuiLiangLin/HSPICE_2order_opamp/">Here</a></em>. </p>
<p> You can return <em><a href="https://kuilianglin.github.io/Welcome/">My Main Page</a></em>. </P>
