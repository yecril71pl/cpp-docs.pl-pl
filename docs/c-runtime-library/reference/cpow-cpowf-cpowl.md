---
title: cpow, cpowf, cpowl
ms.date: 11/04/2016
api_name:
- cpow
- cpowf
- cpowl
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
ms.openlocfilehash: 005bafd4b19164f5c85be839a90fc7d5259d61bf
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942702"
---
# <a name="cpow-cpowf-cpowl"></a>cpow, cpowf, cpowl

Pobiera wartość liczby podniesionej do określonej potęgi, gdzie podstawa i wykładnik są liczbami złożonymi. Ta funkcja ma rozgałęzienie do wykładniki wzdłuż ujemnej osi rzeczywistej.

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
Baza.

*y*<br/>
Wykładnik.

## <a name="return-value"></a>Wartość zwracana

Wartość *x* podniesiona do potęgi *y* z gałęzią wyciętych dla *x* wzdłuż ujemnej osi rzeczywistej.

## <a name="remarks"></a>Uwagi

Ponieważ C++ pozwala na Przeciążenie, można wywoływać przeciążenia **cpow** , które pobierają i zwracają wartości **_Fcomplex** i **_Lcomplex** . W programie C **cpow** zawsze przyjmuje i zwraca wartość **_Dcomplex** .

## <a name="requirements"></a>Wymagania

|Procedura|Nagłówek języka C|C++nagłówki|
|-------------|--------------|------------------|
|**cpow**, **cpowf**, **cpowl**|\<complex.h>|\<ccomplex>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[cexp, cexpf, cexpl](cexp-cexpf-cexpl.md)<br/>
[clog10, clog10f, clog10l](clog10-clog10f-clog10l.md)<br/>
[clog, clogf, clogl](clog-clogf-clogl.md)<br/>
