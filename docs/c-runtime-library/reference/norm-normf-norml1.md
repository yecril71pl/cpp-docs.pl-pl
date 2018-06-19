---
title: normy, normf, norml | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/05/2018
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
ms.workload:
- cplusplus
ms.openlocfilehash: 272f43a7b92c069da8fc4eda64a678ff38efd6ab
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32401132"
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

Ponieważ C++ pozwala przeładowanie, można wywoływać przeciążenia **normy** które trwają **_Fcomplex** lub **_Lcomplex** wartości i wróć **float** lub **podwójnej długości** wartości. W programie C **normy** zawsze ma **_Dcomplex** wartości i zwraca **podwójne** wartość.

## <a name="requirements"></a>Wymagania

|Procedura|Nagłówek C|Nagłówek C++|
|-------------|--------------|------------------|
|**norm —**, **normf**, **norml**|\<complex.h>|\<complex.h>|

**_Fcomplex**, **_Dcomplex**, i **_Lcomplex** typy są specyficzne dla firmy Microsoft odpowiedniki niezaimplementowana natywnych typów C99 **float _Complex** , **podwójne _Complex**, i **_Complex podwójnej długości**odpowiednio.  Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[creal, crealf, creall](creal-crealf-creall.md)<br/>
[cproj, cprojf, cprojl](cproj-cprojf-cprojl.md)<br/>
[conj, conjf, conjl](conj-conjf-conjl.md)<br/>
[cimag, cimagf, cimagl](cimag-cimagf-cimagl.md)<br/>
[carg, cargf, cargl](carg-cargf-cargl.md)<br/>
[cabs, cabsf, cabsl](cabs-cabsf-cabsl.md)<br/>
