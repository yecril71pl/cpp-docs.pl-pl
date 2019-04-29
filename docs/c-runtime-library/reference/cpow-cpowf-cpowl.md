---
title: cpow cpowf, cpowl
ms.date: 11/04/2016
apiname:
- cpow
- cpowf
- cpowl
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
- cpow
- cpowf
- cpowl
- complex/cpow
- complex/cpowf
- complex/copwl
helpviewer_keywords:
- cpow function
- cpowf function
- complex/cpowl function
ms.assetid: 83fe2187-22b7-4295-ab16-4d77abdbb80b
ms.openlocfilehash: 588c437a01237de297e1db31fb2c507eb1145d90
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62339848"
---
# <a name="cpow-cpowf-cpowl"></a>cpow cpowf, cpowl

Pobiera wartość liczbę podniesioną do wskazanej potęgi, w których liczby zespolone base i wykładnika. Funkcja ta ma gałąź Wytnij wykładnika potęgi rzeczywistych osi ujemna.

## <a name="syntax"></a>Składnia

```C
_Dcomplex cpow(
   _Dcomplex x, _Dcomplex y
);
_Fcomplex cpow(
   _Fcomplex x, _Fcomplex y
);  // C++ only
_Lcomplex cpow(
   _Lcomplex x, _Lcomplex y
);  // C++ only
_Fcomplex cpowf(
   _Fcomplex x, _Fcomplex y
);
_Lcomplex cpowl(
   _Lcomplex x, _Lcomplex y
);
```

### <a name="parameters"></a>Parametry

*x*<br/>
Podstawa.

*y*<br/>
Wykładnik potęgi.

## <a name="return-value"></a>Wartość zwracana

Wartość *x* podniesione do potęgi równej *y* z gałęzią Wytnij dla *x* rzeczywistych osi ujemna.

## <a name="remarks"></a>Uwagi

Ponieważ C++ pozwala na przeciążenie, można wywoływać przeciążenia **cpow** przyjmujące i zwracające **_Fcomplex** i **_Lcomplex** wartości. W programie C **cpow** zawsze przyjmuje i zwraca **_Dcomplex** wartości.

## <a name="requirements"></a>Wymagania

|Procedura|Nagłówek języka C|Nagłówek języka C++|
|-------------|--------------|------------------|
|**cpow**, **cpowf**, **cpowl**|\<complex.h>|\<ccomplex>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[cexp, cexpf, cexpl](cexp-cexpf-cexpl.md)<br/>
[clog10, clog10f, clog10l](clog10-clog10f-clog10l.md)<br/>
[clog, clogf, clogl](clog-clogf-clogl.md)<br/>
