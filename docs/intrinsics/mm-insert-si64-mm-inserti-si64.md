---
title: _mm_insert_si64, _mm_inserti_si64 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _mm_inserti_si64
- _mm_insert_si64
dev_langs: C++
helpviewer_keywords:
- insertq instruction
- _mm_insert_si64 intrinsic
- _mm_inserti_si64 intrinsic
ms.assetid: 897a4b36-8b08-4b00-a18f-7850f5732d7d
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5f7a2b52c8a41a3689cc668846e038505425aab4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="mminsertsi64-mminsertisi64"></a>_mm_insert_si64, _mm_inserti_si64
**Dotyczące firmy Microsoft**  
  
 Generuje `insertq` instrukcji, aby wstawić usługi bits z jej drugi argument operacji do jego pierwszym argumentem.  
  
## <a name="syntax"></a>Składnia  
  
```  
__m128i _mm_insert_si64(  
   __m128i Source1,  
   __m128i Source2  
);  
__m128i _mm_inserti_si64(  
   __m128i Source1,  
   __m128i Source2  
   int Length,  
   int Index  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in]`Source1`  
 Pole 128-bitowego z danych wejściowych w jego dolnej 64-bitowej do których zostanie wstawiony pola.  
  
 [in]`Source2`  
 Pole 128-bitowego z danymi do wstawienia w jego niski usługi bits.  Aby uzyskać `_mm_insert_si64`, zawiera także deskryptora pola w jego bitów.  
  
 [in]`Length`  
 Stała liczba całkowita określająca długość pola do wstawienia.  
  
 [in]`Index`  
 Stała liczba całkowita określająca indeks bitem pola, w którym zostaną umieszczone dane.  
  
## <a name="return-value"></a>Wartość zwracana  
 Pole 128-bitowego, którego niższe 64-bitowy zawierają oryginalnego niski 64 bity `Source1` z pola bitowego określonego zastępuje niski bity `Source2`. Górny 64-bitowy zwracanej wartości są niezdefiniowane.  
  
## <a name="requirements"></a>Wymagania  
  
|— Wewnętrzne|Architektura|  
|---------------|------------------|  
|`_mm_insert_si64`|SSE4a|  
|`_mm_inserti_si64`|SSE4a|  
  
 **Plik nagłówka** \<intrin.h >  
  
## <a name="remarks"></a>Uwagi  
 Generuje tym wewnętrzna `insertq` instrukcji, aby wstawić usługi bits z `Source2` do `Source1`. Istnieją dwie wersje tego wewnętrzne: `_mm_inserti_si64`, jest natychmiastowe wersja i `_mm_insert_si64` jest — natychmiastowe.  Każda wersja wyodrębnia pole bitowe o podanej długości z źródło2 i wstawia ją źródło1.  Bity wyodrębnionego są najmniej znaczący bity źródło2.  Źródło1 pola, w którym zostanie wstawiony tych bitów definiuje długość i indeks jego bitem.  Wartości długości i indeksu są pobierane mod 64, w związku z tym zarówno wartość -1 do 127 będą interpretowane jako 63. Jeśli sumy bitowej (zmniejszenie) indeks i długość pola (zmniejszenie) jest większy niż 64, wyniki są niezdefiniowane. Wartość zerowa długość pola jest interpretowany jako 64.  Jeśli indeks długość i bitowe pola są obie zerowe, 63:0 usługi bits z `Source2` są wstawiane do `Source1`.  Jeśli długość pola wynosi zero, ale indeks bit jest różna od zera, wyniki są niezdefiniowane.  
  
 W wywołaniu _mm_insert_si64 długość pola znajduje się w 77:72 bitów źródło2 i indeks w 69:64 usługi bits.  
  
 Jeśli należy wywołać `_mm_inserti_si64` z argumentami, że kompilator nie można określić jako stałe całkowite, kompilator generuje kod pakietu tych wartości w rejestrze XMM oraz wywołanie `_mm_insert_si64`.  
  
 Ustalenie sprzętu Obsługa `insertq` wywołanie instrukcji `__cpuid` wewnętrzne z `InfoType=0x80000001` i sprawdź bit 6 `CPUInfo[2] (ECX)`. Ten bit będzie 1, jeśli instrukcja jest obsługiwana i 0 w inny sposób. Jeśli możesz uruchomić kodu korzystającego z tym wewnętrzna na sprzęcie, który nie obsługuje `insertq` instrukcji są nieprzewidywalne wyniki.  
  
## <a name="example"></a>Przykład  
  
```  
// Compile this sample with: /EHsc  
#include <iostream>  
#include <intrin.h>  
using namespace std;  
  
union {  
    __m128i m;  
    unsigned __int64 ui64[2];  
} source1, source2, source3, result1, result2, result3;  
  
int  
main()  
{  
  
    __int64 mask;  
  
    source1.ui64[0] = 0xffffffffffffffffll;  
    source2.ui64[0] = 0xfedcba9876543210ll;  
    source2.ui64[1] = 0xc10;  
    source3.ui64[0] = source2.ui64[0];  
  
    result1.m = _mm_insert_si64 (source1.m, source2.m);  
    result2.m = _mm_inserti_si64(source1.m, source3.m, 16, 12);  
    mask = 0xffff << 12;  
    mask = ~mask;  
    result3.ui64[0] = (source1.ui64[0] & mask) |  
                      ((source2.ui64[0] & 0xffff) << 12);  
  
    cout << hex << "result1 = 0x" << result1.ui64[0] << endl;  
    cout << "result2 = 0x" << result2.ui64[0] << endl;  
    cout << "result3 = 0x" << result3.ui64[0] << endl;  
  
}  
```  
  
```Output  
result1 = 0xfffffffff3210fff  
result2 = 0xfffffffff3210fff  
result3 = 0xfffffffff3210fff  
```  
  
**KOŃCOWY określonych firmy Microsoft**  
 Copyright 2007 zaawansowane Micro urządzeń, Inc. Wszelkie prawa zastrzeżone. Odtworzyć z uprawnieniem z zaawansowanymi Micro urządzeń, Inc.  
  
## <a name="see-also"></a>Zobacz też  
 [_mm_extract_si64, _mm_extracti_si64](../intrinsics/mm-extract-si64-mm-extracti-si64.md)   
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)