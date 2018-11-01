---
title: feupdateenv
ms.date: 04/05/2018
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
helpviewer_keywords:
- feupdateenv function
ms.assetid: 3d170042-dfd5-4e4f-a55f-038cf2296cc9
ms.openlocfilehash: 6d553d6899f55f5bdfb3ff313e88abfcb56ab4ec
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50605120"
---
# <a name="feupdateenv"></a>feupdateenv

Zapisuje obecnie zostaje zgłoszone wyjątki zmiennoprzecinkowe, przywraca stan określonego środowiska zmiennoprzecinkowych, a następnie zgłasza wyjątki zmiennoprzecinkowe zapisane.

## <a name="syntax"></a>Składnia

```C
int feupdateenv(
   const fenv_t* penv
);
```

### <a name="parameters"></a>Parametry

*penv*<br/>
Wskaźnik do **fenv_t** obiekt, który zawiera zmiennoprzecinkowych środowiska według stawki ustalonej przez wywołanie [fegetenv](fegetenv1.md) lub [feholdexcept](feholdexcept2.md). Można również określić domyślne środowisko zmiennoprzecinkowych uruchamiania, za pomocą makra FE_DFL_ENV.

## <a name="return-value"></a>Wartość zwracana

Zwraca wartość 0, jeśli wszystkie akcje wykonane pomyślnie. W przeciwnym razie zwraca wartość różną od zera.

## <a name="remarks"></a>Uwagi

**Feupdateenv** funkcja wykonuje wiele operacji. Po pierwsze przechowuje bieżące flagi stanu podjętym wyjątkiem zmiennoprzecinkowym w automatycznego przechowywania. Następnie ustawia bieżące środowisko zmiennoprzecinkową z wartością przechowywaną w **fenv_t** obiekt wskazywany przez *penv*. Jeśli *penv* nie **FE_DFL_ENV** lub nie wskazuje prawidłowego **fenv_t** obiekt, kolejne zachowanie jest niezdefiniowane. Na koniec **feupdateenv** zgłasza wyjątki zmiennoprzecinkowe przechowywane lokalnie.

Aby użyć tej funkcji, należy wyłączyć funkcję optymalizacji zmiennopozycyjnych, które mogą uniemożliwić dostęp przy użyciu `#pragma fenv_access(on)` dyrektywy przed wywołaniem. Aby uzyskać więcej informacji, zobacz [fenv_access](../../preprocessor/fenv-access.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Nagłówek języka C|Nagłówek języka C++|
|--------------|--------------|------------------|
|**feupdateenv**|\<fenv.h>|\<cfenv>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[fegetenv](fegetenv1.md)<br/>
[feclearexcept](feclearexcept1.md)<br/>
[feholdexcept](feholdexcept2.md)<br/>
[fesetexceptflag](fesetexceptflag2.md)<br/>
