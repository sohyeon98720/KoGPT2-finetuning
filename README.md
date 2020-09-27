# KoGPT2-finetuning(한국어 자연어 처리 모델 미세조정)
### 2020.04~2020.08

-----------
### description
  - SKT-AI에서 한국어 데이터를 Pre-Training 시킨 KoGPT2를 fine tuning하여 문체 바꾸기
  - __GPT__:
    - __KoGPT__:
  - __fine tuning__:

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
  `python main.py --epoch=200 --data_file_path=.train.csv --save_path=./checkpoint/ --load_path=./checkpoint/KoGPT2_checkpoint_40000.tar --batch_size=1`
  
----------
### generator
  `python generator.py --temperature=1.0 --text_size=1000 --tmp_sent="우리"` <br>
  temp_sent="우리"는 예시. 이곳에 원하는 단어 입력
  
----------

### input data structure
  |weight|genre|sent|
  |:---:|:---:|:---:|
  |100|소설|...|
  
  
---------

### output example

----------

### reference 
  - [KoGPT2](https://github.com/SKT-AI/KoGPT2)
  - [KoGPT2-finetuning-가사데이터학습](https://github.com/gyunggyung/KoGPT2-FineTuning)
