---
title: __rdtsc | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __rdtsc
dev_langs:
- C++
helpviewer_keywords:
- __rdtsc intrinsic
- rdtsc instruction
- Read Time Stamp Counter instruction
ms.assetid: e31d0e51-c9bb-42ca-bbe9-a81ffe662387
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d10bf2392d7e469f8f9a8a113b96e0cf2be88a50
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46434534"
---
# <a name="rdtsc"></a>__rdtsc

**Microsoft Specific**

Generuje `rdtsc` instrukcji, która zwraca znacznik czasu procesora. Sygnatura czasowa procesora zlicza liczbę cykli zegara od ostatniego resetu.

## <a name="syntax"></a>Składnia

```
unsigned __int64 __rdtsc();
```

## <a name="return-value"></a>Wartość zwracana

64-bitowej nieoznaczonej liczby całkowitej reprezentujący liczbę cykli.

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|
|---------------|------------------|
|`__rdtsc`|x86, x64|

**Plik nagłówkowy** \<intrin.h >

## <a name="remarks"></a>Uwagi

Ta procedura jest dostępna tylko jako wewnętrzna.

Interpretacja wartości TSC w tej generacji sprzętowy różni się od we wcześniejszych wersjach programu x64. Zobacz instrukcje sprzętu, aby uzyskać więcej informacji.

## <a name="example"></a>Przykład

```
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

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz też

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)