
## Goals and motivation : 
Purpose of this repo is to implement whisper.cpp on my own in google colab and set it up for transcription and more use cases 

check  [Todo ](#todo) section for updates 

## Table of Contents: 
 - [Setting up and Transcribing Example Snippet](#setup)

## Setting up and simple transcription demo <a name='setup' ></a> 

**Run these commands to update packages**
```
!sudo apt update && sudo apt upgrade
```

**Install dependencies**


```
! sudo apt-get install g++ git yt-dlp make
```

**clone the whisper.cpp git repo**

```
!git clone https://github.com/ggerganov/whisper.cpp.git
```
**Name of models to download**

```
models=(

    "tiny.en"
    "tiny"
    "tiny-q5_1"
    "tiny.en-q5_1"
    "base.en"
    "base"
    "base-q5_1"
    "base.en-q5_1"
    "small.en"
    "small.en-tdrz"
    "small"
    "small-q5_1"
    "small.en-q5_1"
    "medium"
    "medium.en"
    "medium-q5_0"
    "medium.en-q5_0"
    "large-v1"
    "large"
    "large-q5_0"
)
```
## Download the desired model 

just put the ``tiny.en`` at the  end of model.sh to download the model

```
!bash ./models/download-ggml-model.sh tiny.en
```

**Expected  Output :**

 ```
 Downloading ggml model tiny.en from '[https://huggingface.co/ggerganov/whisper.cpp](https://huggingface.co/ggerganov/whisper.cpp)' ... ggml-tiny.en.bin 100%[===================>] 74.10M 22.0MB/s in 3.4s Done! Model 'tiny.en' saved in 'models/ggml-tiny.en.bin' 
 
 You can now use it like this: $ ./main -m models/ggml-tiny.en.bin -f samples/jfk.wav
```


**Make project using Make file**
```
!make
```
### Run the Demo
**There is a short demo called `jfk.wav` included  run this command to run the demo**

```
! ./main -m models/ggml-tiny.en.bin -f samples/jfk.wav
```

this will show the results like this  
```
whisper_init_from_file_no_state: loading model from 'models/ggml-tiny.en.bin'
whisper_model_load: loading model
whisper_model_load: n_vocab       = 51864
whisper_model_load: n_audio_ctx   = 1500
whisper_model_load: n_audio_state = 384
whisper_model_load: n_audio_head  = 6
whisper_model_load: n_audio_layer = 4
whisper_model_load: n_text_ctx    = 448
whisper_model_load: n_text_state  = 384
whisper_model_load: n_text_head   = 6
whisper_model_load: n_text_layer  = 4
whisper_model_load: n_mels        = 80
whisper_model_load: ftype         = 1
whisper_model_load: qntvr         = 0
whisper_model_load: type          = 1
whisper_model_load: adding 1607 extra tokens
whisper_model_load: model ctx     =   73.62 MB
whisper_model_load: model size    =   73.54 MB
whisper_init_state: kv self size  =    2.62 MB
whisper_init_state: kv cross size =    8.79 MB
whisper_init_state: compute buffer (conv)   =   11.17 MB
whisper_init_state: compute buffer (encode) =   61.76 MB
whisper_init_state: compute buffer (cross)  =    3.67 MB
whisper_init_state: compute buffer (decode) =   18.82 MB

system_info: n_threads = 2 / 2 | AVX = 1 | AVX2 = 1 | AVX512 = 0 | FMA = 1 | NEON = 0 | ARM_FMA = 0 | METAL = 0 | F16C = 1 | FP16_VA = 0 | WASM_SIMD = 0 | BLAS = 0 | SSE3 = 1 | SSSE3 = 1 | VSX = 0 | COREML = 0 | OPENVINO = 0 | 

main: processing 'samples/jfk.wav' (176000 samples, 11.0 sec), 2 threads, 1 processors, lang = en, task = transcribe, timestamps = 1 ...


[00:00:00.000 --> 00:00:08.000]   And so my fellow Americans ask not what your country can do for you
[00:00:08.000 --> 00:00:11.000]   ask what you can do for your country.


whisper_print_timings:     load time =   124.87 ms
whisper_print_timings:     fallbacks =   0 p /   0 h
whisper_print_timings:      mel time =    56.78 ms
whisper_print_timings:   sample time =    25.48 ms /    27 runs (    0.94 ms per run)
whisper_print_timings:   encode time =  2806.82 ms /     1 runs ( 2806.82 ms per run)
whisper_print_timings:   decode time =   205.30 ms /    27 runs (    7.60 ms per run)
whisper_print_timings:   prompt time =     0.00 ms /     1 runs (    0.00 ms per run)
whisper_print_timings:    total time =  3290.42 ms


```







#### Links : 

[Whisper.cpp Repository](https://github.com/ggerganov/whisper.cpp)

# TODO: <a name = 'todo'></a>
- transcribe any video from youtube
