---
title: _Cbuild _FCbuild, _LCbuild | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 03/30/2018
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
apiname:
- _Cbuild
- _FCbuild
- _LCbuild
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
- _Cbuild
- _FCbuild
- _LCbuild
- complex/_Cbuild
- complex/_FCbuild
- complex/_LCbuild
dev_langs:
- C++
helpviewer_keywords:
- _Cbuild function
- _FCbuild function
- _LCbuild function
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c6d567dc02715b9e55644b755b6d7360f2fe3d37
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32394390"
---
# <a name="cbuild-fcbuild-lcbuild"></a>_Cbuild, _FCbuild, _LCbuild

Tworzy liczbę złożone z rzeczywistą i urojony części.

## <a name="syntax"></a>Składnia

```C
_Dcomplex _Cbuild( double real, double imaginary );
_Fcomplex _FCbuild( float real, float imaginary );
_Lcomplex _LCbuild( long double real, long double imaginary );
```

### <a name="parameters"></a>Parametry

*rzeczywiste*<br/>
Część rzeczywista liczby złożonej do utworzenia.

*imaginary*<br/>
Wyrażenie Liczba_zespolona część liczby złożonej do utworzenia.

## <a name="return-value"></a>Wartość zwracana

A **_Dcomplex**, **_Fcomplex**, lub **_Lcomplex** strukturę, która reprezentuje liczby złożonej (*rzeczywistych*, *urojony*  \* i) do wartości zmiennoprzecinkowych określonego typu.

## <a name="remarks"></a>Uwagi

**_Cbuild**, **_FCbuild**, i **_LCbuild** funkcje uprościć tworzenie typów złożonych. Użyj [creal crealf, creall](creal-crealf-creall.md) i [cimag cimagf, cimagl](cimag-cimagf-cimagl.md) funkcji do pobrania rzeczywistą i urojony części reprezentowanej liczby złożone.

## <a name="requirements"></a>Wymagania

|Procedura|Nagłówek C|Nagłówek C++|
|-------------|--------------|------------------|
|**_Cbuild**, **_FCbuild**, **_LCbuild**|\<complex.h>|\<ccomplex >|

Te funkcje są specyficzne dla firmy Microsoft. Typy **_Dcomplex**, **_Fcomplex**, i **_Lcomplex** są specyficzne dla firmy Microsoft odpowiedniki typów natywnych niezaimplementowana C99 **_Complex podwójne** , **float _Complex**, i **_Complex podwójnej długości**odpowiednio. Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[_Cmulcc, _FCmulcc, _LCmulcc](cmulcc-fcmulcc-lcmulcc.md)<br/>
[_Cmulcr, _FCmulcr, _LCmulcr](cmulcr-fcmulcr-lcmulcr.md)<br/>
[normy normf, norml](norm-normf-norml1.md)<br/>
[cproj, cprojf, cprojl](cproj-cprojf-cprojl.md)<br/>
[conj, conjf, conjl](conj-conjf-conjl.md)<br/>
[creal, crealf, creall](creal-crealf-creall.md)<br/>
[cimag, cimagf, cimagl](cimag-cimagf-cimagl.md)<br/>
[carg, cargf, cargl](carg-cargf-cargl.md)<br/>
[cabs, cabsf, cabsl](cabs-cabsf-cabsl.md)<br/>
