---
title: _mm_cvttss_si64x
ms.date: 09/02/2019
f1_keywords:
- _mm_cvttss_si64x
helpviewer_keywords:
- _mm_cvttss_si64x intrinsic
- cvttss2si instruction
ms.assetid: f9a3fd07-5bd8-4758-8744-6315c082cf87
ms.openlocfilehash: 6d920a5c59cacb23c7fb155c7ac8e813a9b0e8d0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217990"
---
# <a name="_mm_cvttss_si64x"></a>_mm_cvttss_si64x

**Specyficzne dla firmy Microsoft**

Emituje rozszerzoną wersję x64 konwersji z obcinaniem liczb zmiennoprzecinkowych o pojedynczej precyzji do 64-bitowej liczby całkowitej ( `cvttss2si` ).

## <a name="syntax"></a>Składnia

```C
__int64 _mm_cvttss_si64x(
   __m128 value
);
```

### <a name="parameters"></a>Parametry

*wartościami*\
podczas **`__m128`** Struktura zawierająca wartości zmiennoprzecinkowe o pojedynczej precyzji.

## <a name="return-value"></a>Wartość zwracana

Wynik konwersji pierwszej wartości zmiennoprzecinkowej na 64-bitową liczbę całkowitą.

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`_mm_cvttss_si64x`|x64|

**Plik nagłówka**\<intrin.h>

## <a name="remarks"></a>Uwagi

Wewnętrznie różni się od `_mm_cvtss_si64x` tylko w tym, że konwersje niedokładne są obcinane w kierunku zera. Ponieważ **`__m128`** Struktura reprezentuje rejestr XMM, wygenerowana instrukcja przenosi dane z rejestru XMM do pamięci systemowej.

Ta procedura jest dostępna tylko jako wewnętrzna.

## <a name="example"></a>Przykład

```cpp
// _mm_cvttss_si64x.cpp
// processor: x64
#include <intrin.h>
#include <stdio.h>

#pragma intrinsic(_mm_cvttss_si64x)

int main()
{
    __m128 a;
    __int64 b = 54;

    // _mm_load_ps requires an aligned buffer.
    __declspec(align(16)) float af[4] = { 101.5, 200.75,
                                          300.5, 400.5 };

    // Load a with the floating point values.
    // The values will be copied to the XMM registers.
    a = _mm_load_ps(af);

    // Extract the first element of a and convert to an integer
    b = _mm_cvttss_si64x(a);

    printf_s("%I64d\n", b);
}
```

```Output
101
```

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[__m128](../cpp/m128.md)\
[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)
