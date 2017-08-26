# libopus_for_esp32
Experiments to port libopus encode/decoder to esp32

Original sources by the authors of Opus: http://opus-codec.org

=================================================================================

First benchmark:
Encode Sample16kHz.raw (little-endian) data, 16 bit, stereo 16000 Hz 10 seconds
It's still missing the ogg part !!!!

1. Without CFLAGS:

9746146 microseconds

2. Without CFLAGS and FIXED_POINT:

8185269 microseconds

3. Without CFLAGS and release mode:

8970423 microseconds

So, the best option is (2): 1,22 realtime. 

=================================================================================

Second benchmark:
Encode Sample16kHz.raw (little-endian) data, 16 bit, stereo 16000 Hz 10 seconds, resampled 48KHz (mandatory for opus ????)
Using libopusenc from xiph and last idf framework (24/08/2017).

1. Without CFLAGS:

Total time in microseconds: 23622539 microseconds

So, great performance regression. :-(

=================================================================================

TODO:

- Encode something infinite to check memory leaks
- Profile to find the heaviest parts
- Investigate esp32 dsp features: Vectra LX DSP Engine, MAC16
- Streaming over tcp and http

=================================================================================
