---
title: _mm_cvtsi64x_ss
ms.date: 11/04/2016
f1_keywords:
- _mm_cvtsi64x_ss
helpviewer_keywords:
- cvtsi2ss instruction
- _mm_cvtsi64x_ss intrinsic
ms.assetid: 01e5d321-c18a-46fd-a6f6-324364514e1f
ms.openlocfilehash: 3ba9dc56cbb027e8cf9f31d293b3f96908aff5e4
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59039783"
---
# <a name="mmcvtsi64xss"></a>_mm_cvtsi64x_ss

**Microsoft Specific**

Generuje x64 rozszerzona wersja liczby całkowitej przekonwertować 64-bitowych wartości zmiennopozycyjna pojedynczej precyzji skalarnych (`cvtsi2ss`) instrukcji.

## <a name="syntax"></a>Składnia

```
__m128 _mm_cvtsi64x_ss(
   __m128 a,
   __int64 b
);
```

#### <a name="parameters"></a>Parametry

*a*<br/>
[in] `__m128` Struktury zawierającej czterech wartości zmiennoprzecinkowych pojedynczej precyzji.

*b*<br/>
[in] 64-bitową liczbę całkowitą do przekonwertowania na wartość zmiennoprzecinkową.

## <a name="return-value"></a>Wartość zwracana

`__m128` Strukturę, której pierwsza wartość zmiennoprzecinkowa jest wynik konwersji. Trzy wartości są kopiowane bez zmian od `a`.

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|
|---------------|------------------|
|`_mm_cvtsi64x_ss`|X64|

**Plik nagłówkowy** \<intrin.h >

## <a name="remarks"></a>Uwagi

`__m128` Struktury reprezentuje rejestru XMM, więc w tym wewnętrzne zezwala na wartość `b` z pamięci systemowej do przeniesienia do XMM zarejestrować.

Ta procedura jest dostępna wyłącznie jako wewnętrzna.

## <a name="example"></a>Przykład

```
// _mm_cvtsi64x_ss.cpp
// processor: x64

#include <intrin.h>
#include <stdio.h>

#pragma intrinsic(_mm_cvtsi64x_ss)

int main()
{
    __m128 a;
    __int64 b = 54;

    a.m128_f32[0] = 0;
    a.m128_f32[1] = 0;
    a.m128_f32[2] = 0;
    a.m128_f32[3] = 0;
    a = _mm_cvtsi64x_ss(a, b);

    printf_s( "%lf %lf %lf %lf\n",
              a.m128_f32[0], a.m128_f32[1],
              a.m128_f32[2], a.m128_f32[3] );
}
```

```Output
54.000000 0.000000 0.000000 0.000000
```

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[__m128](../cpp/m128.md)<br/>
[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)