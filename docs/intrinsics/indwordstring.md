---
title: __indwordstring
ms.date: 09/02/2019
f1_keywords:
- __indwordstring
- __indwordstring_cpp
helpviewer_keywords:
- __indwordstring intrinsic
- rep insd instruction
ms.assetid: 96a1cf33-f691-4916-99e4-fa849b61e3a9
ms.openlocfilehash: b0b160ba00b1c0b7aa6bffc913e4cb56d503c2ff
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217834"
---
# <a name="__indwordstring"></a>__indwordstring

**Microsoft Specific**

Odczytuje dane z określonego portu przy użyciu `rep insd` instrukcji.

## <a name="syntax"></a>Składnia

```C
void __indwordstring(
   unsigned short Port,
   unsigned long* Buffer,
   unsigned long Count
);
```

### <a name="parameters"></a>Parametry

*Przewożąc*\
podczas Port, z którego ma zostać odczytany.

*Buforu*\
określoną Dane odczytane z portu są zapisywane w tym miejscu.

*Liczbą*\
podczas Liczba bajtów danych do odczytania.

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`__indwordstring`|x86, x64|

**Plik nagłówka** \<intrin. h >

## <a name="remarks"></a>Uwagi

Ta procedura jest dostępna tylko jako wewnętrzna.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)
