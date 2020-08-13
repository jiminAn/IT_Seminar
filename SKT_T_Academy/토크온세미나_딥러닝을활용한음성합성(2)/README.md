# 딥러닝을 활용한 음성합성(2) 2020.08.13 / 김형주 / SNU ECE | Human Interface lab

## Vocoder
### 1. 음성 신호의 기초
: 차세대 인터페이스로서의 음성 신호
- STT(speach to text) : 음성인식(음성신호를 텍스트로 변환하는 과정)
- TTS(Text to Speach) : 음성합성(주어진 텍스트로 음성신호로 바꾸는 과정)
- 음성향상 : 음성 신호에서 잡음을 제거하여 유용한 신호를 추출하는 과정
- 음성의 생성: 폐에서부터 생성 해 파동이 있는 음성이 입밖으로까지 나오는 과정

### 2. 디지털 신호 처리
- x : frequency | y : Amplitude
- Continuous VS Discrete : x축이 시간일 때 연속성/이산적(비연속성)으로 신호를 구분 가능
- Analog to digital conversion
- Smapling : 음성신호의 샘플링 + Quantization :신호크기를 양자화하여 연속적인 값을 특정 대푯값으로 설정하는 과정
- Nyquist sampling theorem : f(max) 로 제한되어 있는 연속시간신호는 샘플링 주파수를 2*f(max)보다만 크면 완벽하게 복원 가능 
- Aliasing : 피하는 방법 1) 샘플링 레이팅을 높인다 2) lower pass통과시킴
- 주파수 영역에서의 연속 시간 신호 해석 : 주기함수(Fourier series), 비주기함수(Fourier transform)
- DTFT(Discrete time Fourier Transform) : Diecrete time 을 Fourier Transform함
- DFT(Discrete Fourier Transform) : 특정 주기가 있다고 판단하여 n만큼 반복하여 다시 Fourier Transform 함 -> O(N^2) : x(k) 한번 하는데 n의 시간이 걸림 * 0~n-1번 반복
- FFT(Fast Fourier Transform) : DFT를 더 작은 단위의 모듈로 나누어 계산해 시간복잡도가 DFT보다 효율적으로 나옴 -> O(logN)
- STFT(Short Time Fourier Transform) : 발화를 음소단위로 쪼개어 사용 , overlapping + window를 사용하여 원본에 가깝게 추출

- Spectogram(스펙토그램) : Amplitude 를 기준으로 시각화한것( x: time , y: frequency, color : magnuitude of the frequency component)
- Mel Scale : 사람의 귀는 주파수 대역에 따라 민감도가 다름( 낮은 주파수일 수록 민감도가 더 높음) -> 낮은 주파수 부분을 높은 주파수보다 더 샘플링을 자주하는 것이 Mel scale
- Mel-Scale formula :( x axis : Hz, y axis : mel-scale ) 기울기가 점점 작아지는 log형태의 그래프로 표현됨
- Mel-Spectogram : 스펙토그램의 주파수 간격을 mel-scale로 재조정한 것

### 3. 보코더의 개념
: 통신을 위한 압축 기술로, 음성 파형이 아닌 매개변수를 보내, 수신 측에서 매개변수를 통해 원본음성을 합성
- 음성 합성이 이루어지는 과정: text -> end to end model -> Accoustic model -> Sound
- 딥러닝 음성합성 모델의 타깃: 음성신호(raw waveform)는 데이터의 차원이 커서 바로 사용하지 않고, Mel-Spectogram을 사용하여 음성합성을 진행함
- Griffin-Lim Algorithm : 옛날 방법이라 성능이 뛰어나진 않다
- Neural Vocoder : Mel 스펙토그램을 입력으로 받아 음성 신호를 생성하는 딥러닝 모델로 학습 시에서 1~2초로 짧게 짤라 사용하므로 메모리 사용의 부담을 줄일 수 있다

## Deep Generative Model
- Autogrssive model
-
