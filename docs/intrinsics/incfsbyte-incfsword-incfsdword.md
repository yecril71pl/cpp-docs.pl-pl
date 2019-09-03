---
title: __incfsbyte, __incfsword, __incfsdword
ms.date: 09/02/2019
f1_keywords:
- __incfsword
- __incfsbyte_cpp
- __incfsbyte
- __incfsdword
- __incfsword_cpp
- __incfsdword_cpp
helpviewer_keywords:
- __incfsword intrinsic
- __incfsdword intrinsic
- __incfsbyte intrinsic
ms.assetid: 820457fb-e35e-42d3-bcb6-725da3281c64
ms.openlocfilehash: 43824829043304f5762d049b5c75a72b57e2102c
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222128"
---
# <a name="__incfsbyte-__incfsword-__incfsdword"></a>__incfsbyte, __incfsword, __incfsdword

**Microsoft Specific**

Dodaj jeden do wartości w lokalizacji pamięci określonej przez przesunięcie względem początku `FS` segmentu.

## <a name="syntax"></a>Składnia

```C
void __incfsbyte(
   unsigned long Offset
);
void __incfsword(
   unsigned long Offset
);
void __incfsdword(
   unsigned long Offset
);
```

### <a name="parameters"></a>Parametry

*Przesunięcie*\
podczas Przesunięcie od początku `FS`.

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`__incfsbyte`|x86|
|`__incfsword`|x86|
|`__incfsdword`|x86|

**Plik nagłówka** \<intrin. h >

## <a name="remarks"></a>Uwagi

Te elementy wewnętrzne są dostępne tylko w trybie jądra, a procedury są dostępne tylko jako elementy wewnętrzne.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[\__addfsbyte, \__addfsword, \__addfsdword](../intrinsics/addfsbyte-addfsword-addfsdword.md)\
[\__readfsbyte, \__readfsdword, \__readfsqword, \__readfsword](../intrinsics/readfsbyte-readfsdword-readfsqword-readfsword.md)\
[\__writefsbyte, \__writefsdword, \__writefsqword, \__writefsword](../intrinsics/writefsbyte-writefsdword-writefsqword-writefsword.md)\
[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)
