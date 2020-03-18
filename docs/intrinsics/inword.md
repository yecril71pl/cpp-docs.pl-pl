---
title: __inword
ms.date: 09/02/2019
f1_keywords:
- __inword_cpp
- __inword
helpviewer_keywords:
- in instruction
- __inword intrinsic
ms.assetid: 5c617edd-6709-40a1-aad2-40d5e39283c6
ms.openlocfilehash: 7daaf1abd5089716061f118e30e9534e5c5c18ee
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440977"
---
# <a name="__inword"></a>__inword

**Specyficzne dla firmy Microsoft**

Odczytuje dane z określonego portu przy użyciu instrukcji `in`.

## <a name="syntax"></a>Składnia

```C
unsigned short __inword(
   unsigned short Port
);
```

### <a name="parameters"></a>Parametry

\ *portów*
podczas Port, z którego ma zostać odczytany.

## <a name="return-value"></a>Wartość zwracana

Odczytywanie danych.

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`__inword`|x86, x64|

**Plik nagłówkowy** \<intrin. h >

## <a name="remarks"></a>Uwagi

Ta procedura jest dostępna tylko jako wewnętrzna.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)
