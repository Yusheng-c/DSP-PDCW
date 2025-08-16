# DSP-PDCW
DSP课设项目开源

## 主要内容
Signal separation task for robust speech recognition: DSP implementation

-> 针对鲁棒语音识别的信号分离任务：DSP实现

---
实现 TMS320F28335 + MATLAB APP DESIGNER 男女声源分离；

参考文献：Kim, C., Kumar, K., Raj, B., & Stern, R.M. (2012). Signal separation for robust speech recognition based on phase difference information obtained in the frequency domain. Interspeech.

---
F28335文件夹的rar压缩包即是芯片工程文件夹；PDCW文件夹是本项目，DSP2833x_Libraries文件夹是依赖的头文件等；

具体演示：
1. 首先，在上位机载入原始音频，并且获取其语谱图：
<img width="714" height="346" alt="image" src="https://github.com/user-attachments/assets/d003409c-2d38-47eb-9772-1439f1dabd10" />

2. 然后，再点击“Launch”按钮。此时，上位机将命令、参数信息，包括Gammatone channel weighting滤波器的系数均传输至DSP芯片，DSP芯片收到对应参数信息后进入串口接收中断，等待音频信息帧的到来。
<img width="818" height="503" alt="image" src="https://github.com/user-attachments/assets/b5c1412d-6938-4b04-a021-baffdfcca14e" />
<img width="789" height="452" alt="image" src="https://github.com/user-attachments/assets/5afdc665-e327-4924-ba2f-46523c92f49c" />

3. 从芯片接收其处理完整音频后，应该是这样的：
<img width="865" height="429" alt="image" src="https://github.com/user-attachments/assets/8a831a01-8f15-4efc-96fd-d6d85bf36f02" />

- 相较于原始音频，处理后的音频在低频区域滤除了大部分的信号，而从时域的角度看，某些时刻上的信号被抑制，但由于滤波器的平滑处理，整个结果并没有很好地体现这种抑制效果。事实上，在完成语音分离后，应该在原始音频的基础上，进一步对分离信号做增强处理，可以得到听觉上更优的人声分离效果。
