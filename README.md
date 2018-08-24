# HSPICE_2order_opamp

1. Circuit

https://github.com/KuiLiangLin/HSPICE_2order_opamp/blob/master/Circuit.jpg

M3、M4為使M1、M2有固定電流比例的OP對，M1、M2為第一階放大器，M5為用M10偏壓的電流源，M6、M7為第二階放大器，其中密勒補償電容跨於M6的source與drain端。

2. Design Flow

設計SR>30V/us，Vip-Vin=1V~2V，unit-gain bandwidth>4MHz，phase margin>600，voltage gain>70dB。
V¬DD=3V，Cc=3pF，CL=10pF。

2.1 SR=min{I5/Cc , (I7-I5)/CL}= I5/Cc

2.2 SR=2π*GBW*Vout max

2.3 PM>600，gm6>10gm1，Vgs4=Vgs6

2.4 (W/L)7= (W/L)5*(I6/I5)

2.5 gain=gm1(ro2//ro4)gm6(ro6//ro7)

3. Result

未頻率補償

https://github.com/KuiLiangLin/HSPICE_2order_opamp/blob/master/Waveform.jpg

加入密勒電容 --> 使極點分離，進而使零點頻率的特徵維持久一點，故可使第二極點往更高頻移動，延緩相位變化。

https://github.com/KuiLiangLin/HSPICE_2order_opamp/blob/master/Waveform_CC.jpg

加入零點電阻 --> 使轉移函數的零點與極點相消，使相位曲線的下降幅度趨緩。

https://github.com/KuiLiangLin/HSPICE_2order_opamp/blob/master/Waveform_ZR.jpg

迴轉率 --> SR約為30v/us左右，與計算min{I5/Cc , (I7-I5)/CL}所得結果相同。

https://github.com/KuiLiangLin/HSPICE_2order_opamp/blob/master/Waveform_SR.jpg









