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
ms.openlocfilehash: df7ca6ddbb80c21397beb91b8e671f248f2a1d9c
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2018
ms.locfileid: "51326293"
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