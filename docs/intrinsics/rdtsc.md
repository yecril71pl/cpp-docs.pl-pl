---
title: __rdtsc
ms.date: 09/02/2019
f1_keywords:
- __rdtsc
helpviewer_keywords:
- __rdtsc intrinsic
- rdtsc instruction
- Read Time Stamp Counter instruction
ms.assetid: e31d0e51-c9bb-42ca-bbe9-a81ffe662387
ms.openlocfilehash: 837b68ca6ac63587cd43a7e8828777221c677e3c
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217150"
---
# <a name="__rdtsc"></a>__rdtsc

**Microsoft Specific**

`rdtsc` Generuje instrukcję zwracającą sygnaturę czasową procesora. Sygnatura czasowa procesora rejestruje liczbę cykli zegara od momentu ostatniego resetowania.

## <a name="syntax"></a>Składnia

```C
unsigned __int64 __rdtsc();
```

## <a name="return-value"></a>Wartość zwracana

64-bitowa liczba całkowita bez znaku reprezentująca liczbę cykli.

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`__rdtsc`|x86, x64|

**Plik nagłówka** \<intrin. h >

## <a name="remarks"></a>Uwagi

Ta procedura jest dostępna tylko jako wewnętrzna.

Interpretacja wartości TSC w późniejszych generacjach sprzętu różni się od tego we wcześniejszych wersjach x64. Aby uzyskać więcej informacji, zapoznaj się z instrukcjami dotyczącymi sprzętu.

## <a name="example"></a>Przykład

```cpp
// rdtsc.cpp
// processor: x86, x64
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(__rdtsc)

int main()
{
    unsigned __int64 i;
    i = __rdtsc();
    printf_s("%I64d ticks\n", i);
}
```

```Output
3363423610155519 ticks
```

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)
