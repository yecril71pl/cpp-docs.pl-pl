---
title: __readfsbyte, __readfsdword, __readfsqword, __readfsword
ms.date: 09/02/2019
f1_keywords:
- __readfsword
- __readfsdword
- __readfsbyte
- __readfsqword
helpviewer_keywords:
- __readfsword intrinsic
- readfsword intrinsic
- __readfsdword intrinsic
- readfsbyte intrinsic
- __readfsbyte intrinsic
- readfsdword intrinsic
- readfsqword intrinsic
- __readfsqword intrinsic
ms.assetid: f6ee7203-4179-402c-a464-0746c84ce6ac
ms.openlocfilehash: 30040b33fe8c686bc0cda585c525ae2926cdf314
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222364"
---
# <a name="__readfsbyte-__readfsdword-__readfsqword-__readfsword"></a>__readfsbyte, __readfsdword, __readfsqword, __readfsword

**Microsoft Specific**

Odczytaj pamięć z lokalizacji określonej przez przesunięcie względem początku segmentu FS.

## <a name="syntax"></a>Składnia

```C
unsigned char __readfsbyte(
   unsigned long Offset
);
unsigned short __readfsword(
   unsigned long Offset
);
unsigned long __readfsdword(
   unsigned long Offset
);
unsigned __int64 __readfsqword(
   unsigned long Offset
);
```

### <a name="parameters"></a>Parametry

*Przesunięcie*\
podczas Przesunięcie od początku `FS` , z którego ma zostać odczytane.

## <a name="return-value"></a>Wartość zwracana

Zawartość pamięci w bajtach, Word, DoubleWord lub quadword (wskazywanym przez nazwę funkcji o nazwie) w lokalizacji `FS:[Offset]`.

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`__readfsbyte`|x86|
|`__readfsdword`|x86|
|`__readfsqword`|x86|
|`__readfsword`|x86|

**Plik nagłówka** \<intrin. h >

## <a name="remarks"></a>Uwagi

Te procedury są dostępne tylko jako elementy wewnętrzne.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[__writefsbyte, \__writefsdword, \__writefsqword, \__writefsword](../intrinsics/writefsbyte-writefsdword-writefsqword-writefsword.md)\
[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)
