---
title: _purecall
ms.date: 11/04/2016
apiname:
- _purecall
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
- ntoskrnl.exe
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- purecall
- _purecall
helpviewer_keywords:
- _purecall function
- purecall function
ms.assetid: 56135d9b-3403-4e22-822d-e714523801cc
ms.openlocfilehash: a7a6db42dc4b8d9b2962a66c7866aae9db55eb3b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50541192"
---
# <a name="purecall"></a>_purecall

Domyślne czystą mfunkcję wirtualną wywołanie procedurę obsługi błędów. Kompilator generuje kod, aby wywołać tę funkcję, gdy wywoływana jest czystej wirtualnej funkcji składowej.

## <a name="syntax"></a>Składnia

```C
extern "C" int __cdecl _purecall();
```

## <a name="remarks"></a>Uwagi

**_Purecall —** funkcja jest specyficzne dla firmy Microsoft szczegółów implementacji kompilatora Microsoft Visual C++. Ta funkcja nie jest przeznaczony do bezpośredniego wywoływania w kodzie i ma żadna deklaracja publicznych nagłówka. Jest opisane w tym miejscu ponieważ jest on publiczny eksportu biblioteki środowiska uruchomieniowego C.

Wywołanie czystej funkcji wirtualnej występuje błąd, ponieważ jej nie ma implementacji. Kompilator generuje kod, aby wywołać **_purecall —** funkcji obsługi błędu, gdy wywoływana jest czysta funkcja wirtualna. Domyślnie **_purecall —** kończy program. Przed zakończeniem, **_purecall —** funkcja wywołuje **_purecall_handler** działać, jeśli bufor został ustawiony dla procesu. Można zainstalować własną funkcję obsługi błędu dla wywołań czystą funkcję wirtualną, wyłapuj je na potrzeby debugowania lub do celów raportowania. Aby użyć własnego procedurę obsługi błędów, należy utworzyć funkcję, która ma **_purecall_handler** podpisu, następnie za pomocą [_set_purecall_handler —](get-purecall-handler-set-purecall-handler.md) się bieżący program obsługi.

## <a name="requirements"></a>Wymagania

**_Purecall —** funkcja nie zawiera deklarację nagłówka. **_Purecall_handler** typedef jest zdefiniowany w \<stdlib.h >.

## <a name="see-also"></a>Zobacz także

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[_get_purecall_handler, _set_purecall_handler](get-purecall-handler-set-purecall-handler.md)<br/>
