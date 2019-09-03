---
title: __readgsbyte, __readgsdword, __readgsqword, __readgsword
ms.date: 09/02/2019
f1_keywords:
- __readgsbyte
- __readgsdword
- __readgsqword
- __readgsword
helpviewer_keywords:
- __readgsword intrinsic
- __readgsdword intrinsic
- __readgsqword intrinsic
- __readgsbyte intrinsic
ms.assetid: f822632d-854c-4558-a71b-cdfc3eea2236
ms.openlocfilehash: 278f1de33a7e01c5893217ddd8aaa22e68cf0c94
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222348"
---
# <a name="__readgsbyte-__readgsdword-__readgsqword-__readgsword"></a>__readgsbyte, __readgsdword, __readgsqword, __readgsword

**Microsoft Specific**

Odczytaj pamięć z lokalizacji określonej przez przesunięcie względem początku segmentu GS.

## <a name="syntax"></a>Składnia

```C
unsigned char __readgsbyte(
   unsigned long Offset
);
unsigned short __readgsword(
   unsigned long Offset
);
unsigned long __readgsdword(
   unsigned long Offset
);
unsigned __int64 __readgsqword(
   unsigned long Offset
);
```

### <a name="parameters"></a>Parametry

*Przesunięcie*\
podczas Przesunięcie od początku `GS` , z którego ma zostać odczytane.

## <a name="return-value"></a>Wartość zwracana

Zawartość pamięci, słowo, podwójne słowo lub quadword (wskazywane przez nazwę funkcji o nazwie) w lokalizacji `GS:[Offset]`.

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`__readgsbyte`|X64|
|`__readgsdword`|X64|
|`__readgsqword`|X64|
|`__readgsword`|X64|

**Plik nagłówka** \<intrin. h >

## <a name="remarks"></a>Uwagi

Te procedury są dostępne tylko jako wewnętrznie.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[__writegsbyte, \__writegsdword, \__writegsqword, \__writegsword](../intrinsics/writegsbyte-writegsdword-writegsqword-writegsword.md)\
[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)
