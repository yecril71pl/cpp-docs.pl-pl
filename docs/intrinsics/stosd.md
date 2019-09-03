---
title: __stosd
ms.date: 09/02/2019
f1_keywords:
- __stosd
helpviewer_keywords:
- stosd instruction
- rep stosd instruction
- __stosd intrinsic
ms.assetid: 03104247-1cea-49f6-b6f8-287917bf5680
ms.openlocfilehash: c46bb124390ff23d79361c66530493c48faf3f0a
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219979"
---
# <a name="__stosd"></a>__stosd

**Microsoft Specific**

Generuje instrukcję ciągu magazynu (`rep stosd`).

## <a name="syntax"></a>Składnia

```C
void __stosd(
   unsigned long* Destination,
   unsigned long Data,
   size_t Count
);
```

### <a name="parameters"></a>Parametry

*Punktu*\
określoną Miejsce docelowe operacji.

*Data*\
podczas Dane do zapisania.

*Liczbą*\
podczas Długość bloku doublewords do zapisania.

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`__stosd`|x86, x64|

**Plik nagłówka** \<intrin. h >

## <a name="remarks"></a>Uwagi

W efekcie *dane* DoubleWord są zapisywane w bloku *Count* doublewords w lokalizacji pamięci wskazywanej przez *miejsce docelowe*.

Ta procedura jest dostępna tylko jako wewnętrzna.

## <a name="example"></a>Przykład

```C
// stosd.c
// processor: x86, x64

#include <stdio.h>
#include <memory.h>
#include <intrin.h>

#pragma intrinsic(__stosd)

int main()
{
    unsigned long val = 99999;
    unsigned long a[10];

    memset(a, 0, sizeof(a));
    __stosd(a+1, val, 2);

printf_s( "%u %u %u %u",
              a[0], a[1], a[2], a[3]);
}
```

```Output
0 99999 99999 0
```

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)
