---
title: _purecall
ms.date: 4/2/2020
api_name:
- _purecall
- _o__purecall
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
- ntoskrnl.exe
- ucrtbase.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- purecall
- _purecall
helpviewer_keywords:
- _purecall function
- purecall function
ms.assetid: 56135d9b-3403-4e22-822d-e714523801cc
ms.openlocfilehash: f841bc70a4a5365bb9cc6086dd752bd2a1b583ed
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338487"
---
# <a name="_purecall"></a>_purecall

Domyślny program obsługi błędów wywołania czystej funkcji wirtualnej. Kompilator generuje kod do wywołania tej funkcji, gdy wywoływana jest funkcja czystego wirtualnego elementu członkowskiego.

## <a name="syntax"></a>Składnia

```C
extern "C" int __cdecl _purecall();
```

## <a name="remarks"></a>Uwagi

Funkcja **_purecall** jest szczegóły implementacji specyficzne dla firmy Microsoft kompilatora Microsoft C++. Ta funkcja nie jest przeznaczona do wywoływania przez kod bezpośrednio i nie ma deklaracji nagłówka publicznego. Jest to udokumentowane w tym miejscu, ponieważ jest to eksport publiczny biblioteki wykonawczej C.

Wywołanie czystej funkcji wirtualnej jest błędem, ponieważ nie ma implementacji. Kompilator generuje kod do wywołania funkcji obsługi błędów **_purecall,** gdy wywoływana jest czysta funkcja wirtualna. Domyślnie **_purecall** kończy program. Przed zakończeniem funkcja **_purecall** wywołuje funkcję **_purecall_handler,** jeśli została ustawiona dla procesu. Można zainstalować własną funkcję obsługi błędów dla wywołań funkcji czysto wirtualnych, aby przechwycić je do debugowania lub raportowania. Aby użyć własnego programu obsługi błędów, należy utworzyć funkcję, która ma **podpis _purecall_handler,** a następnie użyj [_set_purecall_handler,](get-purecall-handler-set-purecall-handler.md) aby uczynić ją bieżącym programem obsługi.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

Funkcja **_purecall** nie ma deklaracji nagłówka. **_purecall_handler** typedef jest zdefiniowany \<w>.

## <a name="see-also"></a>Zobacz też

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[_get_purecall_handler, _set_purecall_handler](get-purecall-handler-set-purecall-handler.md)<br/>
