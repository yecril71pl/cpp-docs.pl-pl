---
title: _cexit, _c_exit
ms.date: 11/04/2016
api_name:
- _c_exit
- _cexit
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
- _cexit
- c_exit
- _c_exit
- cexit
helpviewer_keywords:
- cleanup operations during processes
- cexit function
- _c_exit function
- _cexit function
- c_exit function
ms.assetid: f3072045-9924-4b1a-9fef-b0dcd6d12663
ms.openlocfilehash: aa25d73bef1d85adfed77ba926e2d381e02e45e8
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939255"
---
# <a name="_cexit-_c_exit"></a>_cexit, _c_exit

Wykonuje operacje czyszczenia i zwraca bez zakończenia procesu.

## <a name="syntax"></a>Składnia

```C
void _cexit( void );
void _c_exit( void );
```

## <a name="remarks"></a>Uwagi

Funkcja **_cexit** wywołuje, w kolejności ostatniej-w, pierwszej (LIFO), funkcje zarejestrowane przez **atexit —** i **_onexit**. Następnie **_cexit** opróżnia wszystkie bufory we/wy i zamyka wszystkie otwarte strumienie przed zwróceniem. **_c_exit** jest taka sama jak **_exit** , ale powraca do procesu wywołującego bez przetwarzania buforów strumieni **atexit —** lub **_onexit** lub opróżniania. W poniższej tabeli przedstawiono zachowanie elementów **Exit**, **_exit**, **_cexit**i **_c_exit** .

|Funkcja|Zachowanie|
|--------------|--------------|
|**Opuść**|Wykonuje kompletne procedury kończenia biblioteki C, kończy proces i kończy pracę z dostarczonym kodem stanu.|
|**_exit**|Wykonuje szybkie procedury kończenia biblioteki C, kończy proces i kończy pracę z dostarczonym kodem stanu.|
|**_cexit**|Wykonuje kompletne procedury kończenia biblioteki C i powraca do obiektu wywołującego, ale nie kończy procesu.|
|**_c_exit**|Wykonuje szybkie procedury kończenia biblioteki C i powraca do obiektu wywołującego, ale nie kończy procesu.|

Po wywołaniu funkcji **_cexit** lub **_c_exit** , destruktory dla wszelkich tymczasowych lub automatycznych obiektów, które istnieją w czasie wywołania nie są wywoływane. Obiekt automatyczny jest obiektem, który jest zdefiniowany w funkcji, w której obiekt nie został zadeklarowany jako statyczny. Obiekt tymczasowy jest obiektem utworzonym przez kompilator. Aby zniszczyć obiekt automatyczny przed wywołaniem metody **_cexit** lub **_c_exit**, jawnie Wywołaj destruktor dla obiektu w następujący sposób:

```cpp
myObject.myClass::~myClass( );
```

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_cexit**|\<process.h>|
|**_c_exit**|\<process.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Procedury kontroli środowiska](../../c-runtime-library/process-and-environment-control.md)<br/>
[abort](abort.md)<br/>
[atexit](atexit.md)<br/>
[_exec, _wexec, funkcje](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
[_spawn, _wspawn, funkcje](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
