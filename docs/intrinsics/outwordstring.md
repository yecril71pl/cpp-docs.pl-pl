---
title: __outwordstring
ms.date: 09/02/2019
f1_keywords:
- __outwordstring
helpviewer_keywords:
- rep outsw instruction
- __outwordstring intrinsic
- outsw instruction
ms.assetid: b470c7a0-1de9-4370-886a-b2c3a1f842f4
ms.openlocfilehash: 3cc5b0ae2101c86e3dc899b7924ec2524f0ea6e7
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217123"
---
# <a name="__outwordstring"></a>__outwordstring

**Microsoft Specific**

Generuje instrukcję, która wysyła słowa *Count* , zaczynając od *buforowania* portu we/wy określonego przez port. `rep outsw`

## <a name="syntax"></a>Składnia

```C
void __outwordstring(
   unsigned short Port,
   unsigned short* Buffer,
   unsigned long Count
);
```

### <a name="parameters"></a>Parametry

*Przewożąc*\
podczas Port, do którego mają zostać wysłane dane.

*Buforu*\
podczas Wskaźnik do danych, które mają zostać wysłane przez określony port.

*Liczbą*\
podczas Liczba słów do wysłania.

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`__outwordstring`|x86, x64|

**Plik nagłówka** \<intrin. h >

## <a name="remarks"></a>Uwagi

Ta procedura jest dostępna tylko jako wewnętrzna.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)
