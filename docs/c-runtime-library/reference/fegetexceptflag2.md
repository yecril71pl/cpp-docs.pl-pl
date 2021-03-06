---
title: fegetexceptflag
ms.date: 04/05/2018
api_name:
- fegetexceptflag
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
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- fegetexceptflag
- fenv/fegetexceptflag
helpviewer_keywords:
- fegetexceptflag function
ms.assetid: 2d28f0ca-70c9-4cff-be8b-3d876eacde71
ms.openlocfilehash: b840408ce704ad5519fbf233de41c8d5422006ad
ms.sourcegitcommit: ba4180a2d79d7e391f2f705797505d4aedbc2a5e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2020
ms.locfileid: "76972189"
---
# <a name="fegetexceptflag"></a>fegetexceptflag

Przechowuje bieżący stan określonych flag wyjątków zmiennoprzecinkowych.

## <a name="syntax"></a>Składnia

```C
int fegetexceptflag(
   fexcept_t* pstatus,
   int excepts
);
```

### <a name="parameters"></a>Parametry

*pstatus*<br/>
Wskaźnik do obiektu **fexcept_t** , aby zawierał bieżące wartości flag wyjątków określonych przez *except*.

*Oprócz*<br/>
Flagi wyjątków zmiennoprzecinkowych do przechowywania w *pstatus*.

## <a name="return-value"></a>Wartość zwrócona

Po pomyślnym zwraca wartość 0. W przeciwnym razie zwraca wartość różną od zera.

## <a name="remarks"></a>Uwagi

Funkcja **fegetexceptflag** przechowuje bieżący stan wyjątków zmiennoprzecinkowych określony przez, *z wyjątkiem* obiektu **fexcept_t** wskazywanego przez *pstatus*.  *pstatus* musi wskazywać prawidłowy obiekt **fexcept_t** lub kolejne zachowanie jest niezdefiniowane. Funkcja **fegetexceptflag** obsługuje te makra wyjątków zdefiniowane w \<fenv. h >:

|Makro wyjątku|Opis|
|---------------------|-----------------|
|FE_DIVBYZERO|Wystąpił błąd Singularity lub wartość w poprzedniej operacji zmiennoprzecinkowej; utworzono nieskończoną wartość.|
|FE_INEXACT|Funkcja była zmuszona do zaokrąglania przechowywanego wyniku poprzedniej operacji zmiennoprzecinkowej.|
|FE_INVALID|Wystąpił błąd domeny w poprzedniej operacji zmiennoprzecinkowej.|
|FE_OVERFLOW|Wystąpił błąd zakresu; wcześniejszy wynik operacji zmiennoprzecinkowej był zbyt duży, aby można było go przedstawić.|
|FE_UNDERFLOW|Wcześniejszy wynik operacji zmiennoprzecinkowej był zbyt mały, aby mógł być reprezentowany z pełną dokładnością; utworzono nienormalną wartość.|
|FE_ALL_EXCEPT|Bitowe lub wszystkie obsługiwane wyjątki zmiennoprzecinkowe.|

Argument *except* może mieć wartość zero, jedno z obsługiwanych makr wyjątków zmiennoprzecinkowych lub bitowe lub dwa lub więcej makr. Wynik innej wartości argumentu jest niezdefiniowany.

Aby użyć tej funkcji, należy wyłączyć optymalizacje zmiennoprzecinkowe, które mogą uniemożliwić dostęp przy użyciu dyrektywy `#pragma fenv_access(on)` przed wywołaniem. Aby uzyskać więcej informacji, zobacz [fenv_access](../../preprocessor/fenv-access.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Nagłówek języka C|C++nagłówki|
|--------------|--------------|------------------|
|**fegetexceptflag**|\<fenv.h>|\<cfenv>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[fesetexceptflag](fesetexceptflag2.md)<br/>
