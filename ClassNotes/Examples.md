# Örnekler

---
### Veri Segmentinde Adresleme Örneği

**Verilen Değerler:**
- DS = 0700H
- Ofset = 0100H

a) Fiziksel Adres

b) Veri Segmentinin Alt Sınırı

c) Veri Segmentinin Üst Sınırı

d) Mantıksal Adres

---
>## Örnek Çözümü: 
### DS:0700h ve ofset adresi 0100h ise:

a) **Fiziksel Adres:**
- Segment adresini 1 byte sola kaydır (en az anlamlı hane olarak 0 ekleyerek) ve ofseti ekle.
    - DS: 0700H → 07000
    - Ofset: 0100H → +0100
    - Fiziksel Adres: 07000 + 0100 = 07100H

b) **Veri Segmentinin Alt Sınırı:**
- DS'nin değeri olan 0700H ile başlar: 07000

c) **Veri Segmentinin Üst Sınırı:**
- DS'nin değeri olan 0700H ile başlar ve ofsetin maksimum değeri olan FFFFH eklenir: 07000 + FFFF = 16FFF

d) **Mantıksal Adres:**
- DS:Offset → 0700:0100

---

## Assembly kodu kullanarak aşağıdaki toplamaları gerçekleştir

a. FCh + 28h

b. ‘0110 1100’ + ‘1011 1100’

c. 123 + 86

d. 434h + 8Ah

---
**Cevaplar:**
> ### a)  FCh + 28h
```assembly
org 100h        ; Bu bir direktiftir. Programın nerede başladığını tanımlar.
mov al, 0FCh    ; al kayıtçısına FCh'yi yükle
add al, 28h     ; al ile 28h'yi topla ve al kayıtçısına gönder
ret             ; Bu bir direktiftir. Programın nerede bittiğini tanımlar.

; Eğer bir onaltılık sayı harfle başlıyorsa, sıfır ile başlamalıdır.
; Onaltılık sayıları ayrıca 0x ile gösterilir.

; Yürütme sonrasında sonuç 24 ise, bu doğru mudur?
```
> ### b)  ‘0110 1100’ + ‘1011 1100’
```assembly
org 100h        ; Bu bir direktiftir. Programın nerede başladığını tanımlar.
mov al, 01101100b ; al kayıtçısına ikilik 01101100 değerini yükle
add al, 10111100b ; al ile ikilik 10111100'yi topla ve al kayıtçısına gönder
ret             ; Bu bir direktiftir. Programın nerede bittiğini tanımlar.

; Yürütme sonrasında sonuç 00101000 ise, bu doğru mudur?
```

> ### c)   123 + 86

```assembly
org 100h
mov al, 123
add al, 86
ret
```
> ### d) 434h + 8Ah

```assembly
org 100h        ; Bu bir direktiftir. Programın nerede başladığını tanımlar.
mov ax, 434h    ; ax kayıtçısına 434h değerini yükle
mov bx, 8Ah     ; bx kayıtçısına 8Ah değerini yükle
add ax, bx      ; ax kayıtçısına bx'yi ekleyerek topla
ret             ; Bu bir direktiftir. Programın nerede bittiğini tanımlar.
```

---
## Yürütme işleminden sonra "al" ve "bl" kayıtçılarının değerleri ne olur?

```assembly
org 100h        ; Bu bir direktiftir. Programın nerede başladığını tanımlar.
mov al, 45h     ; al kayıtçısına 45h değerini yükle
mov bl, 1Ah     ; bl kayıtçısına 1Ah değerini yükle
add al, bl      ; al kayıtçısına bl'yi ekleyerek topla
xchg al, bl     ; al ve bl kayıtçılarının değerlerini değiştir
ret             ; Bu bir direktiftir. Programın nerede bittiğini tanımlar.
```

**cevap:**
```assembly
org 100h
mov  al, 45h ; al = 45h
mov  bl, 1Ah ; bl = 1A
add  al, bl  ; al = al + bl = 5F
xchg al, bl  ; al = 1A,  bl = 5F
ret
```

