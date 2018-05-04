---
title: _cexit, _c_exit | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _c_exit
- _cexit
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
- _cexit
- c_exit
- _c_exit
- cexit
dev_langs:
- C++
helpviewer_keywords:
- cleanup operations during processes
- cexit function
- _c_exit function
- _cexit function
- c_exit function
ms.assetid: f3072045-9924-4b1a-9fef-b0dcd6d12663
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b0840ccec85d46a13984b65ebe99e53b968bedeb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="cexit-cexit"></a>_cexit, _c_exit

Wykonuje operacje oczyszczania i zwraca bez Trwa kończenie procesu.

## <a name="syntax"></a>Składnia

```C
void _cexit( void );
void _c_exit( void );
```

## <a name="remarks"></a>Uwagi

**_Cexit —** funkcji wywołań w ostatniej w kolejności wytworzenia, funkcje zarejestrowane przez **atexit —** i **_onexit —**. Następnie **_cexit —** opróżnia wszystkie bufory We/Wy i zamknięcie wszystkich otwartych strumieni przed zwróceniem. **_c_exit —** jest taka sama jak **_exit —** , ale zwraca do wywoływania procesu bez jej przetwarzania **atexit —** lub **_onexit —** lub opróżnianie buforów strumienia. Zachowanie **zakończyć**, **_exit —**, **_cexit —**, i **_c_exit —** przedstawiono w poniższej tabeli.

|Funkcja|Zachowanie|
|--------------|--------------|
|**Zakończ**|Wykonuje pełne procedury zakończenia biblioteki C, kończy proces i kończy działanie z kodem stanu dostarczony.|
|**_exit —**|Wykonuje szybkie procedury zakończenia biblioteki C, kończy proces i kończy działanie z kodem stanu dostarczony.|
|**_cexit**|Wykonuje pełne procedury zakończenia biblioteki C i zwraca obiekt wywołujący, ale nie kończy proces.|
|**_c_exit**|Wykonuje szybkie procedury zakończenia biblioteki C i zwraca obiekt wywołujący, ale nie kończy proces.|

Podczas wywoływania **_cexit —** lub **_c_exit —** funkcje, destruktory dla tymczasowych lub automatyczne obiektów, które istnieją w momencie wywołania nie są wywoływane. Automatyczne obiekt jest obiekt, który jest zdefiniowany w funkcji, której obiekt nie jest zadeklarowany jako statyczny. Tymczasowy obiekt to obiekt utworzony przez kompilator. Aby zniszczyć automatyczne obiekt przed wywołaniem **_cexit —** lub **_c_exit —**, jawnie Wywołaj destruktor dla obiektu, w następujący sposób:

```cpp
myObject.myClass::~myClass( );
```

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_cexit**|\<process.h >|
|**_c_exit**|\<process.h >|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Procedury kontroli środowiska](../../c-runtime-library/process-and-environment-control.md)<br/>
[abort](abort.md)<br/>
[atexit](atexit.md)<br/>
[_exec, _wexec, funkcje](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
[_spawn, _wspawn, funkcje](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
