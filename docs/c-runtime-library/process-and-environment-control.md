---
title: Procedury kontroli środowiska
ms.date: 11/04/2016
f1_keywords:
- c.programs
helpviewer_keywords:
- processes, stopping
- processes, administrative tasks
- parent process
- processes, starting
- environment control routines
- process control routines
ms.assetid: 7fde74c3-c2a6-4d15-84b8-092160d60c3e
ms.openlocfilehash: ed8d15181a171b4b6a436a3e410a99b48232bc6e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217028"
---
# <a name="process-and-environment-control"></a>Procedury kontroli środowiska

Za pomocą procedur kontroli procesu można uruchamiać, zatrzymywać i zarządzać procesami z poziomu programu. Użyj procedur kontroli środowiska, aby uzyskać i zmienić informacje o środowisku systemu operacyjnego.

## <a name="process-and-environment-control-functions"></a>Funkcje sterowania procesami i środowiskami

|Procedura|Zastosowanie|
|-------------|---------|
|[przerwij](../c-runtime-library/reference/abort.md)|Przerwij proces bez opróżniania buforów ani wywoływania funkcji zarejestrowanych przez **atexit —** i **_onexit**|
|[stanowcz](../c-runtime-library/reference/assert-macro-assert-wassert.md)|Test pod kątem błędu logiki|
|[_ASSERT, _ASSERTE](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) makra|Podobnie jak w przypadku **potwierdzeń**, ale dostępne tylko w wersjach debugowania bibliotek czasu wykonywania|
|[atexit](../c-runtime-library/reference/atexit.md)|Planowanie procedur wykonywania przy zakończeniu działania programu|
|[_beginthread, _beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md)|Tworzenie nowego wątku w procesie systemu operacyjnego Windows|
|[_cexit](../c-runtime-library/reference/cexit-c-exit.md)|Wykonaj procedury zakończenia **kończenia** (takie jak bufory opróżniania), a następnie wróć sterowanie do wywoływania programu bez przerywania procesu|
|[_c_exit](../c-runtime-library/reference/cexit-c-exit.md)|Wykonaj **_exit** procedury zakończenia, a następnie wróć sterowanie do wywoływania programu bez przerywania procesu|
|[_cwait](../c-runtime-library/reference/cwait.md)|Poczekaj na zakończenie innego procesu|
|[_endthread, _endthreadex](../c-runtime-library/reference/endthread-endthreadex.md)|Przerwij wątek systemu operacyjnego Windows|
|[_execl, _wexecl](../c-runtime-library/reference/execl-wexecl.md)|Wykonaj nowy proces z listą argumentów|
|[_execle, _wexecle](../c-runtime-library/reference/execle-wexecle.md)|Wykonaj nowy proces z listą argumentów i danym środowiskiem|
|[_execlp, _wexeclp](../c-runtime-library/reference/execlp-wexeclp.md)|Wykonaj nowy proces przy użyciu zmiennej **Path** i listy argumentów|
|[_execlpe, _wexeclpe](../c-runtime-library/reference/execlpe-wexeclpe.md)|Wykonaj nowy proces za pomocą zmiennej **Path** , danego środowiska i listy argumentów|
|[_execv, _wexecv](../c-runtime-library/reference/execv-wexecv.md)|Wykonaj nowy proces z tablicą argumentów|
|[_execve, _wexecve](../c-runtime-library/reference/execve-wexecve.md)|Wykonaj nowy proces z tablicą argumentów i danym środowiskiem|
|[_execvp, _wexecvp](../c-runtime-library/reference/execvp-wexecvp.md)|Wykonaj nowy proces przy użyciu zmiennej **Path** i tablicy argumentów|
|[_execvpe, _wexecvpe](../c-runtime-library/reference/execvpe-wexecvpe.md)|Wykonaj nowy proces za pomocą zmiennej **Path** , danego środowiska i tablicy argumentów|
|[Opuść](../c-runtime-library/reference/exit-exit-exit.md)|Wywołaj funkcje zarejestrowane przez **atexit —** i **_onexit**, Opróżnij wszystkie bufory, zamknij wszystkie otwarte pliki i Przerwij proces|
|[_exit](../c-runtime-library/reference/exit-exit-exit.md)|Przerwij proces natychmiast bez wywoływania **atexit —** lub **_onexit** lub opróżniania buforów|
|[getenv, _wgetenv](../c-runtime-library/reference/getenv-wgetenv.md), [getenv_s, _wgetenv_s](../c-runtime-library/reference/getenv-s-wgetenv-s.md)|Pobierz wartość zmiennej środowiskowej|
|[_getpid](../c-runtime-library/reference/getpid.md)|Pobierz numer IDENTYFIKACYJNy procesu|
|[longjmp](../c-runtime-library/reference/longjmp.md)|Przywróć zapisane środowisko stosu; Użyj jej do wykonania nielokalnego**`goto`**|
|[_onexit](../c-runtime-library/reference/onexit-onexit-m.md)|Zaplanuj wykonywanie procedur po zakończeniu działania programu; Używanie na potrzeby zgodności z Microsoft C/C++ w wersji 7,0 i starszych|
|[_pclose](../c-runtime-library/reference/pclose.md)|Zaczekaj na nowy procesor poleceń i Zamknij strumień w skojarzonym potoku|
|[perror, _wperror](../c-runtime-library/reference/perror-wperror.md)|Komunikat o błędzie drukowania|
|[_pipe](../c-runtime-library/reference/pipe.md)|Tworzenie potoku do odczytu i zapisu|
|[_popen, _wpopen](../c-runtime-library/reference/popen-wpopen.md)|Utwórz potok i wykonaj polecenie|
|[_putenv, _wputenv](../c-runtime-library/reference/putenv-wputenv.md), [_putenv_s _wputenv_s](../c-runtime-library/reference/putenv-s-wputenv-s.md)|Dodaj lub zmień wartość zmiennej środowiskowej|
|[wywołaj](../c-runtime-library/reference/raise.md)|Wyślij sygnał do procesu wywołującego|
|[setjmp](../c-runtime-library/reference/setjmp.md)|Zapisz środowisko stosu; Użyj do wykonywania nie lokalnego**`goto`**|
|[sygnał](../c-runtime-library/reference/signal.md)|Obsługa sygnału przerwania|
|[_spawnl, _wspawnl](../c-runtime-library/reference/spawnl-wspawnl.md)|Tworzenie i wykonywanie nowego procesu z określoną listą argumentów|
|[_spawnle, _wspawnle](../c-runtime-library/reference/spawnle-wspawnle.md)|Tworzenie i wykonywanie nowego procesu z określoną listą argumentów i środowiskiem|
|[_spawnlp, _wspawnlp](../c-runtime-library/reference/spawnlp-wspawnlp.md)|Tworzenie i wykonywanie nowego procesu przy użyciu zmiennej **Path** i określonej listy argumentów|
|[_spawnlpe, _wspawnlpe](../c-runtime-library/reference/spawnlpe-wspawnlpe.md)|Tworzenie i wykonywanie nowego procesu przy użyciu zmiennej **Path** , określonego środowiska i listy argumentów|
|[_spawnv, _wspawnv](../c-runtime-library/reference/spawnv-wspawnv.md)|Utwórz i wykonaj nowy proces z określoną tablicą argumentów|
|[_spawnve, _wspawnve](../c-runtime-library/reference/spawnve-wspawnve.md)|Utwórz i wykonaj nowy proces z określonym środowiskiem i tablicą argumentów|
|[_spawnvp, _wspawnvp](../c-runtime-library/reference/spawnvp-wspawnvp.md)|Tworzenie i wykonywanie nowego procesu przy użyciu zmiennej **Path** i określonej tablicy argumentów|
|[_spawnvpe, _wspawnvpe](../c-runtime-library/reference/spawnvpe-wspawnvpe.md)|Tworzenie i wykonywanie nowego procesu przy użyciu zmiennej **Path** , określonego środowiska i tablicy argumentów|
|[system, _wsystem](../c-runtime-library/reference/system-wsystem.md)|Wykonaj polecenie systemu operacyjnego|

W systemie operacyjnym Windows proces duplikowany jest równoważny procesowi duplikowania. Każdy proces może użyć **_cwait** , aby poczekać na inny proces, dla którego znany jest identyfikator procesu.

Różnica między rodziną **_exec** i **_spawn** polega na tym, że funkcja **_spawn** może zwrócić kontrolę z nowego procesu do procesu wywołującego. W funkcji **_spawn** zarówno proces wywołujący, jak i nowy proces są obecne w pamięci, chyba że określono **_P_OVERLAY** . W funkcji **_exec** nowy proces nakłada proces wywołujący, więc kontrola nie może powrócić do procesu wywołującego, chyba że wystąpi błąd podczas próby rozpoczęcia wykonywania nowego procesu.

Różnice między funkcjami w rodzinie **_exec** , a także wśród tych w rodzinie **_spawn** , obejmują metodę lokalizowania pliku do wykonania jako nowy proces, formularz, w którym argumenty są przekazane do nowego procesu, oraz metodę ustawiania środowiska, jak pokazano w poniższej tabeli. Użyj funkcji, która przekazuje listę argumentów, gdy liczba argumentów jest stała lub jest znana w czasie kompilacji. Użyj funkcji, która przekazuje wskaźnik do tablicy zawierającej argumenty, gdy liczba argumentów ma być określona w czasie wykonywania. Informacje w poniższej tabeli dotyczą także odpowiedników znaków dwubajtowych w funkcjach **_spawn** i **_exec** .

### <a name="_spawn-and-_exec-function-families"></a>_spawn i _exec rodziny funkcji

|Funkcje|Użyj zmiennej PATH do zlokalizowania pliku|Konwencja przekazywania argumentów|Ustawienia środowiska|
|---------------|--------------------------------------|----------------------------------|--------------------------|
|**_execl**, **_spawnl**|Nie|Lista|Dziedziczone z procesu wywołującego|
|**_execle**, **_spawnle**|Nie|Lista|Wskaźnik do tabeli środowiska dla nowego procesu przeszedł jako ostatni argument|
|**_execlp**, **_spawnlp**|Tak|Lista|Dziedziczone z procesu wywołującego|
|**_execvpe**, **_spawnvpe**|Tak|Tablica|Wskaźnik do tabeli środowiska dla nowego procesu przeszedł jako ostatni argument|
|**_execlpe**, **_spawnlpe**|Tak|Lista|Wskaźnik do tabeli środowiska dla nowego procesu przeszedł jako ostatni argument|
|**_execv**, **_spawnv**|Nie|Tablica|Dziedziczone z procesu wywołującego|
|**_execve**, **_spawnve**|Nie|Tablica|Wskaźnik do tabeli środowiska dla nowego procesu przeszedł jako ostatni argument|
|**_execvp**, **_spawnvp**|Tak|Tablica|Dziedziczone z procesu wywołującego|

## <a name="see-also"></a>Zobacz także

[Procedury środowiska uruchomieniowego języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)<br/>
