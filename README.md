# llama.cpp

Forked from [llama.cpp](https://github.com/ggerganov/llama.cpp) to run Llama2 inference inside of [Codesphere](https://codesphere.com).  

The CI pipeline is configured to fetch a pre-converted and quantized llama code instruct model from TheBloke from [huggingface](https://huggingface.co/TheBloke/CodeLlama-7B-Instruct-GGUF) and run the http server example, README with config options can be found in the /examples/server directory. 

## Run on CPU
If your workspace doesn't have a GPU update the CI pipeline as follows:

Stage 1: Prepare
  - name: Build Llama Cpp  
    command: `make clean && make -j`
  - name: Download model  
    command: `wget -P /home/user/app/models https://huggingface.co/TheBloke/CodeLlama-7B-Instruct-GGUF/resolve/main/codellama-7b-instruct.Q5_K_M.gguf`

Stage 3: Run
  - name: Run  
    command: `./server -m ./models/codellama-7b-instruct.Q5_K_M.gguf -c 2048 --port 3000 --host 0.0.0.0`