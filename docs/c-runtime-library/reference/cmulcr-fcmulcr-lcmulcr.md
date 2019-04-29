---
title: _Cmulcr, _FCmulcr, _LCmulcr
ms.date: 03/30/2018
apiname:
- _Cmulcr
- _FCmulcr
- _LCmulcr
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
- _Cmulcr
- _FCmulcr
- _LCmulcr
- complex/_Cmulcr
- complex/_FCmulcr
- complex/_LCmulcr
helpviewer_keywords:
- _Cmulcr function
- _FCmulcr function
- _LCmulcr function
ms.openlocfilehash: ce45b1b1081faba18d8532d3a55d1be877cf84e3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62340407"
---
# <a name="cmulcr-fcmulcr-lcmulcr"></a>_Cmulcr, _FCmulcr, _LCmulcr

Mnoży liczbę złożone przez liczbę zmiennoprzecinkową.

## <a name="syntax"></a>Składnia

```C
_Dcomplex _Cmulcr( _Dcomplex x, double y );
_Fcomplex _FCmulcr( _Fcomplex x, float y );
_Lcomplex _LCmulcr( _Lcomplex x, long double y );
```

### <a name="parameters"></a>Parametry

*x*<br/>
Jeden z argumentów złożone do pomnożenia.

*y*<br/>
Argument operacji zmiennoprzecinkowych do pomnożenia.

## <a name="return-value"></a>Wartość zwracana

A **_Dcomplex**, **_Fcomplex**, lub **_Lcomplex** strukturę, która reprezentuje złożonych iloczyn liczby zespolonej *x* i numer punktu flaoting *y*.

## <a name="remarks"></a>Uwagi

Ponieważ wbudowanych operatorów arytmetycznych, nie działają na implementacja firmy Microsoft, złożonych typów **_Cmulcr**, **_FCmulcr**, i **_LCmulcr** funkcji Uprość mnożenia typy złożone przez typów zmiennoprzecinkowych.

## <a name="requirements"></a>Wymagania

|Procedura|Nagłówek języka C|Nagłówek języka C++|
|-------------|--------------|------------------|
|**_Cmulcr**, **_FCmulcr**, **_LCmulcr**|\<complex.h>|\<complex.h>|

Te funkcje są specyficzne dla firmy Microsoft. Typy **_Dcomplex**, **_Fcomplex**, i **_Lcomplex** są specyficzne dla firmy Microsoft odpowiedniki typów natywnych niezaimplementowana C99 **double _complex —** , **float _complex —**, i **_complex typu long double —**, odpowiednio. Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[_Cbuild, _FCbuild, _LCbuild](cbuild-fcbuild-lcbuild.md)<br/>
[_Cmulcc, _FCmulcc, _LCmulcc](cmulcc-fcmulcc-lcmulcc.md)<br/>
[norm, normf, norml](norm-normf-norml1.md)<br/>
[cproj, cprojf, cprojl](cproj-cprojf-cprojl.md)<br/>
[conj, conjf, conjl](conj-conjf-conjl.md)<br/>
[creal, crealf, creall](creal-crealf-creall.md)<br/>
[cimag, cimagf, cimagl](cimag-cimagf-cimagl.md)<br/>
[carg, cargf, cargl](carg-cargf-cargl.md)<br/>
[cabs, cabsf, cabsl](cabs-cabsf-cabsl.md)<br/>
