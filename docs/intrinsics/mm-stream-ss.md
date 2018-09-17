---
title: _mm_stream_ss | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _mm_stream_ss
dev_langs:
- C++
helpviewer_keywords:
- movntss instruction
- _mm_stream_ss intrinsic
ms.assetid: c53dffe9-0dfe-4063-85d3-e8987b870fce
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ef5910f47fdf9c058cfb4493c9df486749da18fc
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45714392"
---
# <a name="mmstreamss"></a>_mm_stream_ss  
  
**Microsoft Specific**  
  
 Zapisuje 32-bitowych danych w lokalizacji pamięci bez zanieczyszczenie pamięci podręcznych.  
  
## <a name="syntax"></a>Składnia  
  
```  
void _mm_stream_ss(  
   float * Dest,  
   __m128 Source  
);  
```  
  
#### <a name="parameters"></a>Parametry  
  
*docelowy*<br/>
[out] Wskaźnik do lokalizacji, w którym zapisywana jest źródło danych.  
  
*Źródło*<br/>
[in] 128-bitową liczbą, która zawiera `float` wartość do zapisania w jej dolnej 32-bitowy...  
  
## <a name="return-value"></a>Wartość zwracana  
  
 Brak.  
  
## <a name="requirements"></a>Wymagania  
  
|Wewnętrzne|Architektura|  
|---------------|------------------|  
|`_mm_stream_ss`|SSE4a|  
  
 **Plik nagłówkowy** \<intrin.h >  
  
## <a name="remarks"></a>Uwagi  
  
Generuje tym wewnętrzne `movntss` instrukcji. Aby ustalić, pomoc techniczna dotycząca sprzętu dla tej instrukcji, należy wywołać `__cpuid` wewnętrzne z `InfoType=0x80000001` i sprawdź bit 6 `CPUInfo[2] (ECX)`. Ten bit jest 1, jeśli instrukcja jest obsługiwana i 0.  
  
Jeśli uruchamiasz kod, który używa `_mm_stream_ss` wewnętrzne na sprzęcie, który nie obsługuje `movntss` instrukcji, wyniki są nieprzewidywalne.  
  
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
  
**END specyficzny dla Microsoft**  

Copyright 2007 zaawansowane Micro urządzeń, Inc. Wszelkie prawa zastrzeżone. Odtworzyć zgoda zaawansowane Micro urządzeń, Inc.  
  
## <a name="see-also"></a>Zobacz też  
 [_mm_stream_sd](../intrinsics/mm-stream-sd.md)   
 [_mm_stream_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_stream_ps)   
 [_mm_store_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_store_ss)   
 [_mm_sfence](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sfence)   
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)