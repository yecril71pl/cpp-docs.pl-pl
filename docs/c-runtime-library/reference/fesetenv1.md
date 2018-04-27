---
title: fesetenv | Dokumentacja firmy Microsoft
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
dev_langs:
- C++
helpviewer_keywords:
- fesetenv function
ms.assetid: ffc64fff-8ea7-4d59-9e04-ff96ef8cd012
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 466d37a55cbd0d4fdf3e1fc0eed085cb9fcb5b6a
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="fesetenv"></a>fesetenv

Ustawia bieżącego środowiska zmiennoprzecinkowych.

## <a name="syntax"></a>Składnia

```C
int fesetenv(
   const fenv_t *penv
);
```

### <a name="parameters"></a>Parametry

*penv*<br/>
Wskaźnik do **fenv_t** obiekt, który zawiera zmiennoprzecinkowe środowiska zgodnie z ustaleniami przez wywołanie do [fegetenv](fegetenv1.md) lub [feholdexcept](feholdexcept2.md). Można również określić domyślnego środowiska zmiennoprzecinkowe uruchamiania przy użyciu **FE_DFL_ENV** makra.

## <a name="return-value"></a>Wartość zwracana

Zwraca wartość 0, jeśli skonfigurowano środowisku. W przeciwnym razie zwraca wartość różną od zera.

## <a name="remarks"></a>Uwagi

**Fesetenv** funkcja ustawia bieżącego środowiska zmiennoprzecinkowe z wartości przechowywanej w **fenv_t** obiekt wskazywany przez *penv*. Wartość zmiennoprzecinkowa punktu środowiska to zbiór flagi stanu i tryby kontroli, które mają wpływ na obliczenia liczb zmiennoprzecinkowych. W tym flagi stanu, wyjątki zmiennoprzecinkowe i tryb zaokrąglania.  Jeśli *penv* nie jest **FE_DFL_ENV** lub nie wskazuje na prawidłową **fenv_t** obiekt, kolejne zachowanie jest niezdefiniowany.

Wywołanie tej funkcji ustawia wyjątek flagi stanu, które znajdują się w *penv* obiekt, ale nie wygenerował tych wyjątków.

Aby użyć tej funkcji, należy wyłączyć funkcję zmiennoprzecinkowe funkcje optymalizacji, które może uniemożliwić dostęp przy użyciu `#pragma fenv_access(on)` dyrektywy przed wywołaniem. Aby uzyskać więcej informacji, zobacz [fenv_access](../../preprocessor/fenv-access.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Nagłówek C|Nagłówek C++|
|--------------|--------------|------------------|
|**fesetenv**|\<fenv.h>|\<cfenv>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[fegetenv](fegetenv1.md)<br/>
[feclearexcept](feclearexcept1.md)<br/>
[feholdexcept](feholdexcept2.md)<br/>
[fesetexceptflag](fesetexceptflag2.md)<br/>
