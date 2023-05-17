# Memories van overgave van gouverneurs van Ambon in de 17e en 18e eeuw	

## Download jpg files
The digitized book is available here: <https://resources.huygens.knaw.nl/retroboeken/memories_ambon/>

```bash
for i in {001..506}
do
    wget "https://resources.huygens.knaw.nl/retroapp/service_memories_ambon/memories_ambon_ks62/images/memories_ambon_ks62_${i}.jpg?size=1500x"
done
```

## OCR

Using [Tesseract](https://tesseract-ocr.github.io/) version 5.3.1

```bash
$ tesseract --version
tesseract 5.3.1
 leptonica-1.82.0
  libgif 5.2.1 : libjpeg 8d (libjpeg-turbo 2.1.5.1) : libpng 1.6.39 : libtiff 4.5.0 : zlib 1.2.11 : libwebp 1.3.0 : libopenjp2 2.5.0
 Found SSE4.1
 Found libarchive 3.6.2 zlib/1.2.11 liblzma/5.4.1 bz2lib/1.0.8 liblz4/1.9.4 libzstd/1.5.4
 Found libcurl/7.87.0 SecureTransport (LibreSSL/3.3.6) zlib/1.2.11 nghttp2/1.51.0
```

## TXT

```bash
mkdir txt

for f in *.jpg; do
  output_file="txt/$(basename "${f%.jpg}")"
  tesseract "$f" "$output_file" \
  -l nld \
  -c tessedit_char_whitelist="\"-()'’.,1234567890ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz ;:" \
  -c preserve_interword_spaces=1;
done
```

## Notes on use
* contains footnotes in modern Dutch
* contains summaries in modern Dutch, which appear between brackets '()'


 
