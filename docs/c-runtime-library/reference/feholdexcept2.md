---
title: feholdexcept
ms.date: 04/05/2018
api_name:
- feholdexcept
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
- feholdexcept
- fenv/feholdexcept
helpviewer_keywords:
- feholdexcept function
ms.assetid: 88e512ae-b5d8-452c-afe9-c824cd3ef1d8
ms.openlocfilehash: bd55a4ed627d731f7246d589d4b74b4173e31d4e
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70941189"
---
# <a name="feholdexcept"></a>feholdexcept

Zapisuje bieżące środowisko zmiennoprzecinkowe w określonym obiekcie, czyści flagi stanu zmiennoprzecinkowego i, jeśli to możliwe, umieści środowisko zmiennoprzecinkowe w trybie niezatrzymania.

## <a name="syntax"></a>Składnia

```C
int feholdexcept(
   fenv_t *penv
);
```

### <a name="parameters"></a>Parametry

*penv*<br/>
Wskaźnik do obiektu **fenv_t** , który zawiera kopię środowiska zmiennoprzecinkowego.

## <a name="return-value"></a>Wartość zwracana

Zwraca wartość zero, jeśli i tylko wtedy, gdy funkcja może pomyślnie włączyć zatrzymywanie obsługi wyjątków zmiennoprzecinkowych.

## <a name="remarks"></a>Uwagi

Funkcja **feholdexcept** służy do przechowywania stanu bieżącego środowiska zmiennoprzecinkowego w obiekcie **fenv_t** wskazanym przez *PENV*oraz do ustawienia środowiska, aby nie przerywać wykonywania w wyjątkach zmiennoprzecinkowych. Jest to tzw. Tryb niezatrzymania.  Ten tryb jest kontynuowany do momentu przywrócenia środowiska przy użyciu [fesetenv](fesetenv1.md) lub [feupdateenv](feupdateenv.md).

Tej funkcji można użyć na początku procedury podrzędnej, która wymaga ukrycia co najmniej jednego wyjątku zmiennoprzecinkowego z obiektu wywołującego. Aby zgłosić wyjątek, można po prostu usunąć niepożądane wyjątki przy użyciu [feclearexcept,](feclearexcept1.md) a następnie zakończyć tryb niezatrzymania z wywołaniem do **feupdateenv**.

Aby użyć tej funkcji, należy wyłączyć optymalizacje zmiennoprzecinkowe, które mogą uniemożliwić dostęp przy użyciu `#pragma fenv_access(on)` dyrektywy przed wywołaniem. Aby uzyskać więcej informacji, zobacz [fenv_access](../../preprocessor/fenv-access.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Nagłówek języka C|C++nagłówki|
|--------------|--------------|------------------|
|**feholdexcept**|\<fenv.h>|\<cfenv>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[feclearexcept](feclearexcept1.md)<br/>
[fesetenv](fesetenv1.md)<br/>
[feupdateenv](feupdateenv.md)<br/>
