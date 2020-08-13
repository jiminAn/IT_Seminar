# 딥러닝을 활용한 음성합성(2) 2020.08.13 / 김형주 / SNU ECE | Human Interface lab

## Vocoder
1. 음성 신호의 기초
: 차세대 인터페이스로서의 음성 신호
- STT(speach to text) : 음성인식(음성신호를 텍스트로 변환하는 과정)
- TTS(Text to Speach) : 음성합성(주어진 텍스트로 음성신호로 바꾸는 과정)
- 음성향상 : 음성 신호에서 잡음을 제거하여 유용한 신호를 추출하는 과정
- 음성의 생성: 폐에서부터 생성 해 파동이 있는 음성이 입밖으로까지 나오는 과정

2. 디지털 신호 처리
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
- Mel-Scale formula : 


3. 보코더의 개념

## Deep Generative Model
- Autograssive model
