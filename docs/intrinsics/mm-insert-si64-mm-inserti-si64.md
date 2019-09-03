---
title: _mm_insert_si64, _mm_inserti_si64
ms.date: 09/02/2019
f1_keywords:
- _mm_inserti_si64
- _mm_insert_si64
helpviewer_keywords:
- insertq instruction
- _mm_insert_si64 intrinsic
- _mm_inserti_si64 intrinsic
ms.assetid: 897a4b36-8b08-4b00-a18f-7850f5732d7d
ms.openlocfilehash: 08469ad8049df2a07f0e66d650c1ca3118f8b980
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221775"
---
# <a name="_mm_insert_si64-_mm_inserti_si64"></a>_mm_insert_si64, _mm_inserti_si64

**Microsoft Specific**

`insertq` Generuje instrukcję wstawiania bitów z drugiego operandu do pierwszego operandu.

## <a name="syntax"></a>Składnia

```C
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

### <a name="parameters"></a>Parametry

*Source1*\
podczas Pole 128-bitowe, które zawiera dane wejściowe z niższym 64 bitowym, do którego zostanie wstawione pole.

*Source2*\
podczas Pole 128-bitowe, które ma dane do wstawienia w jego małych bitach.  Dla `_mm_insert_si64`programu, zawiera również deskryptor pola w jego dużych bitach.

*Długość*\
podczas Stała całkowita, która określa długość pola do wstawienia.

*Indeks*\
podczas Stała całkowita, która określa indeks najmniej znaczącego bitu pola, w którym zostaną wstawione dane.

## <a name="return-value"></a>Wartość zwracana

Pole 128-bitowe, którego Dolna liczba bitów 64 zawierają oryginalne, niskie 64 bitów *source1*, z określonym polem bitowym zastąpionym przez małe bity *SOURCE2*. Górne 64 bitów wartości zwracanej nie są zdefiniowane.

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`_mm_insert_si64`|SSE4a|
|`_mm_inserti_si64`|SSE4a|

**Plik nagłówka** \<intrin. h >

## <a name="remarks"></a>Uwagi

Te elementy wewnętrzne generują `insertq` instrukcję wstawiania bitów z *SOURCE2* do *source1*. Istnieją dwie wersje: `_mm_inserti_si64`, to Natychmiastowa wersja, a `_mm_insert_si64` nie natychmiastowa. Każda wersja wyodrębnia pole bitowe o danej długości z SOURCE2 i wstawia je do Source1.  Wyodrębnione bity są najmniej znaczącymi bitami SOURCE2.  Pole source1, do którego zostaną wstawione te bity, definiuje długość i indeks jego najmniej znaczącego bitu.  Wartości długości i indeksu są brane pod kątem mod 64, dlatego oba-1 i 127 są interpretowane jako 63. Jeśli sum (zredukowany) indeks bitowy i (zmniejszony) długość pola jest większa niż 64, wyniki są niezdefiniowane. Wartość zero dla długości pola jest interpretowana jako 64. Jeśli długość pola i indeks bitu są równe zero, bity 63:0 of *SOURCE2* są wstawiane do *source1*. Jeśli długość pola wynosi zero, ale indeks bitowy jest różny od zera, wyniki są niezdefiniowane.

W wywołaniu _mm_insert_si64 długość pola jest zawarta w bitach 77:72 of SOURCE2 i indeksie w bitach 69:64.

W przypadku wywołania `_mm_inserti_si64` z argumentami, które kompilator nie może ustalić jako stałych całkowitych, kompilator generuje kod, aby spakować te wartości do rejestru XMM i wywołać `_mm_insert_si64`.

Aby określić obsługę `insertq` sprzętową instrukcji, `__cpuid` Wywołaj wewnętrzne z `InfoType=0x80000001` i sprawdź bit 6 z `CPUInfo[2] (ECX)`. Ten bit ma wartość 1, jeśli instrukcja jest obsługiwana i 0 w przeciwnym razie. Jeśli uruchamiasz kod, który używa wewnętrznego na sprzęcie, który nie obsługuje `insertq` instrukcji, wyniki są nieprzewidywalne.

## <a name="example"></a>Przykład

```cpp
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

**ZAKOŃCZENIE określonych przez firmę Microsoft**

Fragmenty Copyright 2007 przez Advanced Micro Devices, Inc. Wszelkie prawa zastrzeżone. Wygenerowane z uprawnieniami z zaawansowanych urządzeń Micro Devices, Inc.

## <a name="see-also"></a>Zobacz także

[_mm_extract_si64, _mm_extracti_si64](../intrinsics/mm-extract-si64-mm-extracti-si64.md)\
[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)
