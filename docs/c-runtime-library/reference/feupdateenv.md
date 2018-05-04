---
title: feupdateenv | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
apiname:
- feupdateenv
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
- feupdateenv
- fenv/feupdateenv
dev_langs:
- C++
helpviewer_keywords:
- feupdateenv function
ms.assetid: 3d170042-dfd5-4e4f-a55f-038cf2296cc9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1d88284717aec7a19c936d7ed8d87da96006d7ed
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="feupdateenv"></a>feupdateenv

Zapisuje obecnie zgłoszono wyjątki zmiennoprzecinkowe, przywraca stan określonego środowiska liczb zmiennoprzecinkowych, a następnie wywołuje zapisane wyjątki zmiennoprzecinkowe.

## <a name="syntax"></a>Składnia

```C
int feupdateenv(
   const fenv_t* penv
);
```

### <a name="parameters"></a>Parametry

*penv*<br/>
Wskaźnik do **fenv_t** obiekt, który zawiera zmiennoprzecinkowe środowiska zgodnie z ustaleniami przez wywołanie do [fegetenv](fegetenv1.md) lub [feholdexcept](feholdexcept2.md). Można również określić domyślnego środowiska zmiennoprzecinkowe uruchamiania za pomocą makra FE_DFL_ENV.

## <a name="return-value"></a>Wartość zwracana

Zwraca wartość 0, jeśli wszystkie działania ukończone pomyślnie. W przeciwnym razie zwraca wartość różną od zera.

## <a name="remarks"></a>Uwagi

**Feupdateenv** funkcja wykonuje wiele operacji. Po pierwsze przechowuje bieżące flagi stanu zgłoszono wyjątek zmiennoprzecinkowy, którego w magazynie automatycznego. Następnie, ustawia bieżącego środowiska zmiennoprzecinkowe z wartości przechowywanej w **fenv_t** obiekt wskazywany przez *penv*. Jeśli *penv* nie jest **FE_DFL_ENV** lub nie wskazuje na prawidłową **fenv_t** obiekt, kolejne zachowanie jest niezdefiniowany. Na koniec **feupdateenv** zgłasza wyjątki zmiennoprzecinkowe przechowywane lokalnie.

Aby użyć tej funkcji, należy wyłączyć funkcję zmiennoprzecinkowe funkcje optymalizacji, które może uniemożliwić dostęp przy użyciu `#pragma fenv_access(on)` dyrektywy przed wywołaniem. Aby uzyskać więcej informacji, zobacz [fenv_access](../../preprocessor/fenv-access.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Nagłówek C|Nagłówek C++|
|--------------|--------------|------------------|
|**feupdateenv**|\<fenv.h>|\<cfenv>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[fegetenv](fegetenv1.md)<br/>
[feclearexcept](feclearexcept1.md)<br/>
[feholdexcept](feholdexcept2.md)<br/>
[fesetexceptflag](fesetexceptflag2.md)<br/>
