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
ms.openlocfilehash: df080d1ed8c5a00711468a159acb07159ad31930
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2018
ms.locfileid: "51329413"
---
# <a name="process-and-environment-control"></a>Procedury kontroli środowiska

Procedury kontroli procesu umożliwiają uruchamianie, zatrzymywanie i zarządzać procesami z poziomu używanego programu. Procedury kontroli środowiska umożliwia pobieranie i modyfikowanie informacji na temat środowiska systemu operacyjnego.

## <a name="process-and-environment-control-functions"></a>Proces i funkcje kontroli środowiska

|Procedura|Zastosowanie|
|-------------|---------|
|[abort](../c-runtime-library/reference/abort.md)|Przerwij proces bez opróżniania buforów lub wywołaniem funkcji zarejestrowane przez **atexit** i **_onexit**|
|[assert](../c-runtime-library/reference/assert-macro-assert-wassert.md)|Testowanie błąd logiczny|
|[_ASSERT, _asserte —](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) makra|Podobnie jak **assert**, ale jest dostępna tylko w wersji debugowania bibliotek wykonawczych|
|[atexit](../c-runtime-library/reference/atexit.md)|Zaplanuj procedury do wykonania na kończenie działania programu|
|[_beginthread, _beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md)|Utwórz nowy wątek na temat procesu systemu operacyjnego Windows|
|[_cexit](../c-runtime-library/reference/cexit-c-exit.md)|Wykonaj **wyjść** procedury kończenia (na przykład opróżniania buforów), następnie zwraca formantu do program wywołujący bez zakończenie procesu|
|[_c_exit](../c-runtime-library/reference/cexit-c-exit.md)|Wykonaj **_exit** procedury kończenia następnie zwraca formantu do program wywołujący bez zakończenie procesu|
|[_cwait](../c-runtime-library/reference/cwait.md)|Zaczekaj, aż inny proces zakończy się|
|[_endthread, _endthreadex](../c-runtime-library/reference/endthread-endthreadex.md)|Zakończenie wątku systemu operacyjnego Windows|
|[_execl, _wexecl](../c-runtime-library/reference/execl-wexecl.md)|Wykonania nowego procesu z listy argumentów|
|[_execle, _wexecle](../c-runtime-library/reference/execle-wexecle.md)|Wykonania nowego procesu z listy argumentów i biorąc pod uwagę środowiska|
|[_execlp, _wexeclp](../c-runtime-library/reference/execlp-wexeclp.md)|Wykonywanie za pomocą nowego procesu **ścieżki** zmiennej i listą argumentów|
|[_execlpe, _wexeclpe](../c-runtime-library/reference/execlpe-wexeclpe.md)|Wykonywanie za pomocą nowego procesu **ścieżki** zmiennej danego środowiska i listą argumentów|
|[_execv, _wexecv](../c-runtime-library/reference/execv-wexecv.md)|Wykonania nowego procesu z tablica argumentów|
|[_execve, _wexecve](../c-runtime-library/reference/execve-wexecve.md)|Wykonania nowego procesu z tablica argumentów i biorąc pod uwagę środowiska|
|[_execvp, _wexecvp](../c-runtime-library/reference/execvp-wexecvp.md)|Wykonywanie za pomocą nowego procesu **ścieżki** tablicy w zmiennej i argument|
|[_execvpe, _wexecvpe](../c-runtime-library/reference/execvpe-wexecvpe.md)|Wykonywanie za pomocą nowego procesu **ścieżki** zmiennej danego środowiska i Tablica argumentów|
|[Zakończ](../c-runtime-library/reference/exit-exit-exit.md)|Wywoływanie funkcji zarejestrowane przez **atexit** i **_onexit**Opróżnij wszystkie bufory, zamknij wszystkie otwieranie plików, a następnie Zakończ proces|
|[_exit](../c-runtime-library/reference/exit-exit-exit.md)|Zakończenie procesu bezpośrednio bez wywoływania **atexit** lub **_onexit** lub opróżniania buforów|
|[getenv, _wgetenv —](../c-runtime-library/reference/getenv-wgetenv.md), [getenv_s —, _wgetenv_s —](../c-runtime-library/reference/getenv-s-wgetenv-s.md)|Pobierz wartość zmiennej środowiskowej|
|[_getpid](../c-runtime-library/reference/getpid.md)|Pobierz numer identyfikacyjny ID procesu|
|[longjmp](../c-runtime-library/reference/longjmp.md)|Przywróć zapisane stos środowiska; Umożliwia wykonywanie nielokalne **goto**|
|[_onexit](../c-runtime-library/reference/onexit-onexit-m.md)|Zaplanuj procedury do wykonania po zakończeniu program; zachowania zgodności z programem Microsoft C/C++ version 7.0 i starszych wersji|
|[_pclose](../c-runtime-library/reference/pclose.md)|Poczekaj na nowy procesor polecenia, a następnie zamknąć strumienia na rurze skojarzonej|
|[perror, _wperror](../c-runtime-library/reference/perror-wperror.md)|Drukuj komunikat o błędzie|
|[_pipe](../c-runtime-library/reference/pipe.md)|Utwórz potok do odczytu i zapisu|
|[_popen, _wpopen](../c-runtime-library/reference/popen-wpopen.md)|Tworzenie potoku, a następnie wykonaj polecenie|
|[_putenv, _wputenv —](../c-runtime-library/reference/putenv-wputenv.md), [_putenv_s, _wputenv_s —](../c-runtime-library/reference/putenv-s-wputenv-s.md)|Dodaj lub zmień wartość zmiennej środowiskowej|
|[raise](../c-runtime-library/reference/raise.md)|Wysyłanie sygnałów do procesu wywołującego|
|[setjmp](../c-runtime-library/reference/setjmp.md)|Zapisz stos środowiska; wykonywanie innego niż lokalne za pomocą **goto**|
|[signal](../c-runtime-library/reference/signal.md)|Obsługi sygnału przerwania|
|[_spawnl, _wspawnl](../c-runtime-library/reference/spawnl-wspawnl.md)|Tworzenie i wykonania nowego procesu z określoną listę argumentów|
|[_spawnle, _wspawnle](../c-runtime-library/reference/spawnle-wspawnle.md)|Tworzenie i wykonania nowego procesu z określoną listę argumentów i środowiska|
|[_spawnlp, _wspawnlp](../c-runtime-library/reference/spawnlp-wspawnlp.md)|Tworzenie i wykonywanie nowego procesu przy użyciu **ścieżki** zmienną i określoną listę argumentów|
|[_spawnlpe, _wspawnlpe](../c-runtime-library/reference/spawnlpe-wspawnlpe.md)|Tworzenie i wykonywanie nowego procesu przy użyciu **ścieżki** zmienną, określonego środowiska i listą argumentów|
|[_spawnv, _wspawnv](../c-runtime-library/reference/spawnv-wspawnv.md)|Tworzenie i wykonywanie nowy proces, za pomocą określonego argumentu tablicy|
|[_spawnve, _wspawnve](../c-runtime-library/reference/spawnve-wspawnve.md)|Tworzenie i wykonania nowego procesu przy użyciu określonego środowiska i Tablica argumentów|
|[_spawnvp, _wspawnvp](../c-runtime-library/reference/spawnvp-wspawnvp.md)|Tworzenie i wykonywanie nowego procesu przy użyciu **ścieżki** zmienną i określony argument tablicy|
|[_spawnvpe, _wspawnvpe](../c-runtime-library/reference/spawnvpe-wspawnvpe.md)|Tworzenie i wykonywanie nowego procesu przy użyciu **ścieżki** zmienną, określonego środowiska i Tablica argumentów|
|[system, _wsystem](../c-runtime-library/reference/system-wsystem.md)|Wykonanie polecenia systemu operacyjnego|

W systemie operacyjnym Windows procesu rozmnożonego odpowiada ikrę procesu. Żaden proces, można użyć **_cwait** czekać na inne procesy, dla którego jest znany identyfikator procesu.

Różnica między **_exec** i **_spawn** rodzin jest fakt, że **_spawn** funkcji mogą zwracać kontrolki z nowego procesu do procesu wywołującego. W **_spawn** funkcji procesu wywołującego i nowego procesu znajdują się w pamięci chyba że **_P_OVERLAY** jest określony. W **_exec** funkcji, nowe nakładki proces wywołujący przetwarzania, dzięki czemu formant nie może zwrócić do procesu wywołującego, chyba że wystąpi błąd podczas próby rozpoczęcia realizacji nowego procesu.

Różnice między funkcje w **_exec** rodziny, a także między programami znajdującymi się na **_spawn** rodziny, obejmuje metodę lokalizowania pliku do wykonania jako nowy proces, formularza, w której argumenty są przekazywane do nowego procesu i metody konfiguracji środowiska, jak pokazano w poniższej tabeli. Funkcja, która przekazuje listy argumentów, gdy liczba argumentów jest stałe, lub jest znany w czasie kompilacji. Funkcja, która przekazuje wskaźnik do tablica zawierająca argumenty, gdy liczba argumentów jest ustalany w czasie wykonywania. Informacje przedstawione w poniższej tabeli dotyczą również odpowiedniki o znakach szerokich z **_spawn** i **_exec** funkcji.

### <a name="spawn-and-exec-function-families"></a>_spawn i _exec rodzin — funkcja

|Funkcje|Zlokalizuj plik za pomocą zmiennej PATH|Konwencji przekazywania argumentów|Ustawienia środowiska|
|---------------|--------------------------------------|----------------------------------|--------------------------|
|**_execl**, **_spawnl**|Nie|Lista|Dziedziczone z procesu wywołującego|
|**_execle —**, **_spawnel**|Nie|Lista|Wskaźnik do tabeli środowiska dla nowego procesu jest przekazywany jako ostatni argument|
|**_execlp —**, **_spawnlp —**|Tak|Lista|Dziedziczone z procesu wywołującego|
|**_execvpe**, **_spawnvpe**|Tak|Tablica|Wskaźnik do tabeli środowiska dla nowego procesu jest przekazywany jako ostatni argument|
|**_execlpe —**, **_spawnlpe —**|Tak|Lista|Wskaźnik do tabeli środowiska dla nowego procesu jest przekazywany jako ostatni argument|
|**_execv**, **_spawnv**|Nie|Tablica|Dziedziczone z procesu wywołującego|
|**_execve**, **_spawnve —**|Nie|Tablica|Wskaźnik do tabeli środowiska dla nowego procesu jest przekazywany jako ostatni argument|
|**_execvp —**, **_spawnvp**|Tak|Tablica|Dziedziczone z procesu wywołującego|

## <a name="see-also"></a>Zobacz też

[Procedury czasu wykonywania języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)<br/>
