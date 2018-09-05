---
title: Exit _Exit, _exit | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 1/02/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- exit function
- _exit function
- processes, terminating
- function calls, terminating
- process termination, calling
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8a06fa858ac7d2d8458bd3adf3fb44ca7bdee929
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43678157"
---
# <a name="exit-exit-exit"></a>exit, _Exit, _exit

Kończy proces wywołujący. **Wyjść** funkcja kończy go po oczyszczaniu; **_exit** i **_Exit** Zakończ jej działanie natychmiast.

> [!NOTE]
> Nie należy używać tej metody do zamykania aplikacji uniwersalnych platformy Windows (UWP), z wyjątkiem testowania i debugowania scenariuszy. Sposoby Programmatic lub interfejs użytkownika, zamknąć Store app nie są dozwolone zgodnie z opisem w [zasady Microsoft Store](/legal/windows/agreements/store-policies). Aby uzyskać więcej informacji, zobacz [cykl życia aplikacji platformy uniwersalnej systemu Windows](/windows/uwp/launch-resume/app-lifecycle). Aby uzyskać więcej informacji na temat aplikacji systemu Windows 10, zobacz [instrukcje przewodników dotyczących aplikacji systemu Windows 10](https://developer.microsoft.com/en-us/windows/apps).

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

*Stan* kod stanu zakończenia.

## <a name="remarks"></a>Uwagi

**Wyjść**, **_Exit** i **_exit** funkcje kończą proces wywołujący. **Wyjść** funkcja wywołuje destruktory obiektów lokalnych wątków, następnie wywołuje — w ostatniej wejściu — pierwszy na wyjściu (LIFO) kolejności — funkcje, które są zarejestrowane przez **atexit** i **_onexit**, a następnie opróżnia wszystkie bufory plików przed zakończeniem procesu. **_Exit** i **_exit** funkcje zakończyć proces bez niszczenie obiektów wątków lokalnych lub przetwarzania **atexit** lub **_onexit**funkcje i bez opróżniania buforów strumieni.

Mimo że **wyjść**, **_Exit** i **_exit** wywołania nie zwracają wartości, wartość w *stan* staje się dostępny dla środowiska hosta lub oczekiwania procesu wywołującego, jeśli istnieje, po zakończeniu procesu. Zwykle ustawia obiekt wywołujący *stan* wartość na 0, aby wskazać normalne wyjście lub na inną wartość do wskazania błędu. *Stan* wartość jest dostępna dla polecenia wsadowego systemu operacyjnego **ERRORLEVEL** i jest reprezentowana przez jedną z dwóch stałych: **EXIT_SUCCESS**, która reprezentuje wartość 0 lub **EXIT_FAILURE**, która reprezentuje wartość 1.

**Wyjść**, **_Exit**, **_exit**, **quick_exit**, **_cexit —**, i **_c_exit —** funkcje zachowują się w następujący sposób.

|Funkcja|Opis|
|--------------|-----------------|
|**Zakończ**|Wykonuje kompletne procedury kończenia biblioteki C, kończy proces i zapewnia dostarczonym kodem stanu dla środowiska hosta.|
|**_Exit**|Wykonuje minimalny procedury kończenia biblioteki C, kończy proces i zapewnia dostarczonym kodem stanu dla środowiska hosta.|
|**_exit**|Wykonuje minimalny procedury kończenia biblioteki C, kończy proces i zapewnia dostarczonym kodem stanu dla środowiska hosta.|
|**quick_exit**|Wykonuje szybkie procedury kończenia biblioteki C, kończy proces i zapewnia dostarczonym kodem stanu dla środowiska hosta.|
|**_cexit**|Wykonuje kompletne procedury kończenia biblioteki C i powraca do obiektu wywołującego. Nie kończy procesu.|
|**_c_exit**|Wykonuje minimalny procedury kończenia biblioteki C i powraca do obiektu wywołującego. Nie kończy procesu.|

Gdy wywołujesz **wyjść**, **_Exit** lub **_exit** funkcji, destruktory tymczasowego lub automatycznego obiektu, który istnieje w momencie zgłoszenia wywołania nie są wywoływane. Obiekt automatyczny jest niestatyczną lokalnego obiektu zdefiniowany w funkcji. Obiekt tymczasowy jest obiektem, który jest tworzony przez kompilator, np. wartość zwrócona przez wywołanie funkcji. Aby zniszczyć obiekt automatyczny przed wywołaniem **wyjść**, **_Exit**, lub **_exit**, należy jawnie wywołać destruktor obiektu, jak pokazano poniżej:

```cpp
void last_fn() {}
    struct SomeClass {} myInstance{};
    // ...
    myInstance.~SomeClass(); // explicit destructor call
    exit(0);
}
```

Nie używaj **DLL_PROCESS_ATTACH** do wywołania **wyjść** z **DllMain**. Aby zakończyć działanie **DLLMain** działać i zwracać **FALSE** z **DLL_PROCESS_ATTACH**.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**Zakończ**, **_Exit**, **_exit**|\<process.h > lub \<stdlib.h >|

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
