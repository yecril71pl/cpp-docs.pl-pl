---
title: _cexit, _c_exit
ms.date: 11/04/2016
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
helpviewer_keywords:
- cleanup operations during processes
- cexit function
- _c_exit function
- _cexit function
- c_exit function
ms.assetid: f3072045-9924-4b1a-9fef-b0dcd6d12663
ms.openlocfilehash: a075e8a8e965a195765b86ffa21fed0915dbf5ab
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50495137"
---
# <a name="cexit-cexit"></a>_cexit, _c_exit

Wykonuje operacje oczyszczania i zwraca bez zakończenie debugowanego procesu.

## <a name="syntax"></a>Składnia

```C
void _cexit( void );
void _c_exit( void );
```

## <a name="remarks"></a>Uwagi

**_Cexit —** wywołań w ostatni na wejściu, kolejność FIFO (LIFO), funkcje zarejestrowany przez funkcję **atexit** i **_onexit**. Następnie **_cexit —** opróżnia wszystkie bufory We/Wy i zamyka wszystkie otwarte strumienie przed zwróceniem. **_c_exit —** jest taka sama jak **_exit** , ale powraca do wywoływania proces bez przetwarzania **atexit** lub **_onexit** lub opróżniania buforów strumieni. Zachowanie **wyjść**, **_exit**, **_cexit —**, i **_c_exit —** zostały przedstawione w poniższej tabeli.

|Funkcja|Zachowanie|
|--------------|--------------|
|**Zakończ**|Wykonuje kompletne procedury kończenia biblioteki C, kończy proces i kończy pracę z dostarczonym kodem stanu.|
|**_exit**|Wykonuje szybkie procedury kończenia biblioteki C, kończy proces i kończy pracę z dostarczonym kodem stanu.|
|**_cexit**|Wykonuje kompletne procedury kończenia biblioteki C i powraca do obiektu wywołującego, ale nie kończy procesu.|
|**_c_exit**|Wykonuje szybkie procedury kończenia biblioteki C i powraca do obiektu wywołującego, ale nie kończy procesu.|

Gdy wywołujesz **_cexit —** lub **_c_exit —** funkcje, destruktory tymczasowego lub automatycznego obiektu, który istnieje w momencie zgłoszenia wywołania nie są wywoływane. Obiekt automatyczny jest obiektem, który jest zdefiniowany w funkcji, gdzie obiekt nie został zadeklarowany jako statyczny. Obiekt tymczasowy jest obiektem, który został utworzony przez kompilator. Aby zniszczyć obiekt automatyczny przed wywołaniem **_cexit —** lub **_c_exit —**, należy jawnie wywołać destruktor obiektu w następujący sposób:

```cpp
myObject.myClass::~myClass( );
```

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_cexit**|\<process.h >|
|**_c_exit**|\<process.h >|

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
