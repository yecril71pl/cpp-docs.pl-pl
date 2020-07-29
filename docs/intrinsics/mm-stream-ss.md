---
title: _mm_stream_ss
ms.date: 09/02/2019
f1_keywords:
- _mm_stream_ss
helpviewer_keywords:
- movntss instruction
- _mm_stream_ss intrinsic
ms.assetid: c53dffe9-0dfe-4063-85d3-e8987b870fce
ms.openlocfilehash: ef1a2045a20070b667d416175826e5377fe30ef6
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215988"
---
# <a name="_mm_stream_ss"></a>_mm_stream_ss

**Specyficzne dla firmy Microsoft**

Zapisuje 32-bitowe dane w lokalizacji pamięci bez zanieczyszczania pamięci podręcznych.

## <a name="syntax"></a>Składnia

```C
void _mm_stream_ss(
   float * Destination,
   __m128 Source
);
```

### <a name="parameters"></a>Parametry

*Punktu*\
określoną Wskaźnik do lokalizacji, w której zapisano dane źródłowe.

*Zewnętrz*\
podczas Numer 128-bitowy, który zawiera wartość, która **`float`** ma zostać zapisywana w dolnych bitach 32.

## <a name="return-value"></a>Wartość zwracana

Brak.

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`_mm_stream_ss`|SSE4a|

**Plik nagłówka**\<intrin.h>

## <a name="remarks"></a>Uwagi

Wewnętrznie generuje `movntss` instrukcję. Aby określić obsługę sprzętową dla tej instrukcji, wywołaj `__cpuid` wewnętrzne z `InfoType=0x80000001` i sprawdź bit 6 z `CPUInfo[2] (ECX)` . Ten bit ma wartość 1, gdy instrukcja jest obsługiwana i 0 w przeciwnym razie.

Jeśli uruchamiasz kod, który używa `_mm_stream_ss` wewnętrznego na sprzęcie, który nie obsługuje `movntss` instrukcji, wyniki są nieprzewidywalne.

## <a name="example"></a>Przykład

```cpp
// Compile this sample with: /EHsc
#include <iostream>
#include <intrin.h>
using namespace std;

int main()
{
    __m128 vals;
    float f[4];

    f[0] = -1.;
    f[1] = -2.;
    f[2] = -3.;
    f[3] = -4.;
    vals.m128_f32[0] = 0.;
    vals.m128_f32[1] = 1.;
    vals.m128_f32[2] = 2.;
    vals.m128_f32[3] = 3.;
    _mm_stream_ss(&f[3], vals);
    cout << "f[0] = " << f[0] << ", f[1] = " << f[1] << endl;
    cout << "f[1] = " << f[1] << ", f[3] = " << f[3] << endl;
}
```

```Output
f[0] = -1, f[1] = -2
f[2] = -3, f[3] = 3
```

**ZAKOŃCZENIE określonych przez firmę Microsoft**

Fragmenty Copyright 2007 przez Advanced Micro Devices, Inc. Wszelkie prawa zastrzeżone. Wygenerowane z uprawnieniami z zaawansowanych urządzeń Micro Devices, Inc.

## <a name="see-also"></a>Zobacz także

[_mm_stream_sd](../intrinsics/mm-stream-sd.md)\
[_mm_stream_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_stream_ps)\
[_mm_store_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_store_ss)\
[_mm_sfence](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sfence)\
[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)
