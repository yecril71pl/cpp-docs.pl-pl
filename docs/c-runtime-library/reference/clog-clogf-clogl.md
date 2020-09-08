---
title: clog, clogf, clogl
description: Dokumentacja interfejsu API dla CLOG, clogf i clogl; który pobiera logarytm naturalny liczby zespolonej, z rozgałęzieniem na ujemną oś rzeczywistą.
ms.date: 11/04/2016
api_name:
- clog
- clogf
- clogl
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
- clog
- clogf
- clogl
- complex/clog
- complex/clogf
- complex/clogl
helpviewer_keywords:
- clog function
- clogf function
- clogl function
ms.assetid: 870b9b0b-6618-46f3-bfcf-da595cbd5e18
ms.openlocfilehash: 255f83a93c5c7a0c724fad143f028c2832be3173
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2020
ms.locfileid: "89555075"
---
# <a name="clog-clogf-clogl"></a>clog, clogf, clogl

Pobiera logarytm naturalny liczby zespolonej z rozgałęzieniem na ujemną oś rzeczywistą.

## <a name="syntax"></a>Składnia

```C
_Dcomplex clog(
   _Dcomplex z
);
_Fcomplex clog(
   _Fcomplex z
);  // C++ only
_Lcomplex clog(
   _Lcomplex z
);  // C++ only
_Fcomplex clogf(
   _Fcomplex z
);
_Lcomplex clogl(
   _Lcomplex z
);
```

### <a name="parameters"></a>Parametry

*porządku*\
Podstawa logarytmu.

## <a name="return-value"></a>Wartość zwracana

Logarytm naturalny *z.* Wynik nie jest powiązany wzdłuż osi rzeczywistej, a w interwale [-iπ, + iπ] wzdłuż osi urojonej.

Możliwe wartości zwracane to:

|parametr z|Wartość zwracana|
|-----------------|------------------|
|Dodatnie|Logarytm dziesiętny z|
|Zero|- ∞|
|Ujemne|NaN|
|NaN|NaN|
|+ ∞|+ ∞|

## <a name="remarks"></a>Uwagi

Ponieważ C++ pozwala na Przeciążenie, można wywoływać przeciążenia **CLOG** , które pobierają i zwracają wartości **_Fcomplex** i **_Lcomplex** . W programie C **CLOG** zawsze przyjmuje i zwraca wartość **_Dcomplex** .

## <a name="requirements"></a>Wymagania

|Procedura|Nagłówek języka C|Nagłówek C++|
|-------------|--------------|------------------|
|**CLOG**,               **clogf**, **clogl**|\<complex.h>|\<ccomplex>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[cexp, cexpf, cexpl](cexp-cexpf-cexpl.md)<br/>
[cpow, cpowf, cpowl](cpow-cpowf-cpowl.md)<br/>
[clog10, clog10f, clog10l](clog10-clog10f-clog10l.md)<br/>
