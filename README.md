# gozxing A Barcode Scaning/Encoding Library for Go

[![Build Status](https://travis-ci.org/makiuchi-d/gozxing.svg?branch=master)](https://travis-ci.org/makiuchi-d/gozxing)
[![codecov](https://codecov.io/gh/makiuchi-d/gozxing/branch/master/graph/badge.svg)](https://codecov.io/gh/makiuchi-d/gozxing)

[ZXing](https://github.com/zxing/zxing) is an open-source, multi-format 1D/2D barcode image processing library for Java.
This project is a port of Zxing core library to pure Go.

## Porting Status (supported formats)

### 2D barcodes

| Format      | Scanning           | Encoding           |
|-------------|--------------------|--------------------|
| QR Code     | :heavy_check_mark: | :heavy_check_mark: |
| Data Matrix |                    |                    |
| Aztec       |                    |                    |
| PDF 417     |                    |                    |
| MaxiCode    |                    |                    |


### 1D product barcodes

| Format      | Scanning           | Encoding           |
|-------------|--------------------|--------------------|
| UPC-A       |                    |                    |
| UPC-E       |                    |                    |
| EAN-8       |                    |                    |
| EAN-13      |                    |                    |

### 1D industrial barcode

| Format       | Scanning           | Encoding           |
|--------------|--------------------|--------------------|
| Code 39      |                    |                    |
| Code 93      |                    |                    |
| Code 128     |                    |                    |
| Codabar      |                    |                    |
| ITF          |                    |                    |
| RSS-14       |                    |                    |
| RSS-Expanded |                    |                    |

## Usage Examples

### Scanning QR code

```Go
// open and decode image file
file, _ := os.Open("qrcode.jpg")
img, _, _ := image.Decode(file)

// prepare binary bitmap
src := gozxing.NewLuminanceSourceFromImage(img)
bmp, _ := gozxing.NewBinaryBitmap(common.NewHybridBinarizer(src))

// decode image
qrreader := qrcode.NewQRCodeReader()
result, _ := qrreader.Decode(bmp, nil)

fmt.Println(result)
```

