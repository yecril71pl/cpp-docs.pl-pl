---
title: fetestexcept
ms.date: 04/05/2018
apiname:
- fetestexcept
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- fetestexcept
- fenv/fetestexcept
helpviewer_keywords:
- fetestexept function
ms.assetid: ca4dc43f-5573-440d-bc19-ead7571b13dc
ms.openlocfilehash: ed75ab0ff13029f6ec10c1aafbcb7f7b23b46fd6
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/10/2018
ms.locfileid: "51521366"
---
# <a name="fetestexcept"></a>fetestexcept

Określa, które z określonego wyjątku zmiennoprzecinkowego flagi stanu aktualnie ustawione.

## <a name="syntax"></a>Składnia

```C
int fetestexcept(
   int excepts
);
```

### <a name="parameters"></a>Parametry

*z wyjątkiem*<br/>
Bitowe OR flagi stanu zmiennoprzecinkowego do testowania.

## <a name="return-value"></a>Wartość zwracana

W przypadku powodzenia zwraca maski bitów zawierający bitowe OR makra wyjątków zmiennoprzecinkowych, które odpowiadają flagi stanu wyjątek aktualnie ustawiona. Zwraca wartość 0, jeśli żadna z tych wyjątków są ustawione.

## <a name="remarks"></a>Uwagi

Użyj funkcji fetestexcept ustalenie, wyjątki, które zostały zgłoszone przez zmiennoprzecinkowy operacji. Użyj *z wyjątkiem* parametru, aby określić które flagi stanu wyjątków do testowania. **Fetestexcept** funkcja używa tych makr wyjątków zdefiniowanych w \<fenv.h > w *z wyjątkiem* i wartość zwracana:

|Makra wyjątków|Opis|
|---------------------|-----------------|
|FE_DIVBYZERO|Wystąpił błąd singularity lub pole w starszej operacji zmiennoprzecinkowej; Utworzono wartości nieskończonej.|
|FE_INEXACT|Wymuszono funkcji round przechowywanych wynikiem wcześniejszych operacji zmiennoprzecinkowej.|
|FE_INVALID|Wystąpił błąd domeny w starszej operacji zmiennoprzecinkowej.|
|FE_OVERFLOW|Wystąpił błąd zakresu; wynik operacji zmiennoprzecinkowej wcześniej była zbyt duża, aby mogły być reprezentowane.|
|FE_UNDERFLOW|Wcześniej wyniku operacji zmiennoprzecinkowej był za mały, aby mogły być reprezentowane w o pełnej dokładności; wartość została utworzona.|
|FE_ALLEXCEPT|Bitowe OR wszystkich obsługiwane wyjątki zmiennoprzecinkowe.|

Określony *z wyjątkiem* argument może być 0, jednym z makr wyjątków dotyczących liczb zmiennoprzecinkowych obsługiwanych lub operatora testu koniunkcji lub dwóch lub większej liczby makra. Wpływ wszelkich innych *z wyjątkiem* wartość argumentu jest niezdefiniowana.

Aby użyć tej funkcji, należy wyłączyć funkcję optymalizacji zmiennopozycyjnych, które mogą uniemożliwić dostęp przy użyciu `#pragma fenv_access(on)` dyrektywy przed wywołaniem. Aby uzyskać więcej informacji, zobacz [fenv_access](../../preprocessor/fenv-access.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Nagłówek języka C|Nagłówek języka C++|
|--------------|--------------|------------------|
|**fetestexcept**|\<fenv.h>|\<cfenv>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[feclearexcept](feclearexcept1.md)<br/>
[feraiseexcept](feraiseexcept.md)<br/>
