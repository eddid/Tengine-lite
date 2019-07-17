# Tengine-lite
Tengine-lite is lighten version of Tengine for Cortex-M & RTOS, written in C.

## Supported Ops
* Convolution
* Pooling
* Fully-connected
* Relu
* Softmax

## Example
[Cortex-M-KWS](https://github.com/OAID/cortex-m-kws) is an Keyword Spotting(KWS) demo on Cortex-M(STM32F7). It takes an quantized tensorflow model, converts it into .c and .h files, and runs the model with `Tengine-lite`. For more details, please visit this project [Cortex-M-KWS](https://github.com/OAID/cortex-m-kws).
