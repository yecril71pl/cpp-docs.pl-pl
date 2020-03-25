---
title: cos, cosf, cosl
ms.date: 04/05/2018
api_name:
- cos
- cosf
- cosl
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-math-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- cos
- cosf
- cosl
helpviewer_keywords:
- cosines
- cosl function
- calculating cosine
- cosf function
- cos function
- trigonometric functions
- cosines, calculating
ms.assetid: ae90435e-6b68-4a47-a81f-be87d5c08f16
ms.openlocfilehash: 9ec612aa9f8c6eaf1731d62b654d45841cdfa159
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170258"
---
# <a name="cos-cosf-cosl"></a>cos, cosf, cosl

Oblicza cosinus.

## <a name="syntax"></a>Składnia

```C
double cos( double x );
float cosf( float x );
long double cosl( long double x );
```

```cpp
float cos( float x );  // C++ only
long double cos( long double x );  // C++ only
```

### <a name="parameters"></a>Parametry

*y*<br/>
Kąt w radianach.

## <a name="return-value"></a>Wartość zwracana

Cosinus *x*. Jeśli wartość *x* jest większa lub równa 263 lub mniejsza lub równa-263, występuje utrata znaczenia w wyniku.

|Dane wejściowe|Wyjątek SEH|Wyjątek Matherr|
|-----------|-------------------|-----------------------|
|QNAN, IND|brak|**_DOMAIN**|
|± INF|**Nieprawidłowy**|**_DOMAIN**|

## <a name="remarks"></a>Uwagi

Ponieważ C++ umożliwia Przeciążenie, można wywoływać przeciążenia funkcji **cos** , które pobierają i zwracają wartości **zmiennoprzecinkowe** lub **długie** **Double** . W programie C funkcja **cos** zawsze przyjmuje i zwraca wartość **Double**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek C|Wymagany C++ nagłówek|
|-------------|---------------------|-|
|**cos**, **cosh —** , **cosf —**|\<> Math. h|\<cmath > lub \<Math. h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład w [Sin, SINF —, sinl](sin-sinf-sinl.md).

## <a name="see-also"></a>Zobacz też

[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
[acos, acosf, acosl](acos-acosf-acosl.md)<br/>
[asin, asinf, asinl](asin-asinf-asinl.md)<br/>
[atan, atanf, atanl, atan2, atan2f, atan2l](atan-atanf-atanl-atan2-atan2f-atan2l.md)<br/>
[_matherr](matherr.md)<br/>
[sin, sinf, sinl](sin-sinf-sinl.md)<br/>
[tan, tanf, tanl](tan-tanf-tanl.md)<br/>
[_CIcos](../../c-runtime-library/cicos.md)<br/>
