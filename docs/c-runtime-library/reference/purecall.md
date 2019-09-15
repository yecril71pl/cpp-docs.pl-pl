---
title: _purecall
ms.date: 11/04/2016
api_name:
- _purecall
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
ms.openlocfilehash: 5d62ec30731ce26c4683afc88474d4bddb63a697
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70950158"
---
# <a name="_purecall"></a>_purecall

Domyślna procedura obsługi błędów wywołania funkcji wirtualnej. Kompilator generuje kod, aby wywołać tę funkcję w przypadku wywołania czystej wirtualnej funkcji członkowskiej.

## <a name="syntax"></a>Składnia

```C
extern "C" int __cdecl _purecall();
```

## <a name="remarks"></a>Uwagi

Funkcja **_purecall** jest szczegółową implementacją kompilatora firmy Microsoft C++ . Ta funkcja nie jest przeznaczona do wywoływania bezpośrednio przez kod i nie ma deklaracji nagłówka publicznego. Jest on udokumentowany w tym miejscu, ponieważ jest publicznym eksportem biblioteki środowiska uruchomieniowego języka C.

Wywołanie czystej funkcji wirtualnej jest błędem, ponieważ nie ma implementacji. Kompilator generuje kod, aby wywołać funkcję procedury obsługi błędów **_purecall** w przypadku wywołania czystej funkcji wirtualnej. Domyślnie **_purecall** kończy program. Przed zakończeniem funkcja **_purecall** wywołuje funkcję **_purecall_handler** , jeśli została ona ustawiona dla procesu. Możesz zainstalować własną funkcję obsługi błędów dla czystych wywołań funkcji wirtualnych, aby przechwycić je do celów debugowania lub raportowania. Aby użyć własnego programu obsługi błędów, należy utworzyć funkcję, która ma sygnaturę **_purecall_handler** , a następnie użyć [_set_purecall_handler](get-purecall-handler-set-purecall-handler.md) w celu udostępnienia jej jako bieżącej procedury obsługi.

## <a name="requirements"></a>Wymagania

Funkcja **_purecall** nie ma deklaracji nagłówka. **_Purecall_handler** typedef jest zdefiniowany w \<STDLIB. h >.

## <a name="see-also"></a>Zobacz także

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[_get_purecall_handler, _set_purecall_handler](get-purecall-handler-set-purecall-handler.md)<br/>
