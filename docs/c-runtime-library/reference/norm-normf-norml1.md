---
title: normy, normf, norml | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 03/30/2018
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
apiname:
- norm
- normf
- norml
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
- norm
- normf
- norml
- complex/norm
- complex/normf
- complex/norml
dev_langs:
- C++
helpviewer_keywords:
- norm function
- normf function
- norml function
ms.assetid: 9786ecfe-0019-4553-b378-0af6c691e15c
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 28c8e05dfc2cc9e42584324a78ba14f37a9b951d
ms.sourcegitcommit: 0523c88b24d963c33af0529e6ba85ad2c6ee5afb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2018
---
# <a name="norm-normf-norml"></a>normy normf, norml

Pobiera kwadratów wielkość liczbą.

## <a name="syntax"></a>Składnia

```C
double norm( _Dcomplex z );
float normf( _Fcomplex z );
long double norml( _Lcomplex z );
```

```cpp
float norm( _Fcomplex z );  // C++ only
long double norm( _Lcomplex z );  // C++ only
```

### <a name="parameters"></a>Parametry

*z*<br/>
Liczba złożonych.

## <a name="return-value"></a>Wartość zwracana

Wielkość kwadratów *z*.

## <a name="remarks"></a>Uwagi

Ponieważ C++ pozwala przeładowanie, można wywoływać przeciążenia `norm` które trwają **_Fcomplex** lub **_Lcomplex** wartości i wróć **float** lub **długa Podwójna** wartości. W programie C `norm` zawsze ma **_Dcomplex** wartości i zwraca **podwójne** wartość.

## <a name="requirements"></a>Wymagania

|Procedura|Nagłówek C|Nagłówek C++|
|-------------|--------------|------------------|
|`norm`, `normf`, `norml`|\<complex.h>|\<ccomplex >|

**_Fcomplex**, **_Dcomplex**, i **_Lcomplex** typy są specyficzne dla firmy Microsoft odpowiedniki niezaimplementowana natywnych typów C99 **float _Complex** , **podwójne _Complex**, i **_Complex podwójnej długości**odpowiednio.  Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Alfabetyczne zestawienie funkcji](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[creal, crealf, creall](../../c-runtime-library/reference/creal-crealf-creall.md)<br/>
[cproj, cprojf, cprojl](../../c-runtime-library/reference/cproj-cprojf-cprojl.md)<br/>
[conj, conjf, conjl](../../c-runtime-library/reference/conj-conjf-conjl.md)<br/>
[cimag, cimagf, cimagl](../../c-runtime-library/reference/cimag-cimagf-cimagl.md)<br/>
[carg, cargf, cargl](../../c-runtime-library/reference/carg-cargf-cargl.md)<br/>
[cabs, cabsf, cabsl](../../c-runtime-library/reference/cabs-cabsf-cabsl.md)<br/>
