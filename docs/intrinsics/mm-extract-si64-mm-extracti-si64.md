---
title: _mm_extract_si64, _mm_extracti_si64 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _mm_extracti_si64
- _mm_extract_si64
dev_langs:
- C++
helpviewer_keywords:
- extrq instruction
- _mm_extracti_si64 intrinsic
- _mm_extract_si64 intrinsic
ms.assetid: 459fdd72-cc54-4ee5-bbd5-d2c6067a88e7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a8ba4986abf097a5827d3db7f93dbbd0a9640862
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="mmextractsi64-mmextractisi64"></a>_mm_extract_si64, _mm_extracti_si64
**Microsoft Specific**  
  
 Generuje `extrq` instrukcji do wyodrębnienia określonym usługi bits z niskim 64-bitowy pierwszego argumentu.  
  
## <a name="syntax"></a>Składnia  
  
```  
__m128i _mm_extract_si64(  
   __m128i Source,  
   __m128i Descriptor  
);  
__m128i _mm_extracti_si64(  
   __m128i Source,  
   int Length,  
   int Index  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in] `Source`  
 Pole 128-bitowego z danych wejściowych w jego dolnej 64-bitowy.  
  
 [in]  `Descriptor`  
 Pole 128-bitowego, opisujący pola bitowego do wyodrębnienia.  
  
 [in]  `Length`  
 Liczba całkowita określająca długość pola do wyodrębnienia.  
  
 [in]  `Index`  
 Liczba całkowita określająca indeks pola do wyodrębnienia  
  
## <a name="return-value"></a>Wartość zwracana  
 Pole 128-bitowego z polem wyodrębnione w jego najmniej znaczących bitów.  
  
## <a name="requirements"></a>Wymagania  
  
|— Wewnętrzne|Architektura|  
|---------------|------------------|  
|`_mm_extract_si64`|SSE4a|  
|`_mm_extracti_si64`|SSE4a|  
  
 **Plik nagłówka** \<intrin.h >  
  
## <a name="remarks"></a>Uwagi  
 Generuje tym wewnętrzna `extrq` instrukcji do wyodrębnienia usługi bits z `Source`. Istnieją dwie wersje tego wewnętrzne: `_mm_extracti_si64` jest natychmiastowe wersja i `_mm_extract_si64` jest — natychmiastowe.  Każda wersja wyodrębnia z `Source` pola bitowego zdefiniowany przez jego długość i indeks jego bitem. Wartości długości i indeksu są pobierane mod 64, w związku z tym zarówno wartość -1 do 127 będą interpretowane jako 63. Jeśli sum (mniejsze) indeks i długość pola (zmniejszenie) jest większa niż 64, wyniki są niezdefiniowane. Wartość zerowa długość pola jest interpretowany jako 64. Jeśli indeks długość i bitowe pola są obie zerowe, 63:0 usługi bits z `Source` są wyodrębniane. Jeśli długość pola wynosi zero, ale indeks bit jest różna od zera, wyniki są niezdefiniowane.  
  
 W wywołaniu _mm_extract_si64 `Descriptor` zawiera indeks w 13:8 bitów i długość pola danych do wyodrębnienia w bitach 5:0..  
  
 Jeśli należy wywołać `_mm_extracti_si64` z argumentami, że kompilator nie można określić jako stałe całkowite kompilator generuje kod, aby pakiet tych wartości w rejestrze XMM (`Descriptor`) oraz wywołanie `_mm_extract_si64`.  
  
 Aby określić obsługę sprzętu `extrq` instrukcji, wywołanie `__cpuid` wewnętrzne z `InfoType=0x80000001` i sprawdź bit 6 `CPUInfo[2] (ECX)`. Ten bit będzie 1, jeśli instrukcja jest obsługiwana i 0 w inny sposób. Jeśli uruchamianie kodu, który używa tego wewnętrzne sprzętu, który nie obsługuje `extrq` instrukcji są nieprzewidywalne wyniki.  
  
## <a name="example"></a>Przykład  
  
```  
// Compile this sample with: /EHsc  
#include <iostream>  
#include <intrin.h>  
using namespace std;  
  
union {  
    __m128i m;  
    unsigned __int64 ui64[2];  
} source, descriptor, result1, result2, result3;  
  
int  
main()  
{  
    source.ui64[0] =     0xfedcba9876543210ll;  
    descriptor.ui64[0] = 0x0000000000000b1bll;  
  
    result1.m = _mm_extract_si64 (source.m, descriptor.m);  
    result2.m = _mm_extracti_si64(source.m, 27, 11);  
    result3.ui64[0] = (source.ui64[0] >> 11) & 0x7ffffff;  
  
    cout << hex << "result1 = 0x" << result1.ui64[0] << endl;  
    cout << "result2 = 0x" << result2.ui64[0] << endl;  
    cout << "result3 = 0x" << result3.ui64[0] << endl;  
}  
```  
  
```Output  
result1 = 0x30eca86  
result2 = 0x30eca86  
result3 = 0x30eca86  
```  
  
**KOŃCOWY określonych firmy Microsoft**  
 Copyright 2007 zaawansowane Micro urządzeń, Inc. Wszelkie prawa zastrzeżone. Odtworzyć z uprawnieniem z zaawansowanymi Micro urządzeń, Inc.  
  
## <a name="see-also"></a>Zobacz też  
 [_mm_insert_si64, _mm_inserti_si64](../intrinsics/mm-insert-si64-mm-inserti-si64.md)   
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)