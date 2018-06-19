---
title: fpclassify — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/05/2018
ms.topic: reference
apiname:
- fpclassify
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
apitype: HeaderDef
f1_keywords:
- fpclassify
- math/fpclassify
helpviewer_keywords:
- fpclassify macro
- fpclassify function
ms.assetid: bf549499-7ff9-4a58-8692-f2d1cb6bab81
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: da55cb87804d178d5a305ed466aa498de4bc1ee5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32398435"
---
# <a name="fpclassify"></a>fpclassify —

Zwraca zmiennoprzecinkowe klasyfikacji argumentu.

## <a name="syntax"></a>Składnia

```C
int fpclassify(
   /* floating-point */ x
);

int fpclassify(
   float x
); // C++ only

int fpclassify(
   double x
); // C++ only

int fpclassify(
   long double x
); // C++ only

```

### <a name="parameters"></a>Parametry

*x*<br/>
Wartość zmiennoprzecinkowa do testowania.

## <a name="return-value"></a>Wartość zwracana

**fpclassify —** zwraca wartość wskazującą zmiennoprzecinkowe klasy argumentu *x*. W tej tabeli przedstawiono możliwe wartości zwracane przez **fpclassify —** zdefiniowanej w \<math.h >.

|Wartość|Opis|
|-----------|-----------------|
|**FP_NAN**|Cichy, sygnalizowania lub nieokreślony NaN|
|**FP_INFINITE**|Infinity dodatnie lub ujemne|
|**FP_NORMAL**|Dodatnie lub ujemne niezerową wartość znormalizowaną|
|**FP_SUBNORMAL**|Nieznormalizowana wartość dodatnią lub ujemną|
|**FP_ZERO**|Dodatnią lub ujemną wartość zero|

## <a name="remarks"></a>Uwagi

W języku C **fpclassify —** jest makrem; w języku C++ **fpclassify —** jest przeciążony przy użyciu typów argumentu funkcji **float**, **podwójne**, lub **długi** **podwójne**. W obu przypadkach wartość zwracana zależy od wprowadzenia typu wyrażenia argumentu, a nie na dowolnym reprezentacji pośredniej. Na przykład zwykłym **podwójne** lub **długi** **podwójne** wartość może stać się nieskończoności, Brak reprezentacji zmiennoprzecinkowej lub zero wartości po konwersji na **float**.

## <a name="requirements"></a>Wymagania

|Funkcja/makra|Wymagany nagłówek (C)|Wymaganego nagłówka (C++)|
|---------------------|---------------------------|-------------------------------|
|**fpclassify**|\<math.h>|\<Math.h > lub \<cmath >|

**Fpclassify —** makro i **fpclassify —** funkcje odpowiadają ISO C99 i C ++ 11 specyfikacji. Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
