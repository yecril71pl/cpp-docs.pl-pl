---
title: isNaN, _isnan —, _isnanf
ms.date: 04/05/2018
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
ms.openlocfilehash: ce111569b7caee9d0c7b8f35352c395571ad08b1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50650869"
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

W języku C **isnan** — makro i **_isnan —** i **_isnanf** funkcje zwracają wartość różną od zera, jeśli argument *x* jest NAN; w przeciwnym razie one Zwraca 0.

W języku C++ **isnan** szablonu funkcje zwracają **true** Jeśli argument *x* jest NAN; w przeciwnym razie zwraca **false**.

## <a name="remarks"></a>Uwagi

C **isnan** — makro i **_isnan —** i **_isnanf** wartość zmiennoprzecinkowa testowanie funkcji *x*, zwraca wartość różną od zera, jeśli *x* nie jest wartością liczby (NAN). NAN jest generowany, gdy wynik operacji zmiennoprzecinkowej nie może być przedstawiony w formacie zmiennoprzecinkowych IEEE 754 dla określonego typu. Aby dowiedzieć się, jak jak NAN jest reprezentowana w danych wyjściowych, zobacz [printf](printf-printf-l-wprintf-wprintf-l.md).

Podczas kompilowania co kod C++, **isnan** makro jest niezdefiniowane i **isnan** funkcji szablonu jest zdefiniowany w zamian. Zwraca wartość typu **bool** zamiast liczby całkowitej.

**_Isnan —** i **_isnanf** funkcje są specyficzne dla firmy Microsoft. **_Isnanf** funkcja jest dostępna, gdy kompilowany x64 tylko.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek (C)|Wymagany nagłówek (C++)|
|-------------|---------------------------|-------------------------------|
|**isNaN —**, **_isnanf**|\<math.h>|\<Math.h > lub \<cmath >|
|**_isnan —**|\<float.h>|\<float.h > lub \<cfloat — >|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
[_finite, _finitef](finite-finitef.md)<br/>
[_fpclass, _fpclassf](fpclass-fpclassf.md)<br/>
