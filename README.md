# KoGPT2-finetuning(한국어 자연어 처리 모델 미세조정)
### 산합협력프로젝트(2020.04~2020.08)

---------
visit [here](https://github.com/sohyeon98720/script_generation_kr) for more about text-generation and evaluation

-----------
### description
  - SKT-AI에서 한국어 데이터를 Pre-Training 시킨 KoGPT2를 fine tuning하여 문체 바꾸기
  - __GPT(Generative Pre-Training Transformer)__: OpenAI사가 만든 딥러닝 기반 언어 모델. 최근 3세대 언어 예측 모델인 GPT-3까지 공개됨.
    - __KoGPT2__: 위의 한국어 version. SKT AI팀에서 GPT-2 base모델을 이용하여 개선한 모델임.
  - __fine tuning__: 기존에 학습되어져있는 모델을 기반으로 아키텍쳐를 새로운 목적에 맞게 변형하고 이미 학습된 모델 weights로부터 학습을 업데이트하는 방법. 쉽게 말해서 추가의 데이터와 함께 파라미터를 미세하게 조정하여 업데이트하는 것을 말함. <br>
-> pre-trained model을 이용한 finetuning 전략

----------

### input data structure
  |score|genre|sent|
  |:---:|:---:|:---:|
  |100|소설|우리의 마음을...| <br>
  
  *이 코드에서 score, genre는 이용하지 않은 column이라 값을 모두 통일시킴*
  
---------

### how to install
  ```sh
git clone https://github.com/sohyeon98720/KoGPT2-finetuning.git
cd KoGPT2-finetuning
pip install -r requirements.txt
```
or <br>

  `zip파일 다운로드 후 pip과정부터 수행`

----------

### fine tuning
  `python main.py --epoch=200 --data_file_path=./train.csv --save_path=./checkpoint/ --load_path=./checkpoint/KoGPT2_checkpoint_80000.tar --batch_size=1` <br>
  *load_path는 존재하면 학습된 모델부터 train 시작 / 존재하지않으면 처음부터 train 시작*
  
----------
### fine tuning - output example
<img src="https://user-images.githubusercontent.com/47767202/96966111-3838b080-1548-11eb-8282-75e5e2c38d19.png" width="60%"><br>
`우리` -> `우리 집은 우리 친구들에게 따뜻한 손길을 줄 수 있는 곳입니다.</s>` <br>
*sent가 모두 통일되어있어 sent로 시작하는 문장만 generate하여 보여줌*<br>
*sent: generator의 tmp_sent와 역할이 같음*

----

### generator
  `python generator.py --temperature=1.0 --text_size=1000 --load_path=./checkpoint/KoGPT2_checkpoint_80000.tar --tmp_sent="내가 항상"` <br>
  *temp_sent="내가 항상"는 예시. 이곳에 원하는 단어 입력.*<br>
  *첫 문장만 tmp_sent로 시작되는 문장이 출력되고 이후로는 input을 바꿔 실행할 수 있음* <br>
  *temperature는 생성되는 글의 창의성을 조절*
  
  
----------

### generator - output example
<img src="https://user-images.githubusercontent.com/47767202/96966617-13910880-1549-11eb-86fd-fe840cb17aab.png" width="60%"> <br>
`내가 항상` -> `내가 항상 행복하고 즐거운 일을 하는 것은 아니지만 오늘 하루도 잘 마무리해본다</s>`

----------

### reference 
  - [KoGPT2](https://github.com/SKT-AI/KoGPT2)
  - [KoGPT2-finetuning-가사데이터학습](https://github.com/gyunggyung/KoGPT2-FineTuning)
