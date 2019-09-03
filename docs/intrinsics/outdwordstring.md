---
title: __outdwordstring
ms.date: 09/02/2019
f1_keywords:
- __outdwordstring
helpviewer_keywords:
- outsd instruction
- __outdwordstring intrinsic
- rep outsd instruction
ms.assetid: 55b31a65-aab7-4b5c-b61d-d9e2fb0c497a
ms.openlocfilehash: 50908a65795af617f18a497c073cfefe009dfd80
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217164"
---
# <a name="__outdwordstring"></a>__outdwordstring

**Microsoft Specific**

Generuje instrukcję, która wysyła `Count` doublewords, rozpoczynając `Buffer` od portu we/wy określonego przez `Port`. `rep outsd`

## <a name="syntax"></a>Składnia

```C
void __outdwordstring(
   unsigned short Port,
   unsigned long* Buffer,
   unsigned long Count
);
```

### <a name="parameters"></a>Parametry

*Przewożąc*\
podczas Port, do którego mają zostać wysłane dane.

*Buforu*\
podczas Wskaźnik do danych, które mają zostać wysłane przez określony port.

*Liczbą*\
podczas Liczba doublewords do wysłania.

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`__outdwordstring`|x86, x64|

**Plik nagłówka** \<intrin. h >

## <a name="remarks"></a>Uwagi

Ta procedura jest dostępna tylko jako wewnętrzna.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)
