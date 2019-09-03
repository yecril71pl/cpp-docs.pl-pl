---
title: __stosw
ms.date: 09/02/2019
f1_keywords:
- __stosw
helpviewer_keywords:
- stosw instruction
- __stosw intrinsic
- rep stosw instruction
ms.assetid: 7620fd1d-dba5-40e3-8e07-01aa68895133
ms.openlocfilehash: 5fd29bbf1aebba115670fc1bc35e0d8cbe29c7ad
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219929"
---
# <a name="__stosw"></a>__stosw

**Microsoft Specific**

Generuje instrukcję ciągu magazynu (`rep stosw`).

## <a name="syntax"></a>Składnia

```C
void __stosw(
   unsigned short* Destination,
   unsigned short Data,
   size_t Count
);
```

### <a name="parameters"></a>Parametry

*Punktu*\
określoną Miejsce docelowe operacji.

*Data*\
podczas Dane do zapisania.

*Liczbą*\
podczas Długość bloku wyrazów do zapisania.

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`__stosw`|x86, x64|

**Plik nagłówka** \<intrin. h >

## <a name="remarks"></a>Uwagi

Wynik polega na tym, że *dane* słowa są zapisywane w bloku *liczby* wyrazów w ciągu *docelowym* .

Ta procedura jest dostępna tylko jako wewnętrzna.

## <a name="example"></a>Przykład

```C
// stosw.c
// processor: x86, x64
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(__stosw)

int main()
{
    unsigned short val = 128;
    unsigned short a[100];
    memset(a, 0, sizeof(a));
    __stosw(a+10, val, 2);
    printf_s("%u %u %u %u", a[9], a[10], a[11], a[12]);
}
```

```Output
0 128 128 0
```

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)
