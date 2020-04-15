---
title: _cexit, _c_exit
ms.date: 4/2/2020
api_name:
- _c_exit
- _cexit
- _o__cexit
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 9eb856efca054423465aa7d30092edaf83a65eeb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81333532"
---
# <a name="_cexit-_c_exit"></a>_cexit, _c_exit

Wykonuje operacje oczyszczania i zwraca bez zakończenia procesu.

## <a name="syntax"></a>Składnia

```C
void _cexit( void );
void _c_exit( void );
```

## <a name="remarks"></a>Uwagi

Funkcja **_cexit** wywołuje, w kolejności last-in, first-out (LIFO), funkcje zarejestrowane przez **atexit** i **_onexit**. Następnie **_cexit** opróżnia wszystkie bufory we/wy i zamyka wszystkie otwarte strumienie przed zwróceniem. **_c_exit** jest taka sama jak **_exit,** ale powraca do procesu wywołującego bez przetwarzania **atexit** lub **_onexit** lub opróżniania buforów strumienia. Zachowanie **wyjścia**, **_exit** **, _cexit**i **_c_exit** jest pokazane w poniższej tabeli.

|Funkcja|Zachowanie|
|--------------|--------------|
|**Wyjścia**|Wykonuje pełne procedury zakończenia biblioteki C, kończy proces i kończy pracę z podanym kodem stanu.|
|**_exit**|Wykonuje szybkie procedury zakończenia biblioteki C, kończy proces i kończy pracę z podanym kodem stanu.|
|**_cexit**|Wykonuje pełne procedury zakończenia biblioteki C i zwraca do obiektu wywołującego, ale nie kończy procesu.|
|**_c_exit**|Wykonuje szybkie procedury zakończenia biblioteki C i zwraca do obiektu wywołującego, ale nie kończy procesu.|

Po wywołaniu **funkcji _cexit** lub **_c_exit** destruktory dla wszystkich obiektów tymczasowych lub automatycznych, które istnieją w czasie wywołania, nie są wywoływane. Obiekt automatyczny jest obiektem zdefiniowanym w funkcji, w której obiekt nie jest zadeklarowany jako statyczny. Obiekt tymczasowy jest obiektem utworzonym przez kompilator. Aby zniszczyć obiekt automatyczny przed wywołaniem **_cexit** lub **_c_exit,** jawnie wywołać destruktora dla obiektu, w następujący sposób:

```cpp
myObject.myClass::~myClass( );
```

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_cexit**|\<> proces.h|
|**_c_exit**|\<> proces.h|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Kontrola procesu i środowiska](../../c-runtime-library/process-and-environment-control.md)<br/>
[Przerwać](abort.md)<br/>
[atexit](atexit.md)<br/>
[_exec, funkcje _wexec](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
[_spawn, _wspawn, funkcje](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
