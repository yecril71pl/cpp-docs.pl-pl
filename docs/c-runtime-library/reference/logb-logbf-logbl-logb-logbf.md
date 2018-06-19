---
title: logb —, logbf —, logbl —, _logb —, _logbf — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- logb
- _logb
- _logbl
- logbf
- logbl
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
- logb
- logbl
- _logb
- _logbf
- logbf
dev_langs:
- C++
helpviewer_keywords:
- _logbf function
- mantissas, floating-point variables
- logbf function
- _logb function
- exponent, floating-point numbers
- logbl function
- logb function
- floating-point functions
- floating-point functions, mantissa and exponent
- exponents and mantissas
ms.assetid: 780c4daa-6fe6-4fbc-9412-4c1ba1a1766f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f09a243994112c3ce19d72213391e09ba23c3c4c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32402777"
---
# <a name="logb-logbf-logbl-logb-logbf"></a>logb, logbf, logbl, _logb, _logbf

Wyodrębnianie wartości wykładnika liczb zmiennoprzecinkowych argumentu.

## <a name="syntax"></a>Składnia

```C
double logb(
   double x
);
float logb(
   float x
); // C++ only
long double logb(
   long double x
); // C++ only
float logbf(
   float x
);
long double logbl(
   long double x
);
double _logb(
   double x
);
float _logbf(
   float x
);
```

### <a name="parameters"></a>Parametry

*x*<br/>
Wartość zmiennoprzecinkowa.

## <a name="return-value"></a>Wartość zwracana

**logb —** zwraca wartość nieobciążonej wykładnika *x* jako liczbę całkowitą ze znakiem reprezentowane jako wartości zmiennoprzecinkowej.

## <a name="remarks"></a>Uwagi

**Logb —** funkcje wyodrębnienie wykładniczej wartości argumentu zmiennoprzecinkowego *x*, tak jakby *x* były reprezentowane z zakresem nieskończoną. Jeśli argument *x* jest nieznormalizowane, jest traktowana tak, jakby był on znormalizowany.

Ponieważ C++ pozwala przeładowanie, można wywoływać przeciążenia **logb —** który przyjmować i zwracać **float** lub **długi** **podwójne** wartości. W programie C **logb —** zawsze przyjmuje i zwraca **podwójne**.

|Dane wejściowe|Wyjątek SEH|Matherr — wyjątek|
|-----------|-------------------|-----------------------|
|GRANICACH QNAN, IND|Brak|_DOMAIN|
|± 0|ZERODIVIDE|—|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_logb —**|\<float.h>|
|**logb —**, **logbf —**, **logbl —**, **_logbf —**|\<math.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Zobacz także

[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
[frexp](frexp.md)<br/>
