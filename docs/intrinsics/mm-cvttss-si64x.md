---
title: _mm_cvttss_si64x
ms.date: 11/04/2016
f1_keywords:
- _mm_cvttss_si64x
helpviewer_keywords:
- _mm_cvttss_si64x intrinsic
- cvttss2si instruction
ms.assetid: f9a3fd07-5bd8-4758-8744-6315c082cf87
ms.openlocfilehash: 5c2dd98ad3f74ac56b3656ac5f6f450efc40c088
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50522983"
---
# <a name="mmcvttsssi64x"></a>_mm_cvttss_si64x

**Microsoft Specific**

Emituje x64 rozszerzona wersja Convert numerem zmiennopozycyjna pojedynczej precyzji obcinanie do 64-bitowa liczba całkowita (`cvttss2si`) instrukcji.

## <a name="syntax"></a>Składnia

```
__int64 _mm_cvttss_si64x( 
   __m128 value 
);
```

#### <a name="parameters"></a>Parametry

*value*<br/>
[in] `__m128` Struktury zawierającej wartości zmiennoprzecinkowych pojedynczej precyzji.

## <a name="return-value"></a>Wartość zwracana

Wynik konwersji pierwsza wartość zmiennoprzecinkowa na 64-bitową liczbę całkowitą.

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|
|---------------|------------------|
|`_mm_cvttss_si64x`|X64|

**Plik nagłówkowy** \<intrin.h >

## <a name="remarks"></a>Uwagi

Wewnętrzne różni się od `_mm_cvtss_si64x` tylko dlatego, że niedokładny konwersje są obcinane w kierunku zera. Ponieważ `__m128` struktury reprezentuje rejestru XMM, instrukcji generowane przenosi dane z rejestru XMM do pamięci systemowej.

Ta procedura jest dostępna wyłącznie jako wewnętrzna.

## <a name="example"></a>Przykład

```
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

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz też

[__m128](../cpp/m128.md)<br/>
[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)