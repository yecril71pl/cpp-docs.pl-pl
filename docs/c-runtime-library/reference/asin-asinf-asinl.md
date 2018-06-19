---
title: ASIN asinf —, asinl — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- asinf
- asinl
- asin
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
- asin
- asinl
- asinf
dev_langs:
- C++
helpviewer_keywords:
- asin function
- asinl function
- asinf function
- trigonometric functions
- arcsine function
ms.assetid: ca05f9ea-b711-49f6-9f32-2f4019abfd69
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ee65e4c8ce884ac42de35a23c81dbf5009dd1185
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32393280"
---
# <a name="asin-asinf-asinl"></a>asin, asinf, asinl

Oblicza sinus.

## <a name="syntax"></a>Składnia

```C
double asin( double x );
float asinf ( float x );
long double asinl( long double x );
```

```cpp
float asin( float x );  // C++ only
long double asin( long double x );  // C++ only
```

### <a name="parameters"></a>Parametry

*x*<br/>
Wartość, którego sinus ma zostać obliczona.

## <a name="return-value"></a>Wartość zwracana

**Asin** funkcja Zwraca arcus sinus (Funkcja sinus) *x* w zakresie - π/2 na radiany π/2.

Domyślnie jeśli *x* jest mniejsza niż -1 lub większą niż 1, **asin** zwraca nieokreślony.

|Dane wejściowe|Wyjątek SEH|Matherr — wyjątek|
|-----------|-------------------|-----------------------|
|± ∞|**NIEPRAWIDŁOWY**|**_DOMAIN —**|
|GRANICACH **QNAN**, **IND**|brak|**_DOMAIN —**|
|&#124;x&#124;>1|**NIEPRAWIDŁOWY**|**_DOMAIN —**|

## <a name="remarks"></a>Uwagi

Ponieważ C++ pozwala przeładowanie, można wywoływać przeciążenia **asin** z **float** i **długi** **podwójne** wartości. W programie C **asin** zawsze przyjmuje i zwraca **podwójne**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek (C)|Wymaganego nagłówka (C++)|
|-------------|---------------------|-|
|**ASIN**, **asinf —**, **asinl —**|\<math.h>|\<cmath > lub \<math.h >|

## <a name="example"></a>Przykład

Aby uzyskać więcej informacji, zobacz [acos acosf —, acosl —](acos-acosf-acosl.md).

## <a name="see-also"></a>Zobacz także

[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
[acos, acosf, acosl](acos-acosf-acosl.md)<br/>
[atan, atanf, atanl, atan2, atan2f, atan2l](atan-atanf-atanl-atan2-atan2f-atan2l.md)<br/>
[COS cosf —, cosl —](cos-cosf-cosl.md)<br/>
[_matherr](matherr.md)<br/>
[sin, sinf, sinl](sin-sinf-sinl.md)<br/>
[tan, tanf, tanl](tan-tanf-tanl.md)<br/>
