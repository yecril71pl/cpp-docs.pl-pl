---
title: quick_exit1
ms.date: 11/04/2016
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
helpviewer_keywords:
- quick_exit function
ms.assetid: ecfbdae6-01c4-45fa-aaeb-b368e1de2a9c
ms.openlocfilehash: 50f1ee72cce04c2bebc8f7396a2b6fad98301dd7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62358038"
---
# <a name="quickexit"></a>quick_exit

Powoduje zakończenie normalne programu występuje.

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

**Quick_exit** funkcja nie może zwracać do obiektu wywołującego.

## <a name="remarks"></a>Uwagi

**Quick_exit** funkcja powoduje zakończenie normalne programu. Wywoływanych przez nią żadne funkcje nie zarejestrowane przez **atexit**, **_onexit** lub zarejestrowany przez programy obsługi sygnału **sygnału** funkcji. Zachowanie jest niezdefiniowane, jeżeli **quick_exit** jest wywoływana więcej niż po lub w przypadku **wyjść** funkcja jest również nazywany.

**Quick_exit** wywołań w ostatni na wejściu, kolejność FIFO (LIFO), funkcje zarejestrowany przez funkcję **at_quick_exit**, z wyjątkiem tych funkcji, które już wywoływana, gdy funkcja została zarejestrowana.  Zachowanie jest niezdefiniowane, jeżeli [longjmp](longjmp.md) podczas wywoływania zarejestrowanych funkcja, która zakończy się wywołanie funkcji zostanie nawiązane połączenie.

Po wywołaniu funkcji zarejestrowanych **quick_exit** wywołuje **_Exit** przy użyciu *stan* wartość do zwrócenia kontroli dla środowiska hosta.

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
