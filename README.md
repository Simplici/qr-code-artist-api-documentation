# qr-code-artist-api-documentation
this documentation for qr code artist api at: https://market.mashape.com/best-apis/qr-code-artist .
## overview
this api allows to generate common qr-code, artistic qr-code (black & white or colorized), animated qr-code (black & white or colorized).
## examples
classic qr codes

![alt text](https://github.com/Simplici/qr-code-artist-api-documentation/blob/master/examples/classic-qr-codes.jpg?raw=true "classic qr codes")

artistic qr codes: black and white, with background image

![alt text](https://github.com/Simplici/qr-code-artist-api-documentation/blob/master/examples/b&w-image-qr-codes.jpg?raw=true "artistic qr codes: black and white, with background image")

artistic qr codes: colorized, with background image

![alt text](https://github.com/Simplici/qr-code-artist-api-documentation/blob/master/examples/coloried-image-qr-codes.jpg?raw=true "artistic qr codes: colorized, with background image")

artistic qr codes: black and white, animated, with background image

![alt text](https://github.com/Simplici/qr-code-artist-api-documentation/blob/master/examples/ainimated-ar-code-1.gif?raw=true "artistic qr codes: black and white, animated, with background image")![alt text](https://github.com/Simplici/qr-code-artist-api-documentation/blob/master/examples/animated-qr-code-2.gif?raw=true "artistic qr codes: black and white, animated, with background image")

artistic qr codes: colorized, animated, with background image

![alt text](https://github.com/Simplici/qr-code-artist-api-documentation/blob/master/examples/animated-qr-code-3.gif?raw=true "artistic qr codes: colorized, animated, with background image")![alt text](https://github.com/Simplici/qr-code-artist-api-documentation/blob/master/examples/ainimated-qr-code-4.gif?raw=true "artistic qr codes: colorized, animated, with background image")
## usage
this api supports only POST method.
in the request payload, there are following options:

- text: obligatory, the text content that will be encoded into the qr code.
	 > supported charactors: 0~9, a~z, A~Z, · , . : ; %2b - * / \ ~ ! @ # $ % ^ & ` ' = < > [ ] ( ) ? _ { } | and  (space)
- format: optional, qr code file format, one of 'jpg', 'png', 'bmp', 'gif'. by default 'png'
- size: optional, qr code size, 'low', 'medium', 'high', default 'medium'
	> in most of cases, use the default value is OK, use 'high' when the background image is complex and you it to be clear in the qr code.
- bg-picture-base64: optional, the picture to be used in qr code, in base64 format
	>if you use curl to send the request, you need to replace '+' in the base64 text by '%2b'
- bg-picture-format: optional (obligatory when bg-picture-base64 is present), backgroud picture format, supported original picture formats: 'jpg', 'png', 'bmp', 'gif'
- colorized: optional, whether the resulting picture colorlized, '1' represents yes, '0' represents no

below is an example of payload:
```
{
	'text': 'https://github.com',
	'format': 'png',
	'size': 'medium',
	'bg-picture-base64': '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',
	'bg-picture-format': 'png',
	'colorized': '1'
}
```
## tips
- Use a nearly square picture instead of a rectangle one.
- Don't use pictures with transparent background.