---
title: quick_exit1
ms.date: 11/04/2016
api_name:
- quick_exit
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
- quick_exit
- process/quick_exit
- stdlib/quick_exit
helpviewer_keywords:
- quick_exit function
ms.assetid: ecfbdae6-01c4-45fa-aaeb-b368e1de2a9c
ms.openlocfilehash: 86246ed7a32dcd2f12b38aa4148570fc5fb3b7a6
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70949662"
---
# <a name="quick_exit"></a>quick_exit

Powoduje, że normalne zakończenie programu ma miejsce.

## <a name="syntax"></a>Składnia

```C
__declspec(noreturn) void quick_exit(
    int status
);
```

### <a name="parameters"></a>Parametry

*status*<br/>
Kod stanu do zwrócenia do środowiska hosta.

## <a name="return-value"></a>Wartość zwracana

Funkcja **quick_exit** nie może zwrócić do obiektu wywołującego.

## <a name="remarks"></a>Uwagi

Funkcja **quick_exit** powoduje normalne zakończenie działania programu. Nie wywołuje żadnych funkcji zarejestrowanych przez **atexit —** , **_onexit** lub programy obsługi sygnałów zarejestrowane przez funkcję **sygnału** . Zachowanie jest niezdefiniowane, jeśli **quick_exit** jest wywoływana więcej niż raz lub funkcja **Exit** jest również wywoływana.

Funkcja **quick_exit** wywołuje, w kolejności Last-in, First-Out (LIFO), funkcje zarejestrowane przez **at_quick_exit**, z wyjątkiem tych funkcji, które są już wywoływane podczas rejestrowania funkcji.  Zachowanie jest niezdefiniowane, jeśli wywołanie [longjmp](longjmp.md) jest wykonywane podczas wywołania zarejestrowanej funkcji, która spowodowałaby zakończenie wywołania funkcji.

Po wywołaniu zarejestrowanych funkcji **quick_exit** wywołuje **_exit** przy użyciu wartości *status* , aby zwrócić kontrolę do środowiska hosta.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**quick_exit**|\<Process. h > lub \<STDLIB. h >|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Procedury kontroli środowiska](../../c-runtime-library/process-and-environment-control.md)<br/>
[abort](abort.md)<br/>
[atexit](atexit.md)<br/>
[_exec, _wexec, funkcje](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
[_spawn, _wspawn, funkcje](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
