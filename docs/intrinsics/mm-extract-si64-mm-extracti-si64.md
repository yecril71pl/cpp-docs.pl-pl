---
title: _mm_extract_si64, _mm_extracti_si64
ms.date: 09/02/2019
f1_keywords:
- _mm_extracti_si64
- _mm_extract_si64
helpviewer_keywords:
- extrq instruction
- _mm_extracti_si64 intrinsic
- _mm_extract_si64 intrinsic
ms.assetid: 459fdd72-cc54-4ee5-bbd5-d2c6067a88e7
ms.openlocfilehash: cfd7029966c29f876f0e4f671830e20e2eacc940
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217400"
---
# <a name="_mm_extract_si64-_mm_extracti_si64"></a>_mm_extract_si64, _mm_extracti_si64

**Microsoft Specific**

`extrq` Generuje instrukcję wyodrębniania określonych bitów z najniższych 64 bitów pierwszego argumentu.

## <a name="syntax"></a>Składnia

```C
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

### <a name="parameters"></a>Parametry

*Zewnętrz*\
podczas Pole 128-bitowe z danymi wejściowymi w niższej wersji 64 bitów.

*Opis*\
podczas Pole 128-bitowe opisujące pole bitowe, które ma zostać wyodrębnione.

*Długość*\
podczas Liczba całkowita, która określa długość pola do wyodrębnienia.

*Indeks*\
podczas Liczba całkowita określająca indeks pola do wyodrębnienia

## <a name="return-value"></a>Wartość zwracana

Pole 128-bitowe z wyodrębnionym polem w najmniej znaczących bitach.

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`_mm_extract_si64`|SSE4a|
|`_mm_extracti_si64`|SSE4a|

**Plik nagłówka** \<intrin. h >

## <a name="remarks"></a>Uwagi

Te elementy wewnętrzne generują `extrq` instrukcję wyodrębniania bitów ze *źródła*. Istnieją dwie wersje: `_mm_extracti_si64` jest natychmiastowa wersja i `_mm_extract_si64` jest nienatychmiastowa. Każda wersja wyodrębnia ze *źródła* pole bitowe zdefiniowane przez jego długość i indeks jego najmniej znaczącego bitu. Wartości długości i indeksu są brane pod kątem mod 64, dlatego oba-1 i 127 są interpretowane jako 63. Jeśli sum (zredukowany) indeks i (zmniejszony) długość pola jest większa niż 64, wyniki są niezdefiniowane. Wartość zero dla długości pola jest interpretowana jako 64. Jeśli długość pola i indeks bitu są równe zero, są wyodrębniane bity 63:0 ze *źródła* . Jeśli długość pola wynosi zero, ale indeks bitowy jest różny od zera, wyniki są niezdefiniowane.

W wywołaniu do `_mm_extract_si64`, *deskryptor* zawiera indeks w bitach 13:8 i długość pola danych, które mają zostać wyodrębnione w bitach 5:0.

W przypadku wywołania `_mm_extracti_si64` z argumentami, które kompilator nie może ustalić jako stałych całkowitych, kompilator generuje kod, aby spakować te wartości do rejestru XMM(deskryptora) i `_mm_extract_si64`wywołać.

Aby określić obsługę `extrq` sprzętową instrukcji, `__cpuid` Wywołaj wewnętrzne z `InfoType=0x80000001` i sprawdź bit 6 z `CPUInfo[2] (ECX)`. Ten bit będzie miał wartość 1, jeśli instrukcja jest obsługiwana i 0 w przeciwnym razie. Jeśli uruchamiasz kod korzystający z `extrq` tego wewnętrznego sprzętu, który nie obsługuje instrukcji, wyniki są nieprzewidywalne.

## <a name="example"></a>Przykład

```cpp
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

**ZAKOŃCZENIE określonych przez firmę Microsoft**

Fragmenty Copyright 2007 przez Advanced Micro Devices, Inc. Wszelkie prawa zastrzeżone. Wygenerowane z uprawnieniami z zaawansowanych urządzeń Micro Devices, Inc.

## <a name="see-also"></a>Zobacz także

[_mm_insert_si64, _mm_inserti_si64](../intrinsics/mm-insert-si64-mm-inserti-si64.md)\
[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)
