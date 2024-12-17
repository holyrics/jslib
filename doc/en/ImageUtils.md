# ImageUtils
Utility class for images

---

- [Functions](#functions)
  - [createQRCode](#createqrcodetext-size-margin--1)
  - [createQRCode](#createqrcodeinput)


# Functions 
### createQRCode(text, size, margin = 1)
Gera uma imagem QRCode em base64. May generate Exception

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.text` | _String_ | Texto do qrcode |
| `input.size` | _Number_ | Largura/altura (em pixels) do qrcode gerado. `9 ~ 1080` |
| `input.margin` | _Number (optional)_ |  `Default: 1` |


**Response:**

| Type  | Description |
| :---: | ------------|
| _String_ | Imagem em base64 |


**Example:**

```javascript
var r = h.img.createQRCode('Example', 128);
```

---


### createQRCode(input)
Gera uma imagem QRCode em base64. May generate Exception

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.text` | _String_ | Texto do qrcode |
| `input.size` | _Number_ | Largura/altura (em pixels) do qrcode gerado. `9 ~ 1080` |
| `input.margin` | _Number (optional)_ |  `Default: 1` |
| `input.color` | _String (optional)_ | Color in hexadecimal format `Default: FFFFFF` |
| `input.bg_color` | _String (optional)_ | Color in hexadecimal format `Default: 000000` |
| `input.arc_round_border` | _String (optional)_ | Tamanho do arco de canto do plano de fundo `Default: 0` |
| `input.error_correction_level` | _String (optional)_ | `L` Low, 7%<br>`M` Medium, 15%<br>`Q` Quartile, 25%<br>`H` High, 30% `Default: M` |


**Response:**

| Type  | Description |
| :---: | ------------|
| _String_ | Imagem em base64 |


**Example:**

```javascript
var r = h.img.createQRCode({
    text: 'Example',
    size: 128,
    color: '0000FF'
});
```

---
