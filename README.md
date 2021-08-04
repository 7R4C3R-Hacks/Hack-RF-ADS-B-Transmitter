# HackRF ADS-B Transmitter

This repository contains "ADS-B Out" encoder for Tx-capable SDR hardware.

## Disclaimer
The source code is published for academic purpose only. Do not 

## Instructions - Mac
1. Install Hack-RF
```
$ brew install hackrf
```

2. Execute *ADSB_Encoder.py* script with `<ICAO>` `<Latitude>` `<Longitude>` `<Altitude>` arguments
```
$ python2.7 ADSB_Encoder.py  0xABCDEF 12.34 56.78 9999.0
```
3. Make the raw signal file aligned to 256K buffer size:
```
$ dd if=Samples.iq8s of=Samples_256K.iq8s bs=4k seek=63
```
4. Transmit the signal into air:
```
$ hackrf_transfer -t Samples_256K.iq8s -f 1090000000 -s 2000000 -x 10
```
