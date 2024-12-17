# ImageUtils
Classe utilitária para imagens

---

- [Functions](#functions)
  - [createQRCode](#createqrcodetext-size-margin--1)
  - [createQRCode](#createqrcodeinput)


# Functions 
### createQRCode(text, size, margin = 1)
Gera uma imagem QRCode em base64. Pode gerar Exception

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input.text` | _String_ | Texto do qrcode |
| `input.size` | _Number_ | Largura/altura (em pixels) do qrcode gerado. `9 ~ 1080` |
| `input.margin` | _Number (opcional)_ |  `Padrão: 1` |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _String_ | Imagem em base64 |


**Exemplo:**

```javascript
var r = h.img.createQRCode('Example', 128);
```

---


### createQRCode(input)
Gera uma imagem QRCode em base64. Pode gerar Exception

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input.text` | _String_ | Texto do qrcode |
| `input.size` | _Number_ | Largura/altura (em pixels) do qrcode gerado. `9 ~ 1080` |
| `input.margin` | _Number (opcional)_ |  `Padrão: 1` |
| `input.color` | _String (opcional)_ | Cor no formato hexadecimal `Padrão: FFFFFF` |
| `input.bg_color` | _String (opcional)_ | Cor no formato hexadecimal `Padrão: 000000` |
| `input.arc_round_border` | _String (opcional)_ | Tamanho do arco de canto do plano de fundo `Padrão: 0` |
| `input.error_correction_level` | _String (opcional)_ | `L` Low, 7%<br>`M` Medium, 15%<br>`Q` Quartile, 25%<br>`H` High, 30% `Padrão: M` |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _String_ | Imagem em base64 |


**Exemplo:**

```javascript
var r = h.img.createQRCode({
    text: 'Example',
    size: 128,
    color: '0000FF'
});
```

---
