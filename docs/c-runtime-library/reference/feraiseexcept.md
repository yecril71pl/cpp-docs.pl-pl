---
title: feraiseexcept
ms.date: 04/05/2018
apiname:
- feraiseexcept
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
apitype: HeaderDef
f1_keywords:
- feraiseexcept
- fenv/feraiseexcept
helpviewer_keywords:
- feraiseexcept function
ms.assetid: 87e89151-83c2-4563-9a9a-45666245d437
ms.openlocfilehash: 581dd4026a20ce7221945c5815af3ae102f132fa
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50532252"
---
# <a name="feraiseexcept"></a>feraiseexcept

Wywołuje określone wyjątki zmiennoprzecinkowe.

## <a name="syntax"></a>Składnia

```C
int feraiseexcept(
   int excepts
);
```

### <a name="parameters"></a>Parametry

*z wyjątkiem*<br/>
Wyjątki zmiennoprzecinkowe, aby wywołać.

## <a name="return-value"></a>Wartość zwracana

Jeśli wszystkie określone wyjątki są zgłaszane pomyślnie, zwraca wartość 0.

## <a name="remarks"></a>Uwagi

**Feraiseexcept** funkcja polegające na zgłaszać wyjątki zmiennoprzecinkowe, określony przez *z wyjątkiem*.   **Feraiseexcept** funkcja obsługuje te makra wyjątków, zdefiniowane w pliku \<fenv.h >:

|Makra wyjątków|Opis|
|---------------------|-----------------|
|FE_DIVBYZERO|Wystąpił błąd singularity lub pole w starszej operacji zmiennoprzecinkowej; Utworzono wartości nieskończonej.|
|FE_INEXACT|Wymuszono funkcji round przechowywanych wynikiem wcześniejszych operacji zmiennoprzecinkowej.|
|FE_INVALID|Wystąpił błąd domeny w starszej operacji zmiennoprzecinkowej.|
|FE_OVERFLOW|Wystąpił błąd zakresu; wynik operacji zmiennoprzecinkowej wcześniej była zbyt duża, aby mogły być reprezentowane.|
|FE_UNDERFLOW|Wcześniej wyniku operacji zmiennoprzecinkowej był za mały, aby mogły być reprezentowane w o pełnej dokładności; wartość została utworzona.|
|FE_ALLEXCEPT|Bitowe OR wszystkich obsługiwane wyjątki zmiennoprzecinkowe.|

*z wyjątkiem* argument może wynosić zero, jeden wartości makra wyjątków lub operatora testu koniunkcji lub dwóch lub więcej z makr wyjątków obsługiwanych. Spełnieniu jednego z makr wyjątków określonego FE_OVERFLOW lub FE_UNDERFLOW, może być zgłaszany wyjątek FE_INEXACT, jako efekt uboczny.

Aby użyć tej funkcji, należy wyłączyć funkcję optymalizacji zmiennopozycyjnych, które mogą uniemożliwić dostęp przy użyciu `#pragma fenv_access(on)` dyrektywy przed wywołaniem. Aby uzyskać więcej informacji, zobacz [fenv_access](../../preprocessor/fenv-access.md).

**Microsoft Specific:** wyjątki określone w *z wyjątkiem* są wywoływane w kolejności FE_INVALID, FE_DIVBYZERO FE_OVERFLOW, FE_UNDERFLOW, FE_INEXACT. Jednak FE_INEXACT mogą być wywoływane, gdy FE_OVERFLOW lub FE_UNDERFLOW jest wywoływane, nawet jeśli nie zostanie określony w *z wyjątkiem*. **End specyficzny dla Microsoft**

## <a name="requirements"></a>Wymagania

|Funkcja|Nagłówek języka C|Nagłówek języka C++|
|--------------|--------------|------------------|
|*feraiseexcept*|\<fenv.h>|\<cfenv>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[fesetexceptflag](fesetexceptflag2.md)<br/>
[feholdexcept](feholdexcept2.md)<br/>
[fetestexcept](fetestexcept1.md)<br/>
[feupdateenv](feupdateenv.md)<br/>
