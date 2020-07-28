---
title: _mm_stream_sd
ms.date: 09/02/2019
f1_keywords:
- _mm_stream_sd
helpviewer_keywords:
- _mm_stream_sd intrinsic
- movntsd instruction
ms.assetid: 2b4bea5e-e64e-45fa-9afc-88a2e4b82cfc
ms.openlocfilehash: ec639004884d022fe6a827c2ec31d3201ea04657
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214220"
---
# <a name="_mm_stream_sd"></a>_mm_stream_sd

**Specyficzne dla firmy Microsoft**

Zapisuje 64-bitowe dane w lokalizacji pamięci bez zanieczyszczania pamięci podręcznych.

## <a name="syntax"></a>Składnia

```C
void _mm_stream_sd(
   double * Dest,
   __m128d Source
);
```

### <a name="parameters"></a>Parametry

*Dest*\
określoną Wskaźnik do lokalizacji, w której będą zapisywane dane źródłowe.

*Zewnętrz*\
podczas Wartość 128-bitowa zawierająca **`double`** wartość, która ma zostać zapisywana w dolnych bitach 64.

## <a name="return-value"></a>Wartość zwracana

Brak.

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`_mm_stream_sd`|SSE4a|

**Plik nagłówka**\<intrin.h>

## <a name="remarks"></a>Uwagi

Wewnętrznie generuje `movntsd` instrukcję. Aby określić obsługę sprzętową dla tej instrukcji, wywołaj `__cpuid` wewnętrzne z `InfoType=0x80000001` i sprawdź bit 6 z `CPUInfo[2] (ECX)` . Ten bit ma wartość 1, jeśli sprzęt obsługuje tę instrukcję i 0 w przeciwnym razie.

Jeśli uruchamiasz kod, który używa `_mm_stream_sd` wewnętrznego na sprzęcie, który nie obsługuje `movntsd` instrukcji, wyniki są nieprzewidywalne.

## <a name="example"></a>Przykład

```cpp
// Compile this sample with: /EHsc
#include <iostream>
#include <intrin.h>
using namespace std;

int main()
{
    __m128d vals;
    double d[2];

    d[0] = -1.;
    d[1] = -2.;
    vals.m128d_f64[0] = 0.;
    vals.m128d_f64[1] = 1.;
    _mm_stream_sd(&d[1], vals);
    cout << "d[0] = " << d[0] << ", d[1] = " << d[1] << endl;
}
```

```Output
d[0] = -1, d[1] = 1
```

**ZAKOŃCZENIE określonych przez firmę Microsoft**

Fragmenty Copyright 2007 przez Advanced Micro Devices, Inc. Wszelkie prawa zastrzeżone. Wygenerowane z uprawnieniami z zaawansowanych urządzeń Micro Devices, Inc.

## <a name="see-also"></a>Zobacz także

[_mm_stream_ss](../intrinsics/mm-stream-ss.md)\
[_mm_store_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_store_sd)\
[_mm_sfence](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sfence)\
[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)
