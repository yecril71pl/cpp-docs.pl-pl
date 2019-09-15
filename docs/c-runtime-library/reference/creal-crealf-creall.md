---
title: creal, crealf, creall
ms.date: 03/30/2018
api_name:
- creal
- crealf
- creall
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
- creal
- crealf
- creall
- complex/creal
- complex/crealf
- complex/creall
helpviewer_keywords:
- creal function
- crealf function
- creall function
ms.assetid: fa3ac62f-7aa3-4238-a71f-d6b00cd0c7c8
ms.openlocfilehash: ebd52a23765177d74f2bff5660f806ee5c4a9573
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942613"
---
# <a name="creal-crealf-creall"></a>creal, crealf, creall

Pobiera rzeczywistą część liczby zespolonej.

## <a name="syntax"></a>Składnia

```C
double creal( _Dcomplex z );
float crealf( _Fcomplex z );
long double creall( _Lcomplex z );
```

```cpp
float creal( _Fcomplex z );  // C++ only
long double creal( _Lcomplex z );  // C++ only
```

### <a name="parameters"></a>Parametry

*z*<br/>
Liczba złożona.

## <a name="return-value"></a>Wartość zwracana

Rzeczywista *część z.*

## <a name="remarks"></a>Uwagi

Ponieważ C++ pozwala na Przeciążenie, można wywoływać przeciążenia **Creal** , które pobierają wartości **_Fcomplex** lub **_Lcomplex** i zwracają wartości **zmiennoprzecinkowe** lub **długie Double** . W programie C **Creal** zawsze przyjmuje wartość **_Dcomplex** i zwraca wartość **podwójną** .

## <a name="requirements"></a>Wymagania

|Procedura|Nagłówek języka C|C++nagłówki|
|-------------|--------------|------------------|
|**Creal**, **crealf**, **creall**|\<complex.h>|\<ccomplex>|

Typy **_Fcomplex**, **_Dcomplex**i **_Lcomplex** to charakterystyczne dla firmy Microsoft ekwiwalenty niezaimplementowanych natywnych typów C99 **zmiennoprzecinkowych _Complex**, **podwójnie _Complex**i **Long podwójnie _Complex**. Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[_Cbuild, _FCbuild, _LCbuild](cbuild-fcbuild-lcbuild.md)<br/>
[norm, normf, norml](norm-normf-norml1.md)<br/>
[cproj, cprojf, cprojl](cproj-cprojf-cprojl.md)<br/>
[conj, conjf, conjl](conj-conjf-conjl.md)<br/>
[cimag, cimagf, cimagl](cimag-cimagf-cimagl.md)<br/>
[carg, cargf, cargl](carg-cargf-cargl.md)<br/>
[cabs, cabsf, cabsl](cabs-cabsf-cabsl.md)<br/>