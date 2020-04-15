---
title: exit, _Exit, _exit
ms.date: 4/2/2020
api_name:
- _exit
- exit
- _o__exit
- _o_exit
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
ms.openlocfilehash: 5bdb5ff5c8309e03a49f9518f65a45d5757e9bfa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81347632"
---
# <a name="exit-_exit-_exit"></a>exit, _Exit, _exit

Kończy proces wywoływania. Funkcja **zakończenia** kończy go po oczyszczeniu; **_exit** i **_Exit** natychmiast ją zakończyć.

> [!NOTE]
> Nie należy używać tej metody do zamykania aplikacji platformy uniwersalnej systemu Windows (UWP), z wyjątkiem scenariuszy testowania lub debugowania. Sposób zamykania aplikacji ze Sklepu jest zabroniony zgodnie z [zasadami sklepu Microsoft Store.](/legal/windows/agreements/store-policies) Aby uzyskać więcej informacji, zobacz [cykl życia aplikacji platformy uniwersalnej](/windows/uwp/launch-resume/app-lifecycle)systemu Uniwersalnego . Aby uzyskać więcej informacji o aplikacjach systemu Windows 10, zobacz [Instrukcje dotyczące aplikacji systemu Windows 10](https://developer.microsoft.com/windows/apps).

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

*Stan*<br/>
Kod stanu zakończenia.

## <a name="remarks"></a>Uwagi

Funkcje **exit**, **_Exit** i **_exit** kończą proces wywoływania. Funkcja **zakończenia** wywołuje destruktory dla obiektów lokalnych wątków, a następnie wywołuje — w kolejności LIFO (last-in-first-out) — funkcje zarejestrowane przez **atexit** i **_onexit**, a następnie opróżnia wszystkie bufory plików przed zakończeniem procesu. Funkcje **_Exit** i **_exit** kończą proces bez niszczenia obiektów lokalnych wątków lub przetwarzania **funkcji atexit** lub **_onexit** i bez opróżniania buforów strumienia.

Chociaż **exit**, **_Exit** i **_exit** wywołania nie zwracają wartość, wartość w *stanie* jest udostępniana do środowiska hosta lub oczekiwania procesu wywołującego, jeśli istnieje, po zakończeniu procesu. Zazwyczaj wywołujący ustawia wartość *stanu* na 0, aby wskazać normalne wyjście lub inną wartość, aby wskazać błąd. Wartość *stanu* jest dostępna dla polecenia wsadowego systemu operacyjnego **ERRORLEVEL** i jest reprezentowana przez jedną z dwóch stałych: **EXIT_SUCCESS**, która reprezentuje wartość 0 lub **EXIT_FAILURE**, która reprezentuje wartość 1.

Funkcje **wyjścia**, **_Exit,** **_exit,** **quick_exit,** **_cexit**i **_c_exit** zachowują się w następujący sposób.

|Funkcja|Opis|
|--------------|-----------------|
|**Wyjścia**|Wykonuje pełne procedury zakończenia biblioteki C, kończy proces i udostępnia podany kod stanu do środowiska hosta.|
|**_Exit**|Wykonuje minimalne procedury zakończenia biblioteki C, kończy proces i udostępnia podany kod stanu do środowiska hosta.|
|**_exit**|Wykonuje minimalne procedury zakończenia biblioteki C, kończy proces i udostępnia podany kod stanu do środowiska hosta.|
|**quick_exit**|Wykonuje szybkie procedury zakończenia biblioteki C, kończy proces i udostępnia podany kod stanu do środowiska hosta.|
|**_cexit**|Wykonuje pełne procedury zakończenia biblioteki C i zwraca do wywołującego. Nie kończy procesu.|
|**_c_exit**|Wykonuje minimalne procedury zakończenia biblioteki C i zwraca do wywołującego. Nie kończy procesu.|

Po wywołaniu **funkcji exit**, **_Exit** lub **_exit,** destruktory dla wszystkich obiektów tymczasowych lub automatycznych, które istnieją w czasie wywołania, nie są wywoływane. Obiekt automatyczny jest niestatycznym obiektem lokalnym zdefiniowanym w funkcji. Obiekt tymczasowy jest obiektem, który jest tworzony przez kompilator, takich jak wartość zwracana przez wywołanie funkcji. Aby zniszczyć obiekt automatyczny przed wywołaniem **exit**, **_Exit**lub **_exit**, jawnie wywołać destruktora dla obiektu, jak pokazano poniżej:

```cpp
void last_fn() {}
    struct SomeClass {} myInstance{};
    // ...
    myInstance.~SomeClass(); // explicit destructor call
    exit(0);
}
```

Nie należy używać **DLL_PROCESS_ATTACH** do wywoływania **wyjścia** z **DllMain**. Aby zakończyć funkcję **DLLMain,** zwraca **wartość FAŁSZ** z **DLL_PROCESS_ATTACH**.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**wyjście** **, _Exit,** **_exit**|\<> lub \<>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Zobacz też

[Kontrola procesu i środowiska](../../c-runtime-library/process-and-environment-control.md)<br/>
[Przerwać](abort.md)<br/>
[atexit](atexit.md)<br/>
[_cexit, _c_exit](cexit-c-exit.md)<br/>
[_exec, funkcje _wexec](../../c-runtime-library/exec-wexec-functions.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
[quick_exit](quick-exit1.md)<br/>
[_spawn, _wspawn, funkcje](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
