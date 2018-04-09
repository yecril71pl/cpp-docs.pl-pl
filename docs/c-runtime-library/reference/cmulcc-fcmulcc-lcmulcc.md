---
title: _Cmulcc _FCmulcc, _LCmulcc | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 03/30/2018
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
apiname:
- _Cmulcc
- _FCmulcc
- _LCmulcc
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
- _Cmulcc
- _FCmulcc
- _LCmulcc
- complex/_Cmulcc
- complex/_FCmulcc
- complex/_LCmulcc
dev_langs:
- C++
helpviewer_keywords:
- _Cmulcc function
- _FCmulcc function
- _LCmulcc function
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d6e0158543a90135cb10e76f7c8df0102f5c6a68
ms.sourcegitcommit: 0523c88b24d963c33af0529e6ba85ad2c6ee5afb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2018
---
# <a name="cmulcc-fcmulcc-lcmulcc"></a>_Cmulcc, _FCmulcc, _LCmulcc

Mnoży dwie liczby złożone.

## <a name="syntax"></a>Składnia

```C
_Dcomplex _Cmulcc( _Dcomplex x, _Dcomplex y );
_Fcomplex _FCmulcc( _Fcomplex x, _Fcomplex y );
_Lcomplex _LCmulcc( _Lcomplex x, _Lcomplex y );
```

### <a name="parameters"></a>Parametry

*x*<br/>
Jeden z argumentów złożonych Aby pomnożyć.

*y*<br/>
Inne złożonych operandu na wielokrotnie.

## <a name="return-value"></a>Wartość zwracana

A **_Dcomplex**, **_Fcomplex**, lub **_Lcomplex** strukturę, która reprezentuje złożonych iloczyn liczb złożone *x* i *y*.

## <a name="remarks"></a>Uwagi

Ponieważ wbudowanych operatorów arytmetycznych nie działają na przez firmę Microsoft implementacją typów złożonych **_Cmulcc**, **_FCmulcc**, i **_LCmulcc** funkcji Uproszczenie mnożenia typów złożonych.

## <a name="requirements"></a>Wymagania

|Procedura|Nagłówek C|Nagłówek C++|
|-------------|--------------|------------------|
|`_Cmulcc`,`_FCmulcc`, `_LCmulcc`|\<complex.h>|\<ccomplex >|

Te funkcje są specyficzne dla firmy Microsoft. Typy **_Dcomplex**, **_Fcomplex**, i **_Lcomplex** są specyficzne dla firmy Microsoft odpowiedniki typów natywnych niezaimplementowana C99 **_Complex podwójne** , **float _Complex**, i **_Complex podwójnej długości**odpowiednio. Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Alfabetyczne zestawienie funkcji](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[_Cbuild, _FCbuild, _LCbuild](../../c-runtime-library/reference/cbuild-fcbuild-lcbuild.md)<br/>
[_Cmulcr, _FCmulcr, _LCmulcr](../../c-runtime-library/reference/cmulcr-fcmulcr-lcmulcr.md)<br/>
[normy normf, norml](../../c-runtime-library/reference/norm-normf-norml1.md)<br/>
[cproj, cprojf, cprojl](../../c-runtime-library/reference/cproj-cprojf-cprojl.md)<br/>
[conj, conjf, conjl](../../c-runtime-library/reference/conj-conjf-conjl.md)<br/>
[creal, crealf, creall](../../c-runtime-library/reference/creal-crealf-creall.md)<br/>
[cimag, cimagf, cimagl](../../c-runtime-library/reference/cimag-cimagf-cimagl.md)<br/>
[carg, cargf, cargl](../../c-runtime-library/reference/carg-cargf-cargl.md)<br/>
[cabs, cabsf, cabsl](../../c-runtime-library/reference/cabs-cabsf-cabsl.md)<br/>
