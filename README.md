# KoGPT2-finetuning(한국어 자연어 처리 모델 미세조정)
### 산합협력프로젝트(2020.04~2020.08)

-----------
### description
  - SKT-AI에서 한국어 데이터를 Pre-Training 시킨 KoGPT2를 fine tuning하여 문체 바꾸기
  - __GPT(Generative Pre-Training)__: OpenAI사가 만든 딥러닝 기반 언어 모델. 최근 3세대 언어 예측 모델인 GPT-3까지 공개됨.
    - __KoGPT2__: 위의 한국어 version. SKT AI팀에서 GPT-2모델을 이용하여 개선한 모델임.
  - __fine tuning__: 기존에 학습되어져있는 모델을 기반으로 아키텍쳐를 새로운 목적에 맞게 변형하고 이미 학습된 모델 weights로부터 학습을 업데이트하는 방법. 쉽게 말해서 추가의 데이터와 함께 파라미터를 미세하게 조정하여 업데이트하는 것을 말함.

----------
### how to install
  ```sh
git clone https://github.com/sohyeon98720/KoGPT2-finetuning.git
cd KoGPT2-finetuning
pip install -r requirements.txt
pip install .
```
or <br>

  `zip파일 다운로드 후 pip과정부터 수행`

----------

### Fine tuning
  `python main.py --epoch=200 --data_file_path=.train.csv --save_path=./checkpoint/ --load_path=./checkpoint/KoGPT2_checkpoint_80000.tar --batch_size=1`
  
----------
### generator
  `python generator.py --temperature=1.0 --text_size=1000 --tmp_sent="우리"` <br>
  *temp_sent="우리"는 예시. 이곳에 원하는 단어 입력*
  
----------

### input data structure
  |score|genre|sent|
  |:---:|:---:|:---:|
  |100|소설|...|
  
---------

### output example(generator)

내가 항상 -> 내가 항상 행복하고 즐거운 일을 하는 것은 아니지만 오늘 하루도 잘 마무리해본다</s>

----------

### reference 
  - [KoGPT2](https://github.com/SKT-AI/KoGPT2)
  - [KoGPT2-finetuning-가사데이터학습](https://github.com/gyunggyung/KoGPT2-FineTuning)
