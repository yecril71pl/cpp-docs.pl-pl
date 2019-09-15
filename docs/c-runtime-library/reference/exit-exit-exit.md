---
title: exit, _Exit, _exit
ms.date: 01/02/2018
api_name:
- _exit
- exit
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
- Exit
- _exit
- process/exit
- process/_Exit
- stdlib/exit
- stdlib/_Exit
helpviewer_keywords:
- exit function
- _exit function
- processes, terminating
- function calls, terminating
- process termination, calling
ms.openlocfilehash: fd988ca6339c00b454d673d3bec6f137753ac83a
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70941654"
---
# <a name="exit-_exit-_exit"></a>exit, _Exit, _exit

Kończy proces wywołujący. Funkcja **Exit** kończy działanie po oczyszczeniu; **_exit** i **_exit** przerywają ją od razu.

> [!NOTE]
> Nie należy używać tej metody do zamykania aplikacji platforma uniwersalna systemu Windows (platformy UWP), z wyjątkiem scenariuszy testowania lub debugowania. Sposób programistyczny lub interfejs użytkownika służący do zamykania aplikacji ze sklepu nie są dozwolone zgodnie z [zasadami Microsoft Storeymi](/legal/windows/agreements/store-policies). Aby uzyskać więcej informacji, zobacz [cykl życia aplikacji platformy UWP](/windows/uwp/launch-resume/app-lifecycle). Aby uzyskać więcej informacji o aplikacjach systemu Windows 10, zobacz [przewodniki dotyczące wykonywania aplikacji dla systemu Windows 10](https://developer.microsoft.com/windows/apps).

## <a name="syntax"></a>Składnia

```C
void exit(
   int const status
);
void _Exit(
   int const status
);
void _exit(
   int const status
);
```

### <a name="parameters"></a>Parametry

*status*<br/>
Zakończ działanie kodu stanu.

## <a name="remarks"></a>Uwagi

Funkcje **Exit**, **_exit** i **_exit** przerywają proces wywołujący. Funkcja **Exit** wywołuje destruktory dla obiektów lokalnych wątków, a następnie wywołuje — w kolejności ostatniej-w-pierwszej-wychodzącej (LIFO) — funkcje, które są zarejestrowane przez **atexit —** i **_onexit**, a następnie opróżnia wszystkie bufory plików przed zakończeniem podstawowych. Funkcje **_exit** i **_exit** przerywają proces bez niszczenia obiektów lokalnych wątków lub przetwarzania funkcji **atexit —** lub **_onexit** oraz bez opróżniania buforów strumieni.

Mimo że wywołania **Exit**, **_exit** i **_exit** nie zwracają wartości, wartość w polu *stan* jest udostępniana dla środowiska hosta lub oczekującego procesu wywołującego, jeśli taki istnieje, po zakończeniu procesu. Zazwyczaj obiekt wywołujący ustawia wartość *status* na 0, aby wskazać normalne wyjście lub inną wartość, aby wskazać błąd. Wartość *stanu* jest dostępna dla polecenia Batch systemu operacyjnego **ERRORLEVEL** i jest reprezentowana przez jedną z dwóch stałych: **EXIT_SUCCESS**, który reprezentuje wartość 0 lub **EXIT_FAILURE**, która reprezentuje wartość 1.

Funkcje **Exit**, **_exit**, **_exit**, **quick_exit**, **_cexit**i **_c_exit** zachowują się w następujący sposób.

|Funkcja|Opis|
|--------------|-----------------|
|**Opuść**|Wykonuje kompletne procedury kończenia biblioteki C, kończy proces i dostarcza podany kod stanu do środowiska hosta.|
|**_Exit**|Wykonuje minimalne procedury kończenia biblioteki C, kończy proces i dostarcza podany kod stanu do środowiska hosta.|
|**_exit**|Wykonuje minimalne procedury kończenia biblioteki C, kończy proces i dostarcza podany kod stanu do środowiska hosta.|
|**quick_exit**|Wykonuje szybkie procedury kończenia biblioteki C, kończy proces i dostarcza podany kod stanu do środowiska hosta.|
|**_cexit**|Wykonuje kompletne procedury kończenia biblioteki C i powraca do obiektu wywołującego. Nie kończy procesu.|
|**_c_exit**|Wykonuje minimalne procedury kończenia biblioteki C i powraca do obiektu wywołującego. Nie kończy procesu.|

Po wywołaniu funkcji **Exit**, **_exit** lub **_exit** , destruktory dla wszelkich obiektów tymczasowych lub automatycznych, które istnieją w czasie wywołania nie są wywoływane. Obiekt automatyczny jest niestatycznym obiektem lokalnym zdefiniowanym w funkcji. Obiekt tymczasowy jest obiektem, który jest tworzony przez kompilator, taki jak wartość zwrócona przez wywołanie funkcji. Aby zniszczyć obiekt automatyczny przed wywołaniem metody **Exit**, **_exit**lub **_exit**, jawnie Wywołaj destruktor dla obiektu, jak pokazano poniżej:

```cpp
void last_fn() {}
    struct SomeClass {} myInstance{};
    // ...
    myInstance.~SomeClass(); // explicit destructor call
    exit(0);
}
```

Nie należy używać **DLL_PROCESS_ATTACH** do wywoływania metody **Exit** z **DllMain**. Aby zamknąć funkcję **DllMain** , zwróć **wartość false** z **DLL_PROCESS_ATTACH**.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**Exit**, **_exit**, **_exit**|\<Process. h > lub \<STDLIB. h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_exit.c
// This program returns an exit code of 1. The
// error code could be tested in a batch file.

#include <stdlib.h>

int main( void )
{
   exit( 1 );
}
```

## <a name="see-also"></a>Zobacz także

[Procedury kontroli środowiska](../../c-runtime-library/process-and-environment-control.md)<br/>
[abort](abort.md)<br/>
[atexit](atexit.md)<br/>
[_cexit, _c_exit](cexit-c-exit.md)<br/>
[_exec, _wexec, funkcje](../../c-runtime-library/exec-wexec-functions.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
[quick_exit](quick-exit1.md)<br/>
[_spawn, _wspawn, funkcje](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
