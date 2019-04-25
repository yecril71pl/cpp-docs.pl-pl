---
title: fpclassify —
ms.date: 04/05/2018
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
ms.openlocfilehash: a25897a110d96923a45695d61f923dc7818c7e3a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62287944"
---
# <a name="fpclassify"></a>fpclassify —

Zwraca wartość zmiennoprzecinkową klasyfikacji argumentu.

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

**fpclassify —** zwraca wartość całkowitą, która wskazuje klasę zmiennoprzecinkową argumentu *x*. W poniższej tabeli przedstawiono możliwe wartości zwracane przez **fpclassify —** zdefiniowaną w \<math.h >.

|Wartość|Opis|
|-----------|-----------------|
|**FP_NAN**|Cichy, sygnalizowanie lub nieokreślony NaN|
|**FP_INFINITE**|Nieskończoność dodatnia lub ujemna|
|**FP_NORMAL**|Dodatnie lub ujemne różna od zera wartość znormalizowaną|
|**FP_SUBNORMAL**|Nieznormalizowana wartość dodatnia lub ujemna|
|**FP_ZERO**|Dodatnią lub ujemną wartość zero|

## <a name="remarks"></a>Uwagi

W języku C **fpclassify —** jest makrem; w języku C++, **fpclassify —** jest przeciążona, przy użyciu typów argumentu funkcji **float**, **double**, lub **długie** **double**. W obu przypadkach na efektywne typ wyrażenia argumentu, a nie na dowolnym reprezentacji pośredniej zależy od wartości zwracanej. Na przykład, jako normalny **double** lub **długie** **double** wartość może stać się nieskończoność, zdenormalizowany lub zero wartości podczas konwersji na **float**.

## <a name="requirements"></a>Wymagania

|Funkcja / — makro|Wymagany nagłówek (C)|Wymagany nagłówek (C++)|
|---------------------|---------------------------|-------------------------------|
|**fpclassify**|\<math.h>|\<Math.h > lub \<cmath >|

**Fpclassify —** — makro i **fpclassify —** funkcje są zgodne z ISO C99 i C ++ 11 specyfikacji. Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
