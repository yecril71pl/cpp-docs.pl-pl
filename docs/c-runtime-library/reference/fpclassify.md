---
title: fpclassify
ms.date: 04/05/2018
api_name:
- fpclassify
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
api_type:
- HeaderDef
f1_keywords:
- fpclassify
- math/fpclassify
helpviewer_keywords:
- fpclassify macro
- fpclassify function
ms.assetid: bf549499-7ff9-4a58-8692-f2d1cb6bab81
ms.openlocfilehash: e9b5aa1f7dc20cc920a51c2c36371eb907469875
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957066"
---
# <a name="fpclassify"></a>fpclassify

Zwraca klasyfikację zmiennoprzecinkową argumentu.

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
Wartość zmiennoprzecinkowa do przetestowania.

## <a name="return-value"></a>Wartość zwracana

**fpclassify —** zwraca liczbę całkowitą wskazującą klasę zmiennoprzecinkową argumentu *x*. W tej tabeli przedstawiono możliwe wartości zwrócone przez **fpclassify —** , zdefiniowane w \<Math. h >.

|Wartość|Opis|
|-----------|-----------------|
|**FP_NAN**|Cichy, sygnalizujący lub nieokreślony NaN|
|**FP_INFINITE**|Dodatnia lub ujemna nieskończoność|
|**FP_NORMAL**|Dodatnia lub negatywna znormalizowana wartość różna od zera|
|**FP_SUBNORMAL**|Wartość dodatnia lub ujemna nieznormalizowana|
|**FP_ZERO**|Dodatnia lub ujemna wartość zerowa|

## <a name="remarks"></a>Uwagi

W C, **fpclassify —** to makro; w C++programie **fpclassify —** jest funkcją przeciążoną przy użyciu typów argumentów **zmiennoprzecinkowych**, **Double**lub **Long** **Double**. W obu przypadkach zwracana wartość zależy od typu obowiązywania wyrażenia argumentu, a nie na żadnej pośredniej reprezentacji. Na przykład normalna **Podwójna** lub **długa** **Podwójna** wartość może stać się nieskończonością, nienormalną lub zerem wartość w przypadku przekonwertowania na typ **float**.

## <a name="requirements"></a>Wymagania

|Funkcja/makro|Wymagany nagłówek (C)|Wymagany nagłówek (C++)|
|---------------------|---------------------------|-------------------------------|
|**fpclassify**|\<math.h>|\<Math. h > lub \<cmath >|

Makra **fpclassify —** i funkcje **fpclassify —** są zgodne ze specyfikacjami ISO C99 i c++ 11. Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
