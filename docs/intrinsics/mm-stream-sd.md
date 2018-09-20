---
title: _mm_stream_sd | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _mm_stream_sd
dev_langs:
- C++
helpviewer_keywords:
- _mm_stream_sd intrinsic
- movntsd instruction
ms.assetid: 2b4bea5e-e64e-45fa-9afc-88a2e4b82cfc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b965c1882e6126f34e9e81c99c950e072246db97
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46437608"
---
# <a name="mmstreamsd"></a>_mm_stream_sd

**Microsoft Specific**

Zapisuje 64-bitowych danych w lokalizacji pamięci bez zanieczyszczenie pamięci podręcznych.

## <a name="syntax"></a>Składnia

```
void _mm_stream_sd(
   double * Dest,
   __m128d Source
);
```

#### <a name="parameters"></a>Parametry

*docelowy*<br/>
[out] Wskaźnik do lokalizacji, w której będą zapisywane dane źródłowe.

*Źródło*<br/>
[in] 128-bitowej wartości zawierające `double` wartość do zapisania w jej dolnej 64-bitowy...

## <a name="return-value"></a>Wartość zwracana

Brak.

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|
|---------------|------------------|
|`_mm_stream_sd`|SSE4a|

**Plik nagłówkowy** \<intrin.h >

## <a name="remarks"></a>Uwagi

Generuje tym wewnętrzne `movntsd` instrukcji. Aby ustalić, pomoc techniczna dotycząca sprzętu dla tej instrukcji, należy wywołać `__cpuid` wewnętrzne z `InfoType=0x80000001` i sprawdź bit 6 `CPUInfo[2] (ECX)`. Ten bit jest 1, jeśli sprzęt obsługuje tej instrukcji i 0 w przeciwnym razie.

Jeśli uruchamiasz kod, który używa `_mm_stream_sd` wewnętrzne na sprzęcie, który nie obsługuje `movntsd` instrukcji, wyniki są nieprzewidywalne.

## <a name="example"></a>Przykład

```
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

**END specyficzny dla Microsoft**

Copyright 2007 zaawansowane Micro urządzeń, Inc. Wszelkie prawa zastrzeżone. Odtworzyć zgoda zaawansowane Micro urządzeń, Inc.

## <a name="see-also"></a>Zobacz też

[_mm_stream_ss](../intrinsics/mm-stream-ss.md)<br/>
[_mm_store_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_store_sd)<br/>
[_mm_sfence](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sfence)<br/>
[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)