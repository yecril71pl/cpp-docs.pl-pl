---
title: feholdexcept | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/05/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- feholdexcept function
ms.assetid: 88e512ae-b5d8-452c-afe9-c824cd3ef1d8
caps.latest.revision: 5
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9080358c5d929307dbc68ce0e9669fae7a046022
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="feholdexcept"></a>feholdexcept

Zapisuje bieżące środowisko liczb zmiennoprzecinkowych w określonym obiekcie czyści flagi stanu zmiennoprzecinkowych i, jeśli to możliwe, umieszcza liczb zmiennoprzecinkowych środowiska do zatrzymania z systemem innym niż tryb.

## <a name="syntax"></a>Składnia

```C
int feholdexcept(
   fenv_t *penv
);
```

### <a name="parameters"></a>Parametry

*penv*<br/>
Wskaźnik do **fenv_t** obiekt zawierający kopię zmiennoprzecinkowe środowiska.

## <a name="return-value"></a>Wartość zwracana

Zwraca zero tylko wtedy, gdy funkcja jest w stanie pomyślnie włączyć-stop zmiennoprzecinkowych wyjątków.

## <a name="remarks"></a>Uwagi

**Feholdexcept** funkcja służy do przechowywania stanu bieżącego środowiska ruchomy punkt w **fenv_t** obiekt wskazywany przez *penv*i ustawić środowiska Nie można przerwać wykonywania na wyjątki zmiennoprzecinkowe. Jest to nazywane tryb bez zatrzymania.  Ten tryb jest kontynuowany do momentu przywrócenia środowiska przy użyciu [fesetenv](fesetenv1.md) lub [feupdateenv](feupdateenv.md).

Funkcja ta jest przydatna na początku procedury wymagające Ukryj co najmniej jeden wyjątki zmiennoprzecinkowe wywołujący. Aby zgłosić wyjątek, może po prostu wyczyścić niechciane wyjątków przy użyciu [feclearexcept,](feclearexcept1.md) , a następnie zakończyć tryb-stop wywołaniem **feupdateenv**.

Aby użyć tej funkcji, należy wyłączyć funkcję zmiennoprzecinkowe funkcje optymalizacji, które może uniemożliwić dostęp przy użyciu `#pragma fenv_access(on)` dyrektywy przed wywołaniem. Aby uzyskać więcej informacji, zobacz [fenv_access](../../preprocessor/fenv-access.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Nagłówek C|Nagłówek C++|
|--------------|--------------|------------------|
|**feholdexcept**|\<fenv.h>|\<cfenv>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[feclearexcept](feclearexcept1.md)<br/>
[fesetenv](fesetenv1.md)<br/>
[feupdateenv](feupdateenv.md)<br/>
