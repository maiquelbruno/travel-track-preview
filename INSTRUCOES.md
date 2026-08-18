# RV-10 — Landing atualizada

## 1. O que foi alterado

O `index.html` original foi preservado como base. Foram acrescentados:

- três botões de ação com o mesmo estilo visual do botão **Iniciar viagem**;
- botão **Galeria** com modal e grade de screenshots;
- faixa de miniaturas animada na página inicial;
- leitura automática das imagens da pasta pública `/gallery` do GitHub;
- contador e bandeiras dos países encontrados na rota publicada em `route.json`;
- botão **Pague um café** com Pix, PayPal e área de apoiadores;
- instrução para o apoiador enviar nome, estado e país.

## 2. Configurar o GitHub

No `index.html`, procure por:

`LANDING_CONFIG`

Preencha:

- `gallery.apiUrl`: `https://api.github.com/repos/SEU_USUARIO/SEU_REPOSITORIO/contents/gallery`
- `gallery.webUrl`: endereço normal da pasta `/gallery` no GitHub.

O repositório precisa estar público para que a página possa listar as imagens sem autenticação.

## 3. Colocar screenshots

Use a pasta `/gallery` deste pacote e faça commit das imagens nela.

Exemplo:

```
gallery/
  README.md
  etapa-01.webp
  etapa-02.webp
  etapa-03.webp
  pouso-miami.webp
```

## 4. Pix

No `LANDING_CONFIG.donation`:

- `pixPayload`: coloque o Pix Copia e Cola completo;
- `pixKey`: coloque a chave que será exibida como texto.

O QR Code é gerado no navegador usando QRCode.js. A página não precisa enviar o Pix para um serviço externo para gerar o QR.

## 5. PayPal

Em `paypalUrl`, coloque o link público da sua página de contribuição do PayPal.

## 6. Apoiadores

Depois de receber uma contribuição, acrescente manualmente:

```
{ name: 'Nome da pessoa', location: 'CE · Brasil' }
```

A página exibirá o nome e a localização informada.

## 7. Converter screenshots para WebP

Com ImageMagick:

```
magick screenshot.png -resize "1920x1920>" -strip -quality 80 screenshot.webp
```

Para uma miniatura independente:

```
magick screenshot.png -resize "480x480>" -strip -quality 72 screenshot-thumb.webp
```

Para o site, normalmente basta publicar somente a versão WebP de aproximadamente 1920 px.

## 8. Onde instalar

Substitua o `index.html` atual do seu projeto por este arquivo.

Mantenha os arquivos que já existem no seu projeto, especialmente os assets usados pelo original, como `rv10-capa.webp`, `rv10-earth.png` e `route.json`.
