---
title: _mm_extract_si64, _mm_extracti_si64
ms.date: 11/04/2016
f1_keywords:
- _mm_extracti_si64
- _mm_extract_si64
helpviewer_keywords:
- extrq instruction
- _mm_extracti_si64 intrinsic
- _mm_extract_si64 intrinsic
ms.assetid: 459fdd72-cc54-4ee5-bbd5-d2c6067a88e7
ms.openlocfilehash: 21e2b23ca4ac3b98c44ea7152badc5c79f386c09
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50630103"
---
# <a name="mmextractsi64-mmextractisi64"></a>_mm_extract_si64, _mm_extracti_si64

**Microsoft Specific**

Generuje `extrq` instrukcji do wyodrębnienia określonym usługi bits z niskim 64-bitowy swój pierwszy argument.

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

*Źródło*<br/>
[in] Pole 128-bitowego z danymi wejściowymi w jej dolnej 64-bitowy.

*Deskryptor*<br/>
[in] Pole 128-bitowego, opisujący pola bitowego do wyodrębnienia.

*Długość*<br/>
[in] Liczba całkowita określająca długość pola do wyodrębnienia.

*Index*<br/>
[in] Liczba całkowita określająca indeks pola do wyodrębnienia

## <a name="return-value"></a>Wartość zwracana

Pole 128-bitowego na wyodrębniony pole z jego najmniej znaczące bity.

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|
|---------------|------------------|
|`_mm_extract_si64`|SSE4a|
|`_mm_extracti_si64`|SSE4a|

**Plik nagłówkowy** \<intrin.h >

## <a name="remarks"></a>Uwagi

Generuje tym wewnętrzne `extrq` instrukcji do wyodrębnienia bitów z `Source`. Wewnętrzne są dwie wersje to: `_mm_extracti_si64` jest natychmiastowe wersji, a `_mm_extract_si64` jest — natychmiastowe.  Każda wersja wyodrębnia z `Source` polem bitowym zdefiniowany przez jego długość i indeks jego najmniej znaczący bit. Wartości długości i indeksu są pobierane mod 64, zatem zarówno wartość -1 do 127, są interpretowane jako 63. Jeśli suma liczby (mniejsze) indeks i długość pola (mniejsze) jest większa niż 64, wyniki są niezdefiniowane. Wartość zerowa długość pola jest interpretowany jako 64. W przypadku pola długości i bitowe indeksu zarówno zero, usługa bits 63:0 z `Source` zostały wyodrębnione. Jeśli długość pola wynosi zero, ale indeks bit jest różna od zera, wyniki są niezdefiniowane.

W wywołaniu _mm_extract_si64 `Descriptor` zawiera indeks 13:8 bitów i długość pola danych, który ma zostać wyodrębniony w bitach 5:0..

Jeśli wywołasz `_mm_extracti_si64` z argumentami, że kompilator nie można określić jako stałe całkowite kompilator generuje kod, umieszczenie tych wartości w rejestrze XMM (`Descriptor`) oraz wywołanie `_mm_extract_si64`.

Aby określić, pomoc techniczna dotycząca sprzętu dla `extrq` instrukcji, wywołanie `__cpuid` wewnętrzne z `InfoType=0x80000001` i sprawdź bit 6 `CPUInfo[2] (ECX)`. Ten bit będzie 1, jeśli instrukcja jest obsługiwana lub 0 w inny sposób. Jeśli można uruchomić kod, który używa tego wewnętrzne sprzętu, który nie obsługuje `extrq` instrukcji, wyniki są nieprzewidywalne.

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

**END specyficzny dla Microsoft**

Copyright 2007 zaawansowane Micro urządzeń, Inc. Wszelkie prawa zastrzeżone. Odtworzyć zgoda zaawansowane Micro urządzeń, Inc.

## <a name="see-also"></a>Zobacz też

[_mm_insert_si64, _mm_inserti_si64](../intrinsics/mm-insert-si64-mm-inserti-si64.md)<br/>
[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)