---
title: __movsw
ms.date: 09/02/2019
f1_keywords:
- __movsw
helpviewer_keywords:
- movsw instruction
- rep movsw instruction
- __movsw intrinsic
ms.assetid: db402ad5-7f0e-449a-b0b0-eea9928d6435
ms.openlocfilehash: 67eef7fe0a5b9803650f345740a8c40262cd2014
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221723"
---
# <a name="__movsw"></a>__movsw

**Microsoft Specific**

Generuje instrukcję Move String (`rep movsw`).

## <a name="syntax"></a>Składnia

```C
void __movsw(
   unsigned short* Destination,
   unsigned short* Source,
   size_t Count
);
```

### <a name="parameters"></a>Parametry

*Punktu*\
określoną Miejsce docelowe operacji.

*Zewnętrz*\
podczas Źródło operacji.

*Liczbą*\
podczas Liczba słów do skopiowania.

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`__movsw`|x86, x64|

**Plik nagłówka** \<intrin. h >

## <a name="remarks"></a>Uwagi

Wynikiem tego jest to, że pierwsze słowa liczbowe wskazywane przez *Źródło* są kopiowane do ciągu *docelowego* .

Ta procedura jest dostępna tylko jako wewnętrzna.

## <a name="example"></a>Przykład

```cpp
// movsw.cpp
// processor: x86, x64
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(__movsw)

int main()
{
    unsigned short s1[10];
    unsigned short s2[10] = {0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
    __movsw(s1, s2, 10);

    for (int i = 0; i < 10; i++)
        printf_s("%d ", s1[i]);
    printf_s("\n");
}
```

```Output
0 1 2 3 4 5 6 7 8 9
```

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)
