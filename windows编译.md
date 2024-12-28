# 编译facedetectyn.wasm:
tinygo build -o ../../build/facedetectyn.wasm -target=wasm-unknown .

# 编译Wasmvision.exe:
$env:CGO_LDFLAGS="-L${PWD}\opencv\build\install\x64\mingw\staticlib -lopencv_core4100 -lopencv_face4100 -lopencv_videoio4100 -lopencv_imgproc4100 -lopencv_highgui4100 -lopencv_imgcodecs4100 -lopencv_objdetect4100 -lopencv_features2d4100 -lopencv_video4100 -lopencv_dnn4100 -lopencv_xfeatures2d4100 -lopencv_plot4100 -lopencv_tracking4100 -lopencv_img_hash4100 -lopencv_calib3d4100 -lopencv_bgsegm4100 -lopencv_photo4100 -lopencv_aruco4100 -lopencv_wechat_qrcode4100 -lopencv_ximgproc4100 -lopencv_xphoto4100 -lopencv_flann4100 -static -lade -llibprotobuf -lIlmImf -llibpng -llibopenjp2 -llibwebp -llibtiff -llibjpeg-turbo -lzlib -lkernel32 -lgdi32 -lwinspool -lshell32 -lole32 -loleaut32 -luuid -lcomdlg32 -ladvapi32 -luser32
$env:CGO_CPPFLAGS="-I${PWD}\opencv\build\install\include"
$env:CGO_CXXFLAGS="--std=c++11"
$env:PATH="${PWD}/opencv/build/install/x64/mingw/bin;$env:PATH"
go build -tags customenv -o ./build/wasmvision.exe -buildvcs=false ./cmd/wasmvision