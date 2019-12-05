---
title: feraiseexcept
ms.date: 04/05/2018
api_name:
- feraiseexcept
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
api_type:
- HeaderDef
f1_keywords:
- feraiseexcept
- fenv/feraiseexcept
helpviewer_keywords:
- feraiseexcept function
ms.assetid: 87e89151-83c2-4563-9a9a-45666245d437
ms.openlocfilehash: 07c8a79e0a9569db80607e1ec1e16cd4b502783c
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857830"
---
# <a name="feraiseexcept"></a>feraiseexcept

Podnosi określone wyjątki zmiennoprzecinkowe.

## <a name="syntax"></a>Składnia

```C
int feraiseexcept(
   int excepts
);
```

### <a name="parameters"></a>Parametry

*Oprócz*<br/>
Wyjątki zmiennoprzecinkowe do podniesienia.

## <a name="return-value"></a>Wartość zwrócona

Jeśli wszystkie określone wyjątki są zgłaszane pomyślnie, zwraca wartość 0.

## <a name="remarks"></a>Uwagi

Funkcja **feraiseexcept** próbuje podnieść wyjątki zmiennoprzecinkowe określone przez *except*.   Funkcja **feraiseexcept** obsługuje te makra wyjątków zdefiniowane w \<fenv. h >:

|Makro wyjątku|Opis|
|---------------------|-----------------|
|FE_DIVBYZERO|Wystąpił błąd Singularity lub wartość w poprzedniej operacji zmiennoprzecinkowej; utworzono nieskończoną wartość.|
|FE_INEXACT|Funkcja była zmuszona do zaokrąglania przechowywanego wyniku poprzedniej operacji zmiennoprzecinkowej.|
|FE_INVALID|Wystąpił błąd domeny w poprzedniej operacji zmiennoprzecinkowej.|
|FE_OVERFLOW|Wystąpił błąd zakresu; wcześniejszy wynik operacji zmiennoprzecinkowej był zbyt duży, aby można było go przedstawić.|
|FE_UNDERFLOW|Wcześniejszy wynik operacji zmiennoprzecinkowej był zbyt mały, aby mógł być reprezentowany z pełną dokładnością; utworzono nienormalną wartość.|
|FE_ALLEXCEPT|Bitowe lub wszystkie obsługiwane wyjątki zmiennoprzecinkowe.|

Argument *except* może mieć wartość zero, jedną z wartości makra wyjątku lub bitową lub dwa lub więcej obsługiwanych makr wyjątków. Jeśli jedno z określonych makr wyjątków jest FE_OVERFLOW lub FE_UNDERFLOW, wyjątek FE_INEXACT może być podniesiony jako efekt uboczny.

Aby użyć tej funkcji, należy wyłączyć optymalizacje zmiennoprzecinkowe, które mogą uniemożliwić dostęp przy użyciu dyrektywy `#pragma fenv_access(on)` przed wywołaniem. Aby uzyskać więcej informacji, zobacz [fenv_access](../../preprocessor/fenv-access.md).

**Specyficzne dla firmy Microsoft:** Wyjątki określone w wyjątkach są *wywoływane w kolejności* FE_INVALID, FE_DIVBYZERO, FE_OVERFLOW, FE_UNDERFLOW, FE_INEXACT. Jednakże FE_INEXACT mogą być wywoływane, gdy zostanie zgłoszony FE_OVERFLOW lub FE_UNDERFLOW, nawet jeśli nie zostanie określony w *z wyjątkiem*.

## <a name="requirements"></a>Wymagania

|Funkcja|Nagłówek języka C|C++nagłówki|
|--------------|--------------|------------------|
|*feraiseexcept*|\<fenv.h>|\<cfenv>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[fesetexceptflag](fesetexceptflag2.md)<br/>
[feholdexcept](feholdexcept2.md)<br/>
[fetestexcept](fetestexcept1.md)<br/>
[feupdateenv](feupdateenv.md)<br/>
