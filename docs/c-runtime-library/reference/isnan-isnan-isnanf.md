---
title: isnan, _isnan, _isnanf
ms.date: 01/31/2019
api_name:
- _isnan
- _isnanf
- isnan
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
- _isnan
- isnan
- math/isnan
- math/_isnan
- math/_isnanf
- _isnanf
helpviewer_keywords:
- NAN (not a number)
- _isnan function
- IEEE floating-point representation
- Not a Number (NANs)
- isnan function
ms.assetid: 391fbc5b-89a4-4fba-997e-68f1131caf82
ms.openlocfilehash: 5aebacd15000e0202a26f600614900390c1ba7a4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213544"
---
# <a name="isnan-_isnan-_isnanf"></a>isnan, _isnan, _isnanf

Testuje, czy wartość zmiennoprzecinkowa nie jest liczbą (NAN).

## <a name="syntax"></a>Składnia

```C
int isnan(
   /* floating-point */ x
); /* C-only macro */

int _isnan(
   double x
);

int _isnanf(
   float x
); /* x64 only */

template <class T>
bool isnan(
   T x
) throw(); /* C++ only */
```

### <a name="parameters"></a>Parametry

*x*<br/>
Wartość zmiennoprzecinkowa do przetestowania.

## <a name="return-value"></a>Wartość zwracana

W języku C, makro **isNaN** i funkcje **_isnan** i **_isnanf** zwracają wartość różną od zera, jeśli argument *x* jest NaN; w przeciwnym razie zwracają 0.

W języku C++ funkcja szablonu **isNaN** zwraca wartość, **`true`** Jeśli argument *x* jest NaN; w przeciwnym razie zwraca **`false`** .

## <a name="remarks"></a>Uwagi

Ponieważ wartość NaN nie jest porównywana jako równa żadnej innej wartości NaN, należy użyć jednej z tych funkcji lub makr do wykrycia. Wartość NaN jest generowana, gdy wynik operacji zmiennoprzecinkowej nie może być reprezentowany w formacie zmiennoprzecinkowym IEEE-754 dla określonego typu. Aby uzyskać informacje o sposobie reprezentowania elementu NaN dla danych wyjściowych, zobacz [printf](printf-printf-l-wprintf-wprintf-l.md).

Po skompilowaniu jako C++ makro **isNaN** nie jest zdefiniowane, a zamiast niej zdefiniowana jest funkcja szablonu **isNaN** . Działa tak samo jak makro, ale zwraca wartość typu, **`bool`** a nie liczbę całkowitą.

**_Isnan** i **_isnanf** funkcje są specyficzne dla firmy Microsoft. Funkcja **_isnanf** jest dostępna tylko po skompilowaniu dla x64.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek (C)|Wymagany nagłówek (C++)|
|-------------|---------------------------|-------------------------------|
|**isNaN**, **_isnanf**|\<math.h>|\<math.h> lub \<cmath>|
|**_isnan**|\<float.h>|\<float.h> lub \<cfloat>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Obsługa zmiennoprzecinkowa](../../c-runtime-library/floating-point-support.md)<br/>
[fpclassify](fpclassify.md)<br/>
[_fpclass, _fpclassf](fpclass-fpclassf.md)<br/>
[isfinite, _finite, _finitef](finite-finitef.md)<br/>
[isinf](isinf.md)<br/>
[isnormal](isnormal.md)<br/>
