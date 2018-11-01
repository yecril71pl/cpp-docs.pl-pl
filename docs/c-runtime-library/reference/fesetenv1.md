---
title: fesetenv
ms.date: 04/05/2018
apiname:
- fesetenv
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
- fesetenv
- fenv/fesetenv
helpviewer_keywords:
- fesetenv function
ms.assetid: ffc64fff-8ea7-4d59-9e04-ff96ef8cd012
ms.openlocfilehash: 8c91bfbb89df964fed0a632d5fb5ebac47ebe948
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50436165"
---
# <a name="fesetenv"></a>fesetenv

Ustawia bieżące środowisko zmiennoprzecinkowych.

## <a name="syntax"></a>Składnia

```C
int fesetenv(
   const fenv_t *penv
);
```

### <a name="parameters"></a>Parametry

*penv*<br/>
Wskaźnik do **fenv_t** obiekt, który zawiera zmiennoprzecinkowych środowiska według stawki ustalonej przez wywołanie [fegetenv](fegetenv1.md) lub [feholdexcept](feholdexcept2.md). Można również określić domyślne środowisko zmiennoprzecinkowych uruchamiania przy użyciu **FE_DFL_ENV** makra.

## <a name="return-value"></a>Wartość zwracana

Zwraca wartość 0, jeśli pomyślnie ustawiono środowiska. W przeciwnym razie zwraca wartość różną od zera.

## <a name="remarks"></a>Uwagi

**Fesetenv** funkcja ustawia bieżące środowisko zmiennoprzecinkową z wartością przechowywaną w **fenv_t** obiekt wskazywany przez *penv*. Wartość zmiennoprzecinkowa środowiska punktu ustawiono flagi stanu i tryby kontrolki, które wpływają na obliczeń zmiennopozycyjnych. Obejmuje to trybu zaokrąglania i flagi stanu przypadku wyjątków zmiennoprzecinkowych.  Jeśli *penv* nie **FE_DFL_ENV** lub nie wskazuje prawidłowego **fenv_t** obiekt, kolejne zachowanie jest niezdefiniowane.

Wywołanie tej funkcji ustawia wyjątek flagi stanu, które znajdują się w *penv* obiektu, ale nie powoduje tych wyjątków.

Aby użyć tej funkcji, należy wyłączyć funkcję optymalizacji zmiennopozycyjnych, które mogą uniemożliwić dostęp przy użyciu `#pragma fenv_access(on)` dyrektywy przed wywołaniem. Aby uzyskać więcej informacji, zobacz [fenv_access](../../preprocessor/fenv-access.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Nagłówek języka C|Nagłówek języka C++|
|--------------|--------------|------------------|
|**fesetenv**|\<fenv.h>|\<cfenv>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[fegetenv](fegetenv1.md)<br/>
[feclearexcept](feclearexcept1.md)<br/>
[feholdexcept](feholdexcept2.md)<br/>
[fesetexceptflag](fesetexceptflag2.md)<br/>
