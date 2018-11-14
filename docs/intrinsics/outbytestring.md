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
ms.openlocfilehash: c5d99ee230780d1bfdcd104c1fcf3b3bd099fd6e
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2018
ms.locfileid: "51326927"
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

## <a name="see-also"></a>Zobacz też

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)