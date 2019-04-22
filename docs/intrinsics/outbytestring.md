---
title: __outbytestring
ms.date: 11/04/2016
f1_keywords:
- __outbytestring
helpviewer_keywords:
- rep outsb instruction
- __outbytestring intrinsic
- outsb instruction
ms.assetid: c9150661-9c18-427f-bae8-710bba6ed78c
ms.openlocfilehash: 41064dda6a1a0b9ad4c15f98c3f3081f08ef8db6
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59032196"
---
# <a name="outbytestring"></a>__outbytestring

**Microsoft Specific**

Generuje `rep outsb` instrukcji, która wysyła pierwszy `Count` bajtów danych wskazywanego przez `Buffer` port określony przez `Port`.

## <a name="syntax"></a>Składnia

```
void __outbytestring(
   unsigned short Port,
   unsigned char* Buffer,
   unsigned long Count
);
```

#### <a name="parameters"></a>Parametry

*Port*<br/>
[in] Port do wysyłania danych do.

*Bufor*<br/>
[in] Dane, które zostaną wysłane do określonego portu.

*Liczba*<br/>
[in] Liczba bajtów danych do wysłania.

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|
|---------------|------------------|
|`__outbytestring`|x86, x64|

**Plik nagłówkowy** \<intrin.h >

## <a name="remarks"></a>Uwagi

Ta procedura jest dostępna wyłącznie jako wewnętrzna.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)