---
title: __outwordstring
ms.date: 11/04/2016
f1_keywords:
- __outwordstring
helpviewer_keywords:
- rep outsw instruction
- __outwordstring intrinsic
- outsw instruction
ms.assetid: b470c7a0-1de9-4370-886a-b2c3a1f842f4
ms.openlocfilehash: 92ec21cdf7fb9d86ee7c8b9fa5090bbace2fe869
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50494617"
---
# <a name="outwordstring"></a>__outwordstring

**Microsoft Specific**

Generuje `rep outsw` instrukcji, która wysyła `Count` słów, zaczynając od `Buffer` z portu We/Wy, określony przez `Port`.

## <a name="syntax"></a>Składnia

```
void __outwordstring( 
   unsigned short Port, 
   unsigned short* Buffer, 
   unsigned long Count 
);
```

#### <a name="parameters"></a>Parametry

*Port*<br/>
[in] Port do wysyłania danych do.

*Bufor*<br/>
[in] Wskaźnik do danych, które zostaną wysłane do określonego portu.

*Liczba*<br/>
[in] Liczbę wyrazów do wysłania.

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|
|---------------|------------------|
|`__outwordstring`|x86, x64|

**Plik nagłówkowy** \<intrin.h >

## <a name="remarks"></a>Uwagi

Ta procedura jest dostępna wyłącznie jako wewnętrzna.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz też

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)