---
title: fesetexceptflag
ms.date: 04/05/2018
apiname:
- fesetexceptflag
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
- fesetexceptflag
- fenv/fesetexceptflag
helpviewer_keywords:
- fesetexceptflag function
ms.assetid: 2f7dad77-9e54-4097-a3e3-35176ace4de5
ms.openlocfilehash: 9ac79e790f0b1e7a89413a0d4974f6053c95616e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62333998"
---
# <a name="fesetexceptflag"></a>fesetexceptflag

Ustawia flagi stanu zmiennoprzecinkowego określonego w bieżącym środowisku zmiennoprzecinkowych.

## <a name="syntax"></a>Składnia

```C
int fesetexceptflag(
     const fexcept_t *pstatus,
     int excepts
);
```

### <a name="parameters"></a>Parametry

*pstatus*<br/>
Wskaźnik do **fexcept_t** obiekt zawierający wartości, aby ustawić wyjątek flagi stanu. Obiekt może być ustawiona przez poprzednie wywołanie [fegetexceptflag](fegetexceptflag2.md).

*z wyjątkiem*<br/>
Flagi stanu wyjątek zmiennoprzecinkowy, którego można ustawić.

## <a name="return-value"></a>Wartość zwracana

Jeśli wszystkie flagi stanu określonego wyjątku są ustawione, zwraca wartość 0. W przeciwnym razie zwraca wartość różną od zera.

## <a name="remarks"></a>Uwagi

**Fesetexceptflag** funkcja ustawia stan flagi stanu wyjątków zmiennoprzecinkowych, które są określone przez *z wyjątkiem* odpowiednie wartości w **fexcept_t** Obiekt wskazywany przez *pstatus*.  On zgłaszaj wyjątków. *Pstatus* wskaźnik musi wskazywać prawidłowy **fexcept_t** obiektu lub kolejnych zachowanie jest niezdefiniowane. **Fesetexceptflag** funkcja obsługuje te wartości makra wyjątków w *z wyjątkiem*zdefiniowaną w \<fenv.h >:

|Makra wyjątków|Opis|
|---------------------|-----------------|
|FE_DIVBYZERO|Wystąpił błąd singularity lub pole w starszej operacji zmiennoprzecinkowej; Utworzono wartości nieskończonej.|
|FE_INEXACT|Wymuszono funkcji round przechowywanych wynikiem wcześniejszych operacji zmiennoprzecinkowej.|
|FE_INVALID|Wystąpił błąd domeny w starszej operacji zmiennoprzecinkowej.|
|FE_OVERFLOW|Wystąpił błąd zakresu; wynik operacji zmiennoprzecinkowej wcześniej była zbyt duża, aby mogły być reprezentowane.|
|FE_UNDERFLOW|Wcześniej wyniku operacji zmiennoprzecinkowej był za mały, aby mogły być reprezentowane w o pełnej dokładności; wartość została utworzona.|
|FE_ALLEXCEPT|Bitowe OR wszystkich obsługiwane wyjątki zmiennoprzecinkowe.|

*z wyjątkiem* argument może być zera, makra wyjątków dotyczących liczb zmiennoprzecinkowych obsługiwanych lub operatora testu koniunkcji lub dwóch lub więcej makra. Wpływ dowolna inna wartość argumentu jest niezdefiniowane.

Aby użyć tej funkcji, należy wyłączyć funkcję optymalizacji zmiennopozycyjnych, które mogą uniemożliwić dostęp przy użyciu `#pragma fenv_access(on)` dyrektywy przed wywołaniem. Aby uzyskać więcej informacji, zobacz [fenv_access](../../preprocessor/fenv-access.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Nagłówek języka C|Nagłówek języka C++|
|--------------|--------------|------------------|
|**fesetexceptflag**|\<fenv.h>|\<cfenv>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[fegetexceptflag](fegetexceptflag2.md)<br/>
