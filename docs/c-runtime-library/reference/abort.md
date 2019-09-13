---
title: przerwij
ms.date: 01/02/2018
apiname:
- abort
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
- Abort
helpviewer_keywords:
- aborting current process
- abort function
- processes, aborting
ms.openlocfilehash: ee07e50504b53e9e363f8b4fc5e9f4414637c449
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70927477"
---
# <a name="abort"></a>przerwij

Przerywa bieżący proces i zwraca kod błędu.

> [!NOTE]
> Nie należy używać tej metody do zamykania aplikacji Microsoft Store lub platforma uniwersalna systemu Windows (platformy UWP), z wyjątkiem scenariuszy testowania lub debugowania. Sposób programistyczny lub interfejs użytkownika służący do zamykania aplikacji ze sklepu nie są dozwolone zgodnie z [zasadami Microsoft Storeymi](/legal/windows/agreements/store-policies). Aby uzyskać więcej informacji, zobacz [cykl życia aplikacji platformy UWP](/windows/uwp/launch-resume/app-lifecycle).

## <a name="syntax"></a>Składnia

```C
void abort( void );
```

## <a name="return-value"></a>Wartość zwracana

**przerwanie** nie zwraca kontroli do procesu wywołującego. Domyślnie sprawdza obsługę sygnałów przerwania i wywołuje `SIGABRT` , czy jest ustawiona. Następnie **Przerwij przerywa** bieżący proces i zwraca kod zakończenia do procesu nadrzędnego.

## <a name="remarks"></a>Uwagi

**Microsoft Specific**

Domyślnie, gdy aplikacja jest skompilowana przy użyciu biblioteki środowiska uruchomieniowego debugowania, procedura **Abort** wyświetla komunikat o błędzie przed `SIGABRT` podniesieniem. W przypadku aplikacji konsolowych działających w trybie konsoli komunikat jest wysyłany `STDERR`do. Aplikacje klasyczne systemu Windows i aplikacje konsolowe działające w trybie okienkowym wyświetlają komunikat w oknie komunikatu. Aby pominąć komunikat, użyj [_set_abort_behavior](set-abort-behavior.md) , aby wyczyścić `_WRITE_ABORT_MSG` flagę. Wyświetlany komunikat zależy od używanej wersji środowiska uruchomieniowego. W przypadku aplikacji zbudowanych przy użyciu najnowszych wersji wizualizacji C++komunikat jest podobny do następującego:

> R6010-Abort () został wywołany

W poprzednich wersjach biblioteki środowiska uruchomieniowego języka C zostanie wyświetlony następujący komunikat:

> Ta aplikacja zażądała uruchomienia środowiska uruchomieniowego w nietypowy sposób. Aby uzyskać więcej informacji, skontaktuj się z zespołem pomocy technicznej aplikacji.

Gdy program jest kompilowany w trybie debugowania, w oknie komunikatu są wyświetlane opcje **przerwania**, **ponawiania**lub **ignorowania**. Jeśli użytkownik wybierze przycisk **Przerwij**, program zakończy działanie natychmiast i zwróci kod zakończenia 3. Jeśli użytkownik wybierze pozycję **Ponów próbę**, debuger jest wywoływany dla debugowania just-in-Time, jeśli jest dostępny. Jeśli użytkownik wybierze opcję **Ignoruj**, **przerwanie** kontynuuje normalne przetwarzanie.

W przypadku kompilacji detalicznych i debugowania, **Przerwij** następnie sprawdza, czy ustawiono procedurę obsługi sygnałów przerwania. Jeśli ustawiono program obsługi sygnałów inny niż domyślny, **przerywaj** wywołania `raise(SIGABRT)`. Za pomocą funkcji [sygnału](signal.md) Skojarz funkcję obsługi sygnałów przerwania z `SIGABRT` sygnałem. Możesz wykonywać niestandardowe akcje — na przykład czyścić zasoby lub rejestrować informacje, a także kończyć aplikację przy użyciu własnego kodu błędu w funkcji obsługi. Jeśli nie zdefiniowano niestandardowego programu obsługi sygnałów, Metoda **Abort** nie podnosi `SIGABRT` sygnału.

Domyślnie, w kompilacjach niedebugowanych aplikacji klasycznych lub konsolowych, **przerwanie** wywołuje mechanizm usługi Raportowanie błędów systemu Windows (wcześniej znany jako Dr. Watson), aby zgłosić błędy do firmy Microsoft. To zachowanie można włączyć lub wyłączyć przez wywołanie `_set_abort_behavior` i ustawienie lub maskowanie `_CALL_REPORTFAULT` flagi. Gdy flaga jest ustawiona, system Windows wyświetla okno komunikatu z tekstem podobnym do "A problem spowodował, że program przestanie prawidłowo działać". Użytkownik może wybrać opcję wywołania debugera za pomocą przycisku **Debuguj** lub wybrać przycisk **Zamknij program** , aby zakończyć aplikację z kodem błędu zdefiniowanym przez system operacyjny.

Jeśli program obsługi raportowania błędów systemu Windows nie zostanie wywołany, **Przerwij** wywołania [_exit](exit-exit-exit.md) , aby zakończyć proces z kodem zakończenia 3 i zwraca kontrolę do procesu nadrzędnego lub systemu operacyjnego. `_exit`nie opróżnia buforów strumieni ani nie `atexit` / `_onexit` przetwarza.

Aby uzyskać więcej informacji na temat debugowania CRT, zobacz [techniki debugowania CRT](/visualstudio/debugger/crt-debugging-techniques).

**Zakończenie określonych przez firmę Microsoft**

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**abort**|\<Process. h > lub \<STDLIB. h >|

## <a name="example"></a>Przykład

Następujący program próbuje otworzyć plik i przerywa, jeśli próba nie powiedzie się.

```C
// crt_abort.c
// compile with: /TC
// This program demonstrates the use of
// the abort function by attempting to open a file
// and aborts if the attempt fails.

#include  <stdio.h>
#include  <stdlib.h>

int main( void )
{
    FILE    *stream = NULL;
    errno_t err = 0;

    err = fopen_s(&stream, "NOSUCHF.ILE", "r" );
    if ((err != 0) || (stream == NULL))
    {
        perror( "File could not be opened" );
        abort();
    }
    else
    {
        fclose( stream );
    }
}
```

```Output
File could not be opened: No such file or directory
```

## <a name="see-also"></a>Zobacz także

[Użycie funkcji abort](../../cpp/using-abort.md)<br/>
[abort, funkcja](../../c-language/abort-function-c.md)<br/>
[Procedury kontroli środowiska](../../c-runtime-library/process-and-environment-control.md)<br/>
[_exec, _wexec, funkcje](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[raise](raise.md)<br/>
[signal](signal.md)<br/>
[_spawn, _wspawn, funkcje](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[_DEBUG](../../c-runtime-library/debug.md)<br/>
[_set_abort_behavior](set-abort-behavior.md)