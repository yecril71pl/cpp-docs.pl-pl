---
title: isNaN _isnan —, _isnanf | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- NAN (not a number)
- _isnan function
- IEEE floating-point representation
- Not a Number (NANs)
- isnan function
ms.assetid: 391fbc5b-89a4-4fba-997e-68f1131caf82
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: baf92397087ebbac27c7fea8cf5f524b33736b19
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32401155"
---
# <a name="isnan-isnan-isnanf"></a>isNaN _isnan —, _isnanf

Testy, jeśli wartość zmiennoprzecinkowa nie jest liczbą (NAN).

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

W języku C **isnan** makro i **_isnan —** i **_isnanf** funkcje zwracają wartość niezerową, jeśli argument *x* jest wartością typu NAN; w przeciwnym razie ich Zwraca 0.

W języku C++ **isnan** szablonu funkcje zwracają **true** Jeśli argument *x* jest wartością typu NAN; w przeciwnym razie zwraca **false**.

## <a name="remarks"></a>Uwagi

C **isnan** makro i **_isnan —** i **_isnanf** funkcji testowania wartość zmiennoprzecinkowa *x*, zwracając wartość niezerową, jeśli *x* nie jest wartością liczbą (NAN). NAN jest generowany, gdy wynik operacji zmiennoprzecinkowej nie może być reprezentowany w formacie zmiennoprzecinkowej IEEE-754 dla określonego typu. Informacje, jak NAN są reprezentowane dla danych wyjściowych, zobacz [printf](printf-printf-l-wprintf-wprintf-l.md).

Podczas kompilacji jako C++, **isnan** makro nie jest zdefiniowany i **isnan** funkcji szablonu jest zdefiniowany w zamian. Zwraca wartość typu **bool** zamiast liczbą całkowitą.

**_Isnan —** i **_isnanf** funkcje są określone firmy Microsoft. **_Isnanf** funkcja jest dostępna, gdy kompilowany dla x64 tylko.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek (C)|Wymaganego nagłówka (C++)|
|-------------|---------------------------|-------------------------------|
|**isNaN —**, **_isnanf**|\<math.h>|\<Math.h > lub \<cmath >|
|**_isnan —**|\<float.h>|\<float.h — > lub \<cfloat — >|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
[_finite, _finitef](finite-finitef.md)<br/>
[_fpclass, _fpclassf](fpclass-fpclassf.md)<br/>
