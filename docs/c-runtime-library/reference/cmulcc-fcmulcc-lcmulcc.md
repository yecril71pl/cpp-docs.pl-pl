---
title: _Cmulcc, _FCmulcc, _LCmulcc
ms.date: 03/30/2018
api_name:
- _Cmulcc
- _FCmulcc
- _LCmulcc
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
- _Cmulcc
- _FCmulcc
- _LCmulcc
- complex/_Cmulcc
- complex/_FCmulcc
- complex/_LCmulcc
helpviewer_keywords:
- _Cmulcc function
- _FCmulcc function
- _LCmulcc function
ms.openlocfilehash: fc21f8cbd2103993bc2b3e36020c57c8520f04a1
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939076"
---
# <a name="_cmulcc-_fcmulcc-_lcmulcc"></a>_Cmulcc, _FCmulcc, _LCmulcc

Mnoży dwie liczby zespolone.

## <a name="syntax"></a>Składnia

```C
_Dcomplex _Cmulcc( _Dcomplex x, _Dcomplex y );
_Fcomplex _FCmulcc( _Fcomplex x, _Fcomplex y );
_Lcomplex _LCmulcc( _Lcomplex x, _Lcomplex y );
```

### <a name="parameters"></a>Parametry

*x*<br/>
Jeden z złożonych argumentów operacji do pomnożenia.

*y*<br/>
Drugi argument operacji złożonej do pomnożenia.

## <a name="return-value"></a>Wartość zwracana

Struktura **_Dcomplex**, **_Fcomplex**lub **_Lcomplex** , która reprezentuje złożony iloczyn liczby zespolonej *x* i *y*.

## <a name="remarks"></a>Uwagi

Ponieważ wbudowane operatory arytmetyczne nie działają w implementacji firmy Microsoft typów złożonych, funkcje **_Cmulcc**, **_FCmulcc**i **_LCmulcc** upraszczają mnożenie typów złożonych.

## <a name="requirements"></a>Wymagania

|Procedura|Nagłówek języka C|C++nagłówki|
|-------------|--------------|------------------|
|**_Cmulcc**, **_FCmulcc**, **_LCmulcc**|\<complex.h>|\<complex.h>|

Te funkcje są specyficzne dla firmy Microsoft. Typy **_Dcomplex**, **_Fcomplex**i **_Lcomplex** są odpowiednikami specyficznymi dla firmy Microsoft dla niewdrożonych typów natywnych C99, odpowiednio **_Complex**, **float _Complex**i **Long podwójnie _Complex**. Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[_Cbuild, _FCbuild, _LCbuild](cbuild-fcbuild-lcbuild.md)<br/>
[_Cmulcr, _FCmulcr, _LCmulcr](cmulcr-fcmulcr-lcmulcr.md)<br/>
[norm, normf, norml](norm-normf-norml1.md)<br/>
[cproj, cprojf, cprojl](cproj-cprojf-cprojl.md)<br/>
[conj, conjf, conjl](conj-conjf-conjl.md)<br/>
[creal, crealf, creall](creal-crealf-creall.md)<br/>
[cimag, cimagf, cimagl](cimag-cimagf-cimagl.md)<br/>
[carg, cargf, cargl](carg-cargf-cargl.md)<br/>
[cabs, cabsf, cabsl](cabs-cabsf-cabsl.md)<br/>
