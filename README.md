# Sadtalker-Mooc
## 配置linux环境
conda create -n sadtalker python=3.8

conda activate sadtalker

pip install torch==1.12.1+cu113 torchvision==0.13.1+cu113 torchaudio==0.12.1 --extra-index-url https://download.pytorch.org/whl/cu113

conda install ffmpeg

pip install -r requirements.txt

## 下载模型
bash scripts/download_models.sh

## 生成数字人（更具体的参数移步https://github.com/OpenTalker/SadTalker）
python inference.py --driven_audio <audio.wav> \
                    --source_image <video.mp4 or picture.png> \
                    --result_dir <a file to store results> \
                    --enhancer gfpgan \（此选项为面部增强，提升效果但会显著减慢速度）
                    --preprocess full \（全身）
                    
## ppt
### 提取ppt中的图片
python pre_ppt.py --pdf_file <path_to_pdf> --save_file <save_path>

### 将ppt嵌入视频中并实现随语音的自动切换
pyhton main.py --video_file <video.mp4> --save_name <> --image_file <the path to the ppt images> --excel_file <the file to the word.xlsx>

### excel要求（包含每页的文本内容 第一行为页码 数字人对应语言内容 下面行填写即可）


## TO-DO
### 1.接入TTS语音模块,实现全部流程自动化 （）
### 2.接入whisper语音识别模块，添加mooc视频字幕（）
