---
title: quick_exit1 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
apiname:
- quick_exit
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
- quick_exit
- process/quick_exit
- stdlib/quick_exit
dev_langs:
- C++
helpviewer_keywords:
- quick_exit function
ms.assetid: ecfbdae6-01c4-45fa-aaeb-b368e1de2a9c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: de3eb88093db0eea470a0c1d775516574c466ddd
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32405734"
---
# <a name="quickexit"></a>quick_exit

Powoduje, że Kończenie działania programu normalne występuje.

## <a name="syntax"></a>Składnia

```C
__declspec(noreturn) void quick_exit(
    int status
);
```

### <a name="parameters"></a>Parametry

*status*<br/>
Kod stanu, aby powrócić do środowiska hosta.

## <a name="return-value"></a>Wartość zwracana

**Quick_exit** funkcji nie można wrócić do swojego obiektu wywołującego.

## <a name="remarks"></a>Uwagi

**Quick_exit** funkcja powoduje zakończenie normalne programu. Wywołuje żadnych funkcji w zarejestrowany przez **atexit —**, **_onexit —** lub sygnału obsługi zarejestrowanych przez **sygnału** funkcji. Zachowanie jest niezdefiniowana, jeśli **quick_exit** jest wywoływana więcej niż po lub jeśli **zakończyć** funkcja jest również nazywany.

**Quick_exit** funkcji wywołań w ostatniej w kolejności wytworzenia, funkcje zarejestrowane przez **at_quick_exit**, z wyjątkiem tych funkcji już wywoływane, gdy funkcja została zarejestrowana.  Zachowanie jest niezdefiniowana, jeśli [longjmp](longjmp.md) wywołanie podczas wywoływania zarejestrowanej funkcji, który może obsłużyć wywołania funkcji.

Po wywołaniu funkcji zarejestrowanych **quick_exit** wywołuje **_exit —** za pomocą *stan* wartość zwracana kontroli w środowisku hosta.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**quick_exit**|\<process.h > lub \<stdlib.h >|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Procedury kontroli środowiska](../../c-runtime-library/process-and-environment-control.md)<br/>
[abort](abort.md)<br/>
[atexit](atexit.md)<br/>
[_exec, _wexec, funkcje](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
[_spawn, _wspawn, funkcje](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
