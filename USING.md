# Using wasmVision

```
NAME:
   wasmvision - wasmVision CLI

USAGE:
   wasmvision [global options] command [command options]

VERSION:
   0.1.0-pre4

COMMANDS:
   run       Run wasmVision processors
   download  Download computer vision models
   info      Show installation info
   version   Show version
   about     About wasmVision
   help, h   Shows a list of commands or help for one command

GLOBAL OPTIONS:
   --help, -h     show help
   --version, -v  print the version
```

These are some of the things you can do with wasmVision.

## `wasmvision run`

```shell
NAME:
   wasmvision run - Run wasmVision processors

USAGE:
   wasmvision run [command options]

OPTIONS:
   --source value, -s value                                     video capture source to use such as webcam or file (0 is the default webcam on most systems) (default: "0")
   --output value, -o value                                     output type (mjpeg, file) (default: "mjpeg")
   --destination value, -d value                                output destination (port, file path)
   --processor value, -p value [ --processor value, -p value ]  wasm module to use for processing frames. Format: -processor /path/processor1.wasm -processor /path2/processor2.wasm
   --logging                                                    log detailed info to console (default: true) (default: true)
   --models-dir value, --models value                           directory for model loading (default to $home/models) [$WASMVISION_MODELS_DIR]
   --model-download, --download                                 automatically download known models (default: true) (default: true)
   --help, -h                                                   show help                                                 show help
```

### Capture from your webcam (default), process the video, and stream the output using MJPEG to port 8080 (default)

```shell
wasmvision run -p /path/to/processors/mosaic.wasm
```

### Capture from a secondary webcam, process the video, and stream the output using MJPEG to port 8080 (default)

```shell
wasmvision run -s /dev/video2 -p /path/to/processors/mosaic.wasm
```

### Capture from your webcam (default), process the video using 2 processors chained together, and stream the output using MJPEG to port 8080 (default)

```shell
wasmvision run -p /path/to/processors/hello.wasm -p /path/to/processors/mosaic.wasm
```

### Capture from a file, process the video, and stream the output using MJPEG to port 6000

```shell
wasmvision run -s /path/to/video/filename.mp4 -p /path/to/processors/blur.wasm -o mjpeg -d :6000
```

### Capture from your webcam, process the video, and save the output to a file

```shell
wasmvision run -p /path/to/processors/mosaic.wasm -o file -d /path/to/video/filename.avi
```

## `wasmvision download`

```shell
NAME:
   wasmvision download - Download computer vision models

USAGE:
   wasmvision download [command options] [known-model-name]

OPTIONS:
   --models-dir value, --models value  directory for model loading (default to $home/models) [$WASMVISION_MODELS_DIR]
   --help, -h                          show help
```

### Download the `candy-9.onnx` model used for fast neural style transfer from the official ONNX repository to the default models directory on the local machine.

```shell
wasmvision download candy-9
```