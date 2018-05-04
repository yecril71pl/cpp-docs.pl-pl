---
title: fesetexceptflag | Dokumenty Microsoft
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- fesetexceptflag function
ms.assetid: 2f7dad77-9e54-4097-a3e3-35176ace4de5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eef8ba1c91e6db4f0d620ef820a6487b3b17e649
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="fesetexceptflag"></a>fesetexceptflag

Ustawia flagi określony stan liczb zmiennoprzecinkowych w bieżącym środowisku zmiennoprzecinkowych.

## <a name="syntax"></a>Składnia

```C
int fesetexceptflag(
     const fexcept_t *pstatus,
     int excepts
);
```

### <a name="parameters"></a>Parametry

*pstatus*<br/>
Wskaźnik do **fexcept_t** obiekt zawierający wartości, które mają ustawioną wartość wyjątek flagi stanu. Obiekt może zostać ustawiona przez poprzednie wywołanie [fegetexceptflag](fegetexceptflag2.md).

*z wyjątkiem*<br/>
Flagi stanu wyjątek zmiennoprzecinkowy, którego można ustawić.

## <a name="return-value"></a>Wartość zwracana

Zwraca wartość 0, jeśli pomyślnie ustawiono wszystkie flagi stanu określonego wyjątku. W przeciwnym razie zwraca wartość różną od zera.

## <a name="remarks"></a>Uwagi

**Fesetexceptflag** funkcja ustawia stan flagi stanu zmiennoprzecinkowych wyjątków, określony przez *z wyjątkiem* do odpowiedniej wartości **fexcept_t** Obiekt wskazywany przez *pstatus*.  Zgłaszaj wyjątków. *Pstatus* wskaźnika musi wskazywać prawidłowe **fexcept_t** obiektu lub kolejnych zachowanie jest niezdefiniowana. **Fesetexceptflag** funkcja obsługuje te wartości makra wyjątków w *z wyjątkiem*zdefiniowanej w \<fenv.h >:

|Makra wyjątków|Opis|
|---------------------|-----------------|
|FE_DIVBYZERO|Wystąpił błąd singularity lub pole w wcześniej operacji zmiennoprzecinkowej; Utworzono wartości nieskończonej.|
|FE_INEXACT|Funkcja wymuszono zaokrąglona wyniku przechowywanego wcześniej operacji zmiennoprzecinkowej.|
|FE_INVALID|Wystąpił błąd domeny w wcześniej operacji zmiennoprzecinkowej.|
|FE_OVERFLOW|Wystąpił błąd zakresu; wcześniej wynik operacji zmiennoprzecinkowej jest zbyt duży, może być reprezentowana.|
|FE_UNDERFLOW|Wynik operacji zmiennoprzecinkowej wcześniej był za mały na pełne precyzji; wartość została utworzona.|
|FE_ALLEXCEPT|Bitowe lub wszystkie obsługiwane wyjątki zmiennoprzecinkowe.|

*z wyjątkiem* argument może być równy zero, jednym z makr wyjątków dotyczących liczb zmiennoprzecinkowych obsługiwanych lub operatora testu koniunkcji lub dwóch lub więcej makr. Efekt dowolna inna wartość argumentu jest niezdefiniowany.

Aby użyć tej funkcji, należy wyłączyć funkcję zmiennoprzecinkowe funkcje optymalizacji, które może uniemożliwić dostęp przy użyciu `#pragma fenv_access(on)` dyrektywy przed wywołaniem. Aby uzyskać więcej informacji, zobacz [fenv_access](../../preprocessor/fenv-access.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Nagłówek C|Nagłówek C++|
|--------------|--------------|------------------|
|**fesetexceptflag**|\<fenv.h>|\<cfenv>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[fegetexceptflag](fegetexceptflag2.md)<br/>
