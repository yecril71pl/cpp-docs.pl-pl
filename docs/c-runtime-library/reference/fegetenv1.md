---
title: fegetenv
ms.date: 04/05/2018
apiname:
- fetegenv
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
- fegetenv
- fenv/fegetenv
helpviewer_keywords:
- fetegenv function
ms.assetid: 68962421-6978-4b27-8e4c-ad1577830cf6
ms.openlocfilehash: d3985e4dd2b3944bcdddb79605887def7ba15473
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50668094"
---
# <a name="fegetenv"></a>fegetenv

Zapisuje bieżące środowisko zmiennoprzecinkowych w określony obiekt.

## <a name="syntax"></a>Składnia

```C
int fegetenv(
   fenv_t *penv
);
```

### <a name="parameters"></a>Parametry

*penv*<br/>
Wskaźnik do **fenv_t** będzie zawierał bieżącej wartości zmiennoprzecinkowych środowiska.

## <a name="return-value"></a>Wartość zwracana

Zwraca wartość 0, jeśli zmiennoprzecinkowych środowisko zostało pomyślnie zapisane w *penv*. W przeciwnym razie zwraca wartość różna od zera.

## <a name="remarks"></a>Uwagi

**Fegetenv** funkcja przechowuje bieżące środowisko zmiennoprzecinkowych w obiekt wskazywany przez *penv*. Wartość zmiennoprzecinkowa środowiska punktu ustawiono flagi stanu i tryby kontrolki, które wpływają na obliczeń zmiennopozycyjnych. Obejmuje to trybu zaokrąglania kierunku i flagi stanu przypadku wyjątków zmiennoprzecinkowych.  Jeśli *penv* nie wskazuje prawidłowego **fenv_t** obiekt, kolejne zachowanie jest niezdefiniowane.

Aby użyć tej funkcji, należy wyłączyć funkcję optymalizacji zmiennopozycyjnych, które mogą uniemożliwić dostęp przy użyciu `#pragma fenv_access(on)` dyrektywy przed wywołaniem. Aby uzyskać więcej informacji, zobacz [fenv_access](../../preprocessor/fenv-access.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Nagłówek języka C|Nagłówek języka C++|
|--------------|--------------|------------------|
|**fegetenv**|\<fenv.h>|\<cfenv>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[fesetenv](fesetenv1.md)<br/>
