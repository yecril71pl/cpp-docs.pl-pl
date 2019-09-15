---
title: fegetenv
ms.date: 04/05/2018
api_name:
- fetegenv
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
- fegetenv
- fenv/fegetenv
helpviewer_keywords:
- fetegenv function
ms.assetid: 68962421-6978-4b27-8e4c-ad1577830cf6
ms.openlocfilehash: b2e3566eb96174d0f0ccd6beb401824cc052c995
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70941245"
---
# <a name="fegetenv"></a>fegetenv

Przechowuje bieżące środowisko zmiennoprzecinkowe w określonym obiekcie.

## <a name="syntax"></a>Składnia

```C
int fegetenv(
   fenv_t *penv
);
```

### <a name="parameters"></a>Parametry

*penv*<br/>
Wskaźnik do obiektu **fenv_t** , aby zawierał bieżące wartości środowisk zmiennoprzecinkowych.

## <a name="return-value"></a>Wartość zwracana

Zwraca wartość 0, jeśli środowisko zmiennoprzecinkowe zostało pomyślnie zapisane w *PENV*. W przeciwnym razie zwraca wartość różną od zera.

## <a name="remarks"></a>Uwagi

Funkcja **fegetenv** przechowuje bieżące środowisko zmiennoprzecinkowe w obiekcie wskazywanym przez *PENV*. Środowisko zmiennoprzecinkowe jest zestawem flag stanu i trybów kontroli, które wpływają na obliczenia zmiennoprzecinkowe. Obejmuje to tryb kierunku zaokrąglenia oraz flagi stanu dla wyjątków zmiennoprzecinkowych.  Jeśli *PENV* nie wskazuje prawidłowego obiektu **fenv_t** , następne zachowanie jest niezdefiniowane.

Aby użyć tej funkcji, należy wyłączyć optymalizacje zmiennoprzecinkowe, które mogą uniemożliwić dostęp przy użyciu `#pragma fenv_access(on)` dyrektywy przed wywołaniem. Aby uzyskać więcej informacji, zobacz [fenv_access](../../preprocessor/fenv-access.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Nagłówek języka C|C++nagłówki|
|--------------|--------------|------------------|
|**fegetenv**|\<fenv.h>|\<cfenv>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[fesetenv](fesetenv1.md)<br/>
