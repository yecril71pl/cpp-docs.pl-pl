---
title: _mm_cvtss_si64x
ms.date: 09/02/2019
f1_keywords:
- _mm_cvtss_si64x
helpviewer_keywords:
- cvtss2si intrinsic
- _mm_cvtss_si64x intrinsic
ms.assetid: c279aff2-ee29-4271-8829-3ec691bf7718
ms.openlocfilehash: bc6e33da5ac7b25727f6e24c3af6e6a926b29847
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230509"
---
# <a name="_mm_cvtss_si64x"></a>_mm_cvtss_si64x

**Specyficzne dla firmy Microsoft**

Generuje rozszerzoną wersję x64 liczby zmiennoprzecinkowej konwersji skalarnej o pojedynczej precyzji do 64-bitowej liczby całkowitej ( `cvtss2si` ).

## <a name="syntax"></a>Składnia

```C
__int64 _mm_cvtss_si64x(
   __m128 value
);
```

### <a name="parameters"></a>Parametry

*wartościami*\
podczas **`__m128`** Struktura zawierająca wartości zmiennoprzecinkowe.

## <a name="return-value"></a>Wartość zwracana

64-bitowa liczba całkowita, wynik konwersji pierwszej wartości zmiennoprzecinkowej na liczbę całkowitą.

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`_mm_cvtss_si64x`|x64|

**Plik nagłówka**\<intrin.h>

## <a name="remarks"></a>Uwagi

Pierwszy element wartości struktury jest konwertowany na liczbę całkowitą i zwracany. Bity sterujące zaokrąglaniem w MXCSR są używane do określania zachowania zaokrąglania. Domyślny tryb zaokrąglania jest zaokrąglany do najbliższe, zaokrąglanie do liczby parzystej, jeśli część dziesiętna to 0,5. Ponieważ **`__m128`** Struktura reprezentuje rejestr XMM, wewnętrzna przyjmuje wartość z rejestru XMM i zapisuje ją w pamięci systemowej.

Ta procedura jest dostępna tylko jako wewnętrzna.

## <a name="example"></a>Przykład

```cpp
// _mm_cvtss_si64x.cpp
// processor: x64
#include <intrin.h>
#include <stdio.h>

#pragma intrinsic(_mm_cvtss_si64x)

int main()
{
    __m128 a;
    __int64 b = 54;

    // _mm_load_ps requires an aligned buffer.
    __declspec(align(16)) float af[4] =
                           { 101.25, 200.75, 300.5, 400.5 };

    // Load a with the floating point values.
    // The values will be copied to the XMM registers.
    a = _mm_load_ps(af);

    // Extract the first element of a and convert to an integer
    b = _mm_cvtss_si64x(a);

    printf_s("%I64d\n", b);
}
```

```Output
101
```

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[__m128d](../cpp/m128d.md)\
[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)
