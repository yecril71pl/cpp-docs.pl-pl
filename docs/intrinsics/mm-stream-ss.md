---
title: _mm_stream_ss | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- _mm_stream_ss
dev_langs:
- C++
helpviewer_keywords:
- movntss instruction
- _mm_stream_ss intrinsic
ms.assetid: c53dffe9-0dfe-4063-85d3-e8987b870fce
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 420952d58bb46012741ee95ced4cf39c12d381cd
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="mmstreamss"></a>_mm_stream_ss  
  
**Microsoft Specific**  
  
 Zapisuje dane 32-bitowe w lokalizacji pamięci bez zanieczyszczenie pamięci podręcznych.  
  
## <a name="syntax"></a>Składnia  
  
```  
void _mm_stream_ss(  
   float * Dest,  
   __m128 Source  
);  
```  
  
#### <a name="parameters"></a>Parametry  
  
 [out] `Dest`  
 Wskaźnik do lokalizacji, w którym zapisywana jest źródło danych.  
  
 [in] `Source`  
 Numer 128-bitowego, która zawiera `float` wartość ma zostać zapisany w jego dolnej 32-bitowy.  
  
## <a name="return-value"></a>Wartość zwracana  
  
 Brak.  
  
## <a name="requirements"></a>Wymagania  
  
|— Wewnętrzne|Architektura|  
|---------------|------------------|  
|`_mm_stream_ss`|SSE4a|  
  
 **Plik nagłówka** \<intrin.h >  
  
## <a name="remarks"></a>Uwagi  
  
Generuje tym wewnętrzna `movntss` instrukcji. Aby określić obsługi sprzętowej w tej instrukcji, należy wywołać `__cpuid` wewnętrzne z `InfoType=0x80000001` i sprawdź bit 6 `CPUInfo[2] (ECX)`. Ten bit jest 1, jeśli instrukcja jest obsługiwana i 0, w przeciwnym razie wartość.  
  
Po uruchomieniu kodu korzystającego z `_mm_stream_ss` wewnętrznej na sprzęcie, który nie obsługuje `movntss` instrukcji są nieprzewidywalne wyniki.  
  
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
  
**KOŃCOWY określonych firmy Microsoft**  

Copyright 2007 zaawansowane Micro urządzeń, Inc. Wszelkie prawa zastrzeżone. Odtworzyć z uprawnieniem z zaawansowanymi Micro urządzeń, Inc.  
  
## <a name="see-also"></a>Zobacz też  
 [_mm_stream_sd](../intrinsics/mm-stream-sd.md)   
 [_mm_stream_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_stream_ps)   
 [_mm_store_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_store_ss)   
 [_mm_sfence](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sfence)   
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)