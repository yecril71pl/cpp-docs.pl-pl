---
title: feraiseexcept | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- feraiseexcept function
ms.assetid: 87e89151-83c2-4563-9a9a-45666245d437
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dfd60612c92f8e3ff542fd22bbf5b4a01f7b7365
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32398640"
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

Jeśli wszystkie określone wyjątki pojawienia się pomyślnie, zwraca wartość 0.

## <a name="remarks"></a>Uwagi

**Feraiseexcept** funkcja próbuje zgłaszać wyjątki zmiennoprzecinkowe określony przez *z wyjątkiem*.   **Feraiseexcept** funkcja obsługuje makrach wyjątków zdefiniowane w \<fenv.h >:

|Makra wyjątków|Opis|
|---------------------|-----------------|
|FE_DIVBYZERO|Wystąpił błąd singularity lub pole w wcześniej operacji zmiennoprzecinkowej; Utworzono wartości nieskończonej.|
|FE_INEXACT|Funkcja wymuszono zaokrąglona wyniku przechowywanego wcześniej operacji zmiennoprzecinkowej.|
|FE_INVALID|Wystąpił błąd domeny w wcześniej operacji zmiennoprzecinkowej.|
|FE_OVERFLOW|Wystąpił błąd zakresu; wcześniej wynik operacji zmiennoprzecinkowej jest zbyt duży, może być reprezentowana.|
|FE_UNDERFLOW|Wynik operacji zmiennoprzecinkowej wcześniej był za mały na pełne precyzji; wartość została utworzona.|
|FE_ALLEXCEPT|Bitowe lub wszystkie obsługiwane wyjątki zmiennoprzecinkowe.|

*z wyjątkiem* argument może być równy zero, jednej z wartości makra wyjątków lub operatora testu koniunkcji lub dwóch lub więcej z makr wyjątków obsługiwanych. Po spełnieniu jednego z makr wyjątków określony FE_OVERFLOW lub FE_UNDERFLOW, może zostać zgłoszony wyjątek FE_INEXACT, jako efektem ubocznym.

Aby użyć tej funkcji, należy wyłączyć funkcję zmiennoprzecinkowe funkcje optymalizacji, które może uniemożliwić dostęp przy użyciu `#pragma fenv_access(on)` dyrektywy przed wywołaniem. Aby uzyskać więcej informacji, zobacz [fenv_access](../../preprocessor/fenv-access.md).

**Microsoft Specific:** wyjątki określone w *z wyjątkiem* są wywoływane w kolejności FE_INVALID, FE_DIVBYZERO, FE_OVERFLOW, FE_UNDERFLOW, FE_INEXACT. Jednak FE_INEXACT mogą być wywoływane, gdy FE_OVERFLOW lub FE_UNDERFLOW jest wywoływane, nawet jeśli nie zostanie określony w *z wyjątkiem*. **Końcowy określonych firmy Microsoft**

## <a name="requirements"></a>Wymagania

|Funkcja|Nagłówek C|Nagłówek C++|
|--------------|--------------|------------------|
|*feraiseexcept*|\<fenv.h>|\<cfenv>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[fesetexceptflag](fesetexceptflag2.md)<br/>
[feholdexcept](feholdexcept2.md)<br/>
[fetestexcept](fetestexcept1.md)<br/>
[feupdateenv](feupdateenv.md)<br/>
