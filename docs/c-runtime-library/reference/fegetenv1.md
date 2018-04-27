---
title: fegetenv | Dokumenty Microsoft
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
dev_langs:
- C++
helpviewer_keywords:
- fetegenv function
ms.assetid: 68962421-6978-4b27-8e4c-ad1577830cf6
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a3569b015784f41fae4a4a91b6a32fe08dd57284
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="fegetenv"></a>fegetenv

Przechowuje bieżącego środowiska zmiennoprzecinkowe określonego obiektu.

## <a name="syntax"></a>Składnia

```C
int fegetenv(
   fenv_t *penv
);
```

### <a name="parameters"></a>Parametry

*penv*<br/>
Wskaźnik do **fenv_t** obiektu zawiera bieżące wartości zmiennoprzecinkowych środowiska.

## <a name="return-value"></a>Wartość zwracana

Zwraca wartość 0, jeśli środowisko zmiennoprzecinkowe pomyślnie była przechowywana w *penv*. W przeciwnym razie zwraca wartość inną niż zero.

## <a name="remarks"></a>Uwagi

**Fegetenv** funkcja przechowuje bieżącego środowiska liczb zmiennoprzecinkowych w obiekcie wskazywana przez *penv*. Wartość zmiennoprzecinkowa punktu środowiska to zbiór flagi stanu i tryby kontroli, które mają wpływ na obliczenia liczb zmiennoprzecinkowych. W tym trybu zaokrąglania kierunku i flagi stanu zmiennoprzecinkowych wyjątków.  Jeśli *penv* nie wskazuje na prawidłową **fenv_t** obiekt, kolejne zachowanie jest niezdefiniowany.

Aby użyć tej funkcji, należy wyłączyć funkcję zmiennoprzecinkowe funkcje optymalizacji, które może uniemożliwić dostęp przy użyciu `#pragma fenv_access(on)` dyrektywy przed wywołaniem. Aby uzyskać więcej informacji, zobacz [fenv_access](../../preprocessor/fenv-access.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Nagłówek C|Nagłówek C++|
|--------------|--------------|------------------|
|**fegetenv**|\<fenv.h>|\<cfenv>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[fesetenv](fesetenv1.md)<br/>
