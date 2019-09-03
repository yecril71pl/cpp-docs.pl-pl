---
title: __stosq
ms.date: 09/02/2019
f1_keywords:
- __stosq
helpviewer_keywords:
- rep stosq instruction
- stosq instruction
- __stosq intrinsic
ms.assetid: 3ea28297-4369-4c2d-bf0c-91fa539ce209
ms.openlocfilehash: 8b347d595da4cdbf1fefb6244940e262981671e9
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219952"
---
# <a name="__stosq"></a>__stosq

**Microsoft Specific**

Generuje instrukcję ciągu magazynu (`rep stosq`).

## <a name="syntax"></a>Składnia

```C
void __stosb(
   unsigned __int64* Destination,
   unsigned __int64 Data,
   size_t Count
);
```

### <a name="parameters"></a>Parametry

*Punktu*\
określoną Miejsce docelowe operacji.

*Data*\
podczas Dane do zapisania.

*Liczbą*\
podczas Długość bloku quadwords do zapisania.

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`__stosq`|AMD64|

**Plik nagłówka** \<intrin. h >

## <a name="remarks"></a>Uwagi

Wynik polega na tym, że *dane* quadword są zapisywane w bloku *Count* quadwords w ciągu *docelowym* .

Ta procedura jest dostępna tylko jako wewnętrzna.

## <a name="example"></a>Przykład

```C
// stosq.c
// processor: x64
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(__stosq)

int main()
{
   unsigned __int64 val = 0xFFFFFFFFFFFFI64;
   unsigned __int64 a[10];
   memset(a, 0, sizeof(a));
   __stosq(a+1, val, 2);
   printf("%I64x %I64x %I64x %I64x", a[0], a[1], a[2], a[3]);
}
```

```Output
0 ffffffffffff ffffffffffff 0
```

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)
