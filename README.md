# ONNXSTREAM-ANDROID-TERMUX
This is an easy to follow guide to install sdxl on 500mb ram device you can run this on 2gb, 1gb ram devices like Nvidia shield tablet







WARNING IT TAKES AN HOUR TO INSTALL XNNPACK PLEASE BE PATIENT ITS WORTH THE WAIT!





pkg updated && pkg upgrade -y && termux-setup-storage &&
pkg install wget -y && pkg install git -y && pkg install proot -y &&
cd ~ && git clone https://github.com/MFDGaming/ubuntu-in-termux.git && cd ubuntu-in-termux && chmod +x ubuntu.sh && ./ubuntu.sh -y && ./startubuntu.sh 
__________________________________________________________________

apt update && apt upgrade

apt install python3 python3-pip git git-lfs wget nano cmake

install XNNPACK in ubuntu first then move it to home folder with, mv XNNPACK /home/

git clone https://github.com/google/XNNPACK.git

cd XNNPACK 

git checkout 579de32260742a24166ecd13213d2e60af862675

mkdir build

cd build

cmake -DXNNPACK_BUILD_TESTS=OFF -DXNNPACK_BUILD_BENCHMARKS=OFF ..

cmake --build . --config Release

install OnnxStream in ubuntu first then move it to home folder with, mv OnnxStream /home/

git clone https://github.com/vitoplantamura/OnnxStream.git

cd OnnxStream

cd src

mkdir build

cd build

[CHANGE MAX SPEED TO OFF FOR OLDER PHONES IDK IF IT WILL WORK FOR YOUR PHONE IT USES MORE MEMORY SO U NEED 12GB RAM TO USE MAX SPEED IF U GOT 8GB OR LOWER RAM MAKE SURE YOU CHANGE MAX SPEED TO OFF BEFORE PASTEING COMMANDS]both commands are together copy both and paste in termux as one command 

cmake -DMAX_SPEED=ON-DOS_LLM=OFF-DOS_CUDA=OFF -DXNNPACK_DIR=/home/XNNPACK ..

cmake --build . --config Release



DOWNLOAD XL MODELS 

git clone --depth=1 https://huggingface.co/AeroX2/stable-diffusion-xl-turbo-1.0-onnxstream


git clone --depth=1 https://huggingface.co/vitoplantamura/stable-diffusion-xl-base-1.0-onnxstream

I renamed the directory to SDXL-TURBO with the mv command, but keep it in sync with the-models-path parameter(see below).

cd ubuntu-in-termux && ./startubuntu.sh &&
cd /home/OnnxStream/src/build



SDXL TURBO EXECUTE

./sd --models-path /home/SDXL-TURBO --turbo --steps 4 --not-tiled --prompt "Cute Cat"

SDXL 1.0 EXECUTE

./sd --models-path /home/SDXL10 --xl --steps --not-tiled --prompt "pretty womzn mid 20s,volumetric lighting" --neg-prompt " ((bad art)), ((extra limbs)), blurry, (((duplicate))), ((mutilated)), extra fingers, mutated hands, ((poorly drawn hands)), ((poorly drawn face)), (((deformed))), (((bad proportions))), ((extra limbs)), (((disfigured))), (out of frame), ugly, extra limbs, (malformed limbs), ((missing arms)), ((missing legs)), (((extra arms))), (((extra legs))), mutated hands, (fused fingers), (too many fingers), (((long neck))), ugly, poorly drawn hands, poorly drawn feet, poorly drawn face, out of frame, extra limbs, extra legs, extra arms, cross-eye, body out of frame, (badhands5), text, logo, signature. Tattoos. Shoulder stripes bra without tits part. Big boobs. Operated bust. Cat ears."



Move png to Download folder

mv result.png /sdcard/Download/


