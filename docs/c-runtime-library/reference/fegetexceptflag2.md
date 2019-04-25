---
title: fegetexceptflag
ms.date: 04/05/2018
apiname:
- fegetexceptflag
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
- fegetexceptflag
- fenv/fegetexceptflag
helpviewer_keywords:
- fegetexceptflag function
ms.assetid: 2d28f0ca-70c9-4cff-be8b-3d876eacde71
ms.openlocfilehash: 43259001bd05bb7df9e2e1636c174018dcdaef3c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62334427"
---
# <a name="fegetexceptflag"></a>fegetexceptflag

Zapisuje bieżący stan flagi określonego wyjątku zmiennoprzecinkowego.

## <a name="syntax"></a>Składnia

```C
int fegetexceptflag(
   fexcept_t* pstatus,
   int excepts
);
```

### <a name="parameters"></a>Parametry

*pstatus*<br/>
Wskaźnik do **fexcept_t** zawierają bieżących wartości flag wyjątków określonych przez obiekt *z wyjątkiem*.

*z wyjątkiem*<br/>
Flagi wyjątków zmiennoprzecinkowych, aby przechowywać w *pstatus*.

## <a name="return-value"></a>Wartość zwracana

W przypadku powodzenia zwraca wartość 0. W przeciwnym razie zwraca wartość różna od zera.

## <a name="remarks"></a>Uwagi

**Fegetexceptflag** funkcja przechowuje bieżący stan flagi stanu wyjątków zmiennoprzecinkowych, które są określone przez *z wyjątkiem* w **fexcept_t** obiekt wskazywany przez *pstatus*.  *pstatus* musi wskazywać prawidłowy **fexcept_t** obiektu lub kolejnych zachowanie jest niezdefiniowane. **Fegetexceptflag** funkcja obsługuje te makra wyjątków, zdefiniowane w pliku \<fenv.h >:

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
|**fegetexceptflag**|\<fenv.h>|\<cfenv>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[fesetexceptflag](fesetexceptflag2.md)<br/>
