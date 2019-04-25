---
title: feholdexcept
ms.date: 04/05/2018
apiname:
- feholdexcept
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
- feholdexcept
- fenv/feholdexcept
helpviewer_keywords:
- feholdexcept function
ms.assetid: 88e512ae-b5d8-452c-afe9-c824cd3ef1d8
ms.openlocfilehash: 26097398b9f9d498ab4c56690dc9c6cbb950bafb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62334388"
---
# <a name="feholdexcept"></a>feholdexcept

Zapisuje bieżące środowisko zmiennoprzecinkowych określonym obiektem, czyści flagi stanu zmiennoprzecinkowego i, jeśli to możliwe, umieszcza zmiennoprzecinkowych środowiska w trybie gładkie zatrzymanie.

## <a name="syntax"></a>Składnia

```C
int feholdexcept(
   fenv_t *penv
);
```

### <a name="parameters"></a>Parametry

*penv*<br/>
Wskaźnik do **fenv_t** obiekt ma zawierać kopię zmiennoprzecinkowych środowiska.

## <a name="return-value"></a>Wartość zwracana

Zwraca zero, tylko wtedy, gdy funkcja jest w stanie pomyślnie Włącz obsługę wyjątków zmiennoprzecinkowych gładkie zatrzymanie.

## <a name="remarks"></a>Uwagi

**Feholdexcept** funkcja jest używana do przechowywania stanu bieżącego środowiska ruchomy punkt w **fenv_t** obiekt wskazywany przez *penv*i aby ustawić środowiska Nie można przerwać wykonywanie na wyjątki zmiennoprzecinkowe. Jest to nazywane tryb bez zatrzymania.  Ten tryb jest kontynuowany do momentu przywrócenia środowiska za pomocą [fesetenv](fesetenv1.md) lub [feupdateenv](feupdateenv.md).

Funkcja ta jest przydatna na początku procedury, który wymaga, aby ukryć jeden lub kilka wyjątków zmiennoprzecinkowych wywołujący. Aby zgłosić wyjątek, można po prostu wyczyść niechciane wyjątków za pomocą [feclearexcept,](feclearexcept1.md) a następnie zakończyć trybu-stop wywołaniem **feupdateenv**.

Aby użyć tej funkcji, należy wyłączyć funkcję optymalizacji zmiennopozycyjnych, które mogą uniemożliwić dostęp przy użyciu `#pragma fenv_access(on)` dyrektywy przed wywołaniem. Aby uzyskać więcej informacji, zobacz [fenv_access](../../preprocessor/fenv-access.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Nagłówek języka C|Nagłówek języka C++|
|--------------|--------------|------------------|
|**feholdexcept**|\<fenv.h>|\<cfenv>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[feclearexcept](feclearexcept1.md)<br/>
[fesetenv](fesetenv1.md)<br/>
[feupdateenv](feupdateenv.md)<br/>
