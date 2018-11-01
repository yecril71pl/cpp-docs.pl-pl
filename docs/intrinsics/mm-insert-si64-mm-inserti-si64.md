---
title: _mm_insert_si64, _mm_inserti_si64
ms.date: 11/04/2016
f1_keywords:
- _mm_inserti_si64
- _mm_insert_si64
helpviewer_keywords:
- insertq instruction
- _mm_insert_si64 intrinsic
- _mm_inserti_si64 intrinsic
ms.assetid: 897a4b36-8b08-4b00-a18f-7850f5732d7d
ms.openlocfilehash: 062e7e56de16d8e8a18101dec0a8e9766e02967f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50631044"
---
# <a name="mminsertsi64-mminsertisi64"></a>_mm_insert_si64, _mm_inserti_si64

**Microsoft Specific**

Generuje `insertq` instrukcji, aby wstawić bitów z drugim argumentem operacji do swojego pierwszego operandu.

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

*Źródło1*<br/>
[in] Pole 128-bitowego z danymi wejściowymi w jej dolnej 64 bitów, w których zostanie wstawione pole.

*Źródło2*<br/>
[in] Pole 128-bitowego z danymi można wstawić w jego bitów ma niski.  Aby uzyskać `_mm_insert_si64`, również zawiera pole deskryptor w jego bitów.

*Długość*<br/>
[in] Stała liczba całkowita określająca długość pola do wstawienia.

*Index*<br/>
[in] Stała liczba całkowita, określająca indeks najmniej znaczący bit pola, do którego zostaną wstawione dane.

## <a name="return-value"></a>Wartość zwracana

Pole 128-bitowego, którego dolnej 64-bitowy zawierają oryginalny niski 64 bity `Source1` za pomocą pola bitowego określonego zastępuje niski bity `Source2`. Górny 64-bitowy zwracanej wartości są niezdefiniowane.

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|
|---------------|------------------|
|`_mm_insert_si64`|SSE4a|
|`_mm_inserti_si64`|SSE4a|

**Plik nagłówkowy** \<intrin.h >

## <a name="remarks"></a>Uwagi

Generuje tym wewnętrzne `insertq` instrukcji, aby wstawić bitów z `Source2` do `Source1`. Wewnętrzne są dwie wersje to: `_mm_inserti_si64`, jest natychmiastowe wersji, a `_mm_insert_si64` jest — natychmiastowe.  Każda wersja wyodrębnia pola bitowe o podanej długości z źródło2 i wstawia ją źródło1.  Wyodrębnione bity są co najmniej znaczące bity źródło2.  Źródło1 pola, do którego zostanie wstawiony tych bitów jest definiowany przez długość i indeks jego najmniej znaczący bit.  Wartości długości i indeksu są pobierane mod 64, zatem zarówno wartość -1 do 127, są interpretowane jako 63. Jeśli suma indeksu bit (mniejsze) i długość pola (mniejsze) jest większa niż 64, wyniki są niezdefiniowane. Wartość zerowa długość pola jest interpretowany jako 64.  W przypadku pola długości i bitowe indeksu zarówno zero, usługa bits 63:0 z `Source2` są wstawiane do `Source1`.  Jeśli długość pola wynosi zero, ale indeks bit jest różna od zera, wyniki są niezdefiniowane.

W wywołaniu _mm_insert_si64 długość pola znajduje się w 77:72 bitów źródło2 i indeks w 69:64 usługi bits.

Jeśli wywołasz `_mm_inserti_si64` z argumentami, że kompilator nie można określić jako stałe całkowite, kompilator generuje kod, umieszczenie tych wartości w rejestrze XMM oraz wywołanie `_mm_insert_si64`.

Aby określić, pomoc techniczna dotycząca sprzętu dla `insertq` wywołania instrukcji `__cpuid` wewnętrzne z `InfoType=0x80000001` i sprawdź bit 6 `CPUInfo[2] (ECX)`. Ten bit będzie 1, jeśli instrukcja jest obsługiwana lub 0 w inny sposób. Jeśli możesz uruchomić kod, który korzysta z tym wewnętrzne na sprzęcie, który nie obsługuje `insertq` instrukcji, wyniki są nieprzewidywalne.

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

**END specyficzny dla Microsoft**

Copyright 2007 zaawansowane Micro urządzeń, Inc. Wszelkie prawa zastrzeżone. Odtworzyć zgoda zaawansowane Micro urządzeń, Inc.

## <a name="see-also"></a>Zobacz też

[_mm_extract_si64, _mm_extracti_si64](../intrinsics/mm-extract-si64-mm-extracti-si64.md)<br/>
[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)