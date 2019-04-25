---
title: isNaN, _isnan —, _isnanf
ms.date: 01/31/2019
apiname:
- _isnan
- _isnanf
- isnan
apilocation:
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
apitype: DLLExport
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
ms.openlocfilehash: 8a907dd33803cebd7bc5d71789834d115333b6a0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62157353"
---
# <a name="isnan-isnan-isnanf"></a>isNaN, _isnan —, _isnanf

Sprawdza, czy wartość zmiennoprzecinkowa nie jest liczbą (NAN).

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
Wartość zmiennoprzecinkowa do testowania.

## <a name="return-value"></a>Wartość zwracana

W języku C **isnan** — makro i **_isnan —** i **_isnanf** funkcje zwracają wartość różna od zera, jeśli argument *x* jest NAN; w przeciwnym razie one Zwraca 0.

W języku C++ **isnan** funkcja szablonu zwraca **true** Jeśli argument *x* jest NaN; w przeciwnym razie zwraca **false**.

## <a name="remarks"></a>Uwagi

Ponieważ wartość NaN nie porównywane jako jakąkolwiek wartość NaN, musi być jedną z tych funkcji lub makra wykryta. NaN jest generowany, gdy wynik operacji zmiennoprzecinkowej nie może być przedstawiony w formacie zmiennoprzecinkowych IEEE 754 dla określonego typu. Aby dowiedzieć się, jak jak NaN jest reprezentowana w danych wyjściowych, zobacz [printf](printf-printf-l-wprintf-wprintf-l.md).

Podczas kompilowania co kod C++, **isnan** makro jest niezdefiniowane i **isnan** funkcji szablonu jest zdefiniowany w zamian. Działa tak samo jak makro, ale zwraca wartość typu **bool** zamiast liczby całkowitej.

**_Isnan —** i **_isnanf** funkcje są specyficzne dla firmy Microsoft. **_Isnanf** funkcja jest dostępna, gdy kompilowany x64 tylko.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek (C)|Wymagany nagłówek (C++)|
|-------------|---------------------------|-------------------------------|
|**isNaN —**, **_isnanf**|\<math.h>|\<Math.h > lub \<cmath >|
|**_isnan —**|\<float.h>|\<float.h > lub \<cfloat — >|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
[fpclassify](fpclassify.md)<br/>
[_fpclass, _fpclassf](fpclass-fpclassf.md)<br/>
[isfinite, _finite, _finitef](finite-finitef.md)<br/>
[isinf](isinf.md)<br/>
[isnormal](isnormal.md)<br/>
