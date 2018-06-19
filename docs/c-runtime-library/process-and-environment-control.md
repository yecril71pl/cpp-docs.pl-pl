---
title: Proces i kontroli środowiska | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.programs
dev_langs:
- C++
helpviewer_keywords:
- processes, stopping
- processes, administrative tasks
- parent process
- processes, starting
- environment control routines
- process control routines
ms.assetid: 7fde74c3-c2a6-4d15-84b8-092160d60c3e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e52284db986ec642724f97aae75a9af004339b40
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32392474"
---
# <a name="process-and-environment-control"></a>Procedury kontroli środowiska

Procedury kontroli procesu umożliwia uruchamianie, zatrzymywanie i zarządzanie nimi procesy w programie. Pobierz i zmieniać informacje o środowisku systemu operacyjnego za pomocą procedury kontroli środowiska.

## <a name="process-and-environment-control-functions"></a>Proces i funkcje kontroli środowiska

|Procedura|Zastosowanie|
|-------------|---------|
|[abort](../c-runtime-library/reference/abort.md)|Przerwij proces bez opróżniania buforów lub wywołaniem funkcji zarejestrowane przez **atexit —** i **_onexit —**|
|[assert](../c-runtime-library/reference/assert-macro-assert-wassert.md)|Testowanie błąd logiczny|
|[_ASSERT, _asserte —](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) makra|Podobnie jak **assert**, ale są dostępne tylko w wersjach debugowania biblioteki wykonawczej|
|[atexit](../c-runtime-library/reference/atexit.md)|Procedury harmonogramem do wykonania na zakończenie programu|
|[_beginthread, _beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md)|Tworzenie nowego wątku w procesie systemu operacyjnego Windows|
|[_cexit](../c-runtime-library/reference/cexit-c-exit.md)|Wykonaj **zakończyć** procedury zakończenia (na przykład opróżniania buforów), następnie zwrócić kontrolkę do wywoływania programu bez przerywa proces|
|[_c_exit](../c-runtime-library/reference/cexit-c-exit.md)|Wykonaj **_exit —** zakończenia procedury, następnie zwrócić kontrolkę do wywoływania programu bez przerywa proces|
|[_cwait](../c-runtime-library/reference/cwait.md)|Poczekaj na zakończenie innego procesu|
|[_endthread, _endthreadex](../c-runtime-library/reference/endthread-endthreadex.md)|Zakończenie wątku systemu operacyjnego Windows|
|[_execl, _wexecl](../c-runtime-library/reference/execl-wexecl.md)|Wykonaj nowy proces z listą argumentów|
|[_execle, _wexecle](../c-runtime-library/reference/execle-wexecle.md)|Wykonaj nowy proces z listą argumentów i danego środowiska|
|[_execlp, _wexeclp](../c-runtime-library/reference/execlp-wexeclp.md)|Wykonywanie za pomocą nowego procesu **ścieżki** zmienną i argumentu listy|
|[_execlpe, _wexeclpe](../c-runtime-library/reference/execlpe-wexeclpe.md)|Wykonywanie za pomocą nowego procesu **ścieżki** zmiennej danego środowiska i listy argumentów|
|[_execv, _wexecv](../c-runtime-library/reference/execv-wexecv.md)|Wykonaj nowy proces z tablica argumentów|
|[_execve, _wexecve](../c-runtime-library/reference/execve-wexecve.md)|Wykonaj nowy proces z tablica argumentów i danego środowiska|
|[_execvp, _wexecvp](../c-runtime-library/reference/execvp-wexecvp.md)|Wykonywanie za pomocą nowego procesu **ścieżki** zmienną i argument tablicy|
|[_execvpe, _wexecvpe](../c-runtime-library/reference/execvpe-wexecvpe.md)|Wykonywanie za pomocą nowego procesu **ścieżki** zmiennej danego środowiska, a tablica argumentów|
|[Zakończ](../c-runtime-library/reference/exit-exit-exit.md)|Wywołanie funkcji w zarejestrowany przez **atexit —** i **_onexit —**, opróżnienia buforów wszystkie, zamknij otwarte pliki i zakończenie procesu|
|[_exit —](../c-runtime-library/reference/exit-exit-exit.md)|Zakończenie procesu natychmiast bez wywoływania elementu **atexit —** lub **_onexit —** lub opróżnianie buforów|
|[getenv —, _wgetenv —](../c-runtime-library/reference/getenv-wgetenv.md), [getenv_s —, _wgetenv_s —](../c-runtime-library/reference/getenv-s-wgetenv-s.md)|Pobierz wartość zmiennej środowiskowej|
|[_getpid](../c-runtime-library/reference/getpid.md)|Pobierz identyfikator procesu|[System::Diagnostics::process::ID](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.id.aspx)|
|[longjmp](../c-runtime-library/reference/longjmp.md)|Przywróć zapisany stosu środowiska; Umożliwia wykonanie nielokalne **goto**|
|[_onexit —](../c-runtime-library/reference/onexit-onexit-m.md)|Procedury harmonogramem do wykonania po zakończeniu programu; zachowania zgodności z programem Microsoft C/C++ version 7.0 i starszych wersji|
|[_pclose](../c-runtime-library/reference/pclose.md)|Poczekaj, aż nowe procesora poleceń i zamknąć strumienia skojarzone potoku|
|[perror, _wperror](../c-runtime-library/reference/perror-wperror.md)|Drukuj komunikat o błędzie|
|[_pipe](../c-runtime-library/reference/pipe.md)|Tworzenie potoku do odczytywania i zapisywania|
|[_popen, _wpopen](../c-runtime-library/reference/popen-wpopen.md)|Tworzenie potoku i wykonywanie polecenia|
|[_putenv —, _wputenv —](../c-runtime-library/reference/putenv-wputenv.md), [_putenv_s —, _wputenv_s —](../c-runtime-library/reference/putenv-s-wputenv-s.md)|Dodaj lub zmień wartość zmiennej środowiskowej|
|[raise](../c-runtime-library/reference/raise.md)|Wysyłanie sygnałów do wywoływania procesu|
|[setjmp](../c-runtime-library/reference/setjmp.md)|Zapisz stosu środowiska; Służy do wykonywania innych niż lokalne **goto**|
|[signal](../c-runtime-library/reference/signal.md)|Sygnał przerwania dojścia|
|[_spawnl, _wspawnl](../c-runtime-library/reference/spawnl-wspawnl.md)|Tworzenie i wykonywanie nowego procesu z określona lista argumentów|
|[_spawnle, _wspawnle](../c-runtime-library/reference/spawnle-wspawnle.md)|Tworzenie i wykonywanie nowego procesu określona lista argumentów i środowiska|
|[_spawnlp, _wspawnlp](../c-runtime-library/reference/spawnlp-wspawnlp.md)|Tworzenie i wykonywanie nowego procesu przy użyciu **ścieżki** zmienną i określona lista argumentów|
|[_spawnlpe, _wspawnlpe](../c-runtime-library/reference/spawnlpe-wspawnlpe.md)|Tworzenie i wykonywanie nowego procesu przy użyciu **ścieżki** zmiennej, określonego środowiska i listy argumentów|
|[_spawnv, _wspawnv](../c-runtime-library/reference/spawnv-wspawnv.md)|Tworzenie i wykonywanie nowego procesu z określonego argumentu tablicy|
|[_spawnve, _wspawnve](../c-runtime-library/reference/spawnve-wspawnve.md)|Tworzenie i wykonywanie nowego procesu z określonego środowiska i Tablica argumentów|
|[_spawnvp, _wspawnvp](../c-runtime-library/reference/spawnvp-wspawnvp.md)|Tworzenie i wykonywanie nowego procesu przy użyciu **ścieżki** zmienną i określony argument tablicy|
|[_spawnvpe, _wspawnvpe](../c-runtime-library/reference/spawnvpe-wspawnvpe.md)|Tworzenie i wykonywanie nowego procesu przy użyciu **ścieżki** zmiennej, określonego środowiska i Tablica argumentów|
|[system, _wsystem](../c-runtime-library/reference/system-wsystem.md)|Wykonanie polecenia systemu operacyjnego|

 W systemie operacyjnym Windows proces jest odpowiednikiem ikrę procesu. Żaden proces, można użyć **_cwait —** oczekiwania innego procesu, dla którego jest znany identyfikator procesu.

 Różnica między **_exec —** i **_spawn** rodzin jest to, że **_spawn** funkcja może zwrócić kontrolkę z nowego procesu do wywoływania procesu. W **_spawn** funkcji procesu wywołującego, a nowy proces znajdują się w pamięci chyba że **_p_overlay —** jest określona. W **_exec —** funkcji, nowe nakładki procesu przetwarzania wywołujący, więc formantu nie można wrócić do procesu wywołującego, o ile nie wystąpił błąd podczas próby rozpoczęcia realizacji nowego procesu.

 Różnice między funkcje w **_exec —** rodziny, jak również między tymi w **_spawn** rodziny, obejmują metodę lokalizowania plików do wykonania jako nowy proces formularza, w których argumentów są przekazywane do nowego procesu i metody konfiguracji środowiska, jak pokazano w poniższej tabeli. Funkcja, która przekazuje listy argumentów, gdy liczba argumentów jest stałe, lub jest znany w czasie kompilacji. Funkcja, która przekazuje wskaźnik do tablicę zawierającą argumenty, gdy liczba argumentów jest określana w czasie wykonywania. Informacje przedstawione w poniższej tabeli dotyczą również odpowiedników znaków dwubajtowych **_spawn** i **_exec —** funkcji.

### <a name="spawn-and-exec-function-families"></a>_spawn i _exec — rodzin — funkcja

|Funkcje|Zlokalizuj plik za pomocą zmiennej ścieżki|Przekazywanie argumentów Konwencji|Ustawienia środowiska|
|---------------|--------------------------------------|----------------------------------|--------------------------|
|**_execl —**, **_spawnl —**|Nie|Lista|Dziedziczone z wywołaniem procesu|
|**_execle —**, **_spawnle —**|Nie|Lista|Wskaźnik do tabeli środowiska dla nowego procesu jako ostatni argument|
|**_execlp —**, **_spawnlp —**|Tak|Lista|Dziedziczone z wywołaniem procesu|
|**_execvpe —**, **_spawnvpe —**|Tak|Tablica|Wskaźnik do tabeli środowiska dla nowego procesu jako ostatni argument|
|**_execlpe —**, **_spawnlpe —**|Tak|Lista|Wskaźnik do tabeli środowiska dla nowego procesu jako ostatni argument|
|**_execv —**, **_spawnv —**|Nie|Tablica|Dziedziczone z wywołaniem procesu|
|**_execve —**, **_spawnve —**|Nie|Tablica|Wskaźnik do tabeli środowiska dla nowego procesu jako ostatni argument|
|**_execvp —**, **_spawnvp —**|Tak|Tablica|Dziedziczone z wywołaniem procesu|

## <a name="see-also"></a>Zobacz też

[Procedury czasu wykonywania języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)<br/>
