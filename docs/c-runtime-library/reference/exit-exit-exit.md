---
title: "exit, _exit — _exit — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 1/02/2018
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _exit
- exit
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
- Exit
- _exit
- process/exit
- process/_Exit
- stdlib/exit
- stdlib/_Exit
dev_langs: C++
helpviewer_keywords:
- exit function
- _exit function
- processes, terminating
- function calls, terminating
- process termination, calling
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: dbb54b756363da2069bbc4bface4e971fcab91e4
ms.sourcegitcommit: a5d8f5b92cb5e984d5d6c9d67fe8a1241f3fe184
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/05/2018
---
# <a name="exit-exit-exit"></a>exit, _exit — _exit —

Kończy proces wywoływania. `exit` Funkcja kończy je po oczyszczania; `_exit` i `_Exit` przerwać jego działanie od razu.

> [!NOTE]
> Nie należy używać tej metody można zamknąć aplikacji uniwersalnych platformy systemu Windows (UWP), z wyjątkiem w testowania i debugowania scenariuszy. Programowe lub interfejsu użytkownika sposobów Zamknij aplikację sklepu nie są dozwolone zgodnie z [zasady Microsoft Store](/legal/windows/agreements/store-policies). Aby uzyskać więcej informacji, zobacz [cykl życia aplikacji platformy uniwersalnej systemu Windows](/windows/uwp/launch-resume/app-lifecycle). Aby uzyskać więcej informacji o aplikacji systemu Windows 10, zobacz [prowadzi instrukcje dla aplikacji systemu Windows 10](http://go.microsoft.com/fwlink/p/?linkid=619133).

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

_Stan_  
Kod stanu zakończenia.

## <a name="remarks"></a>Uwagi

`exit`, `_Exit` i `_exit` funkcje przerwanie procesu wywołującego. `exit` Funkcja wywołuj destruktory dla obiektów wątków lokalnych, następnie wywołuje — w kolejności (LIFO) ostatnich w pierwszym poza — funkcje, które są zarejestrowane przez `atexit` i `_onexit`, a następnie czyści wszystkie bufory pliku przed jego kończy proces. `_Exit` i `_exit` funkcje zakończenie procesu bez niszczenie obiektów wątków lokalnych lub przetwarzania `atexit` lub `_onexit` funkcje i bez opróżniania buforów strumienia.

Mimo że `exit`, `_Exit` i `_exit` wywołania nie zwraca wartości, wartość w _stan_ dostępnego w środowisku hosta lub oczekującego procesu wywołującego, jeśli istnieje, po zamknięciu procesu. Zazwyczaj zestawy wywołującego _stan_ wartość na 0, aby wskazać normalne zakończenia lub wartość wystąpił błąd. _Stan_ wartość jest dostępna dla polecenia batch systemu operacyjnego `ERRORLEVEL` i jest reprezentowana przez jedną z dwóch: `EXIT_SUCCESS`, który reprezentuje wartość 0, lub `EXIT_FAILURE`, reprezentuje wartość 1.

`exit`, `_Exit`, `_exit`, `quick_exit`, `_cexit`, I `_c_exit` funkcje działają w następujący sposób.

|Funkcja|Opis|
|--------------|-----------------|
|`exit`|Wykonuje pełne procedury zakończenia biblioteki C, kończy proces i zawiera kod stanu dostarczony dla środowiska hosta.|
|`_Exit`|Wykonuje minimalnego procedury zakończenia biblioteki C, kończy proces i zawiera kod stanu dostarczony dla środowiska hosta.|
|`_exit`|Wykonuje minimalnego procedury zakończenia biblioteki C, kończy proces i zawiera kod stanu dostarczony dla środowiska hosta.|
|`quick_exit`|Wykonuje szybkie procedury zakończenia biblioteki C, kończy proces i zawiera kod stanu dostarczony dla środowiska hosta.|
|`_cexit`|Wykonuje pełne procedury zakończenia biblioteki C i zwraca do obiektu wywołującego. Nie zakończyć proces.|
|`_c_exit`|Wykonuje minimalnego procedury zakończenia biblioteki C i zwraca do obiektu wywołującego. Nie zakończyć proces.|

Podczas wywoływania `exit`, `_Exit` lub `_exit` funkcji destruktory dla tymczasowych lub automatyczne obiektów, które istnieją w momencie wywołania nie są nazywane. Automatyczne obiekt jest obiektem lokalnym niestatyczna zdefiniowany w funkcji. Tymczasowy obiekt to obiekt utworzony przez kompilator, np. wartość zwrócona przez wywołanie funkcji. Aby zniszczyć automatyczne obiekt przed wywołaniem `exit`, `_Exit`, lub `_exit`, jawnie Wywołaj destruktor dla obiektu, jak pokazano poniżej:

```cpp
void last_fn() {}
    struct SomeClass {} myInstance{};
    // ...
    myInstance.~SomeClass(); // explicit destructor call
    exit(0);
}
```

Nie należy używać `DLL_PROCESS_ATTACH` w celu wywołania `exit` z `DllMain`. Aby zakończyć `DLLMain` funkcji, aby uzyskać `FALSE` z `DLL_PROCESS_ATTACH`.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|`exit`, `_Exit`, `_exit`|\<process.h > lub \<stdlib.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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

[Procedury kontroli środowiska](../../c-runtime-library/process-and-environment-control.md)  
[abort](../../c-runtime-library/reference/abort.md)  
[atexit](../../c-runtime-library/reference/atexit.md)  
[_cexit, _c_exit](../../c-runtime-library/reference/cexit-c-exit.md)  
[_exec, _wexec, funkcje](../../c-runtime-library/exec-wexec-functions.md)  
[_onexit, _onexit_m](../../c-runtime-library/reference/onexit-onexit-m.md)  
[quick_exit](../../c-runtime-library/reference/quick-exit1.md)  
[_spawn, _wspawn, funkcje](../../c-runtime-library/spawn-wspawn-functions.md)  
[system, _wsystem](../../c-runtime-library/reference/system-wsystem.md)  
