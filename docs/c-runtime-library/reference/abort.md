---
title: przerwij
ms.date: 1/02/2018
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
ms.openlocfilehash: d8cb190e36a64e8bd8cfcb75bc9a19c2a394fc48
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62342201"
---
# <a name="abort"></a>przerwij

Przerywa bieżący proces i zwraca kod błędu.

> [!NOTE]
> Nie należy używać tej metody do zamykania aplikacji Microsoft Store lub aplikacji uniwersalnych platformy Windows (UWP), z wyjątkiem testowania i debugowania scenariuszy. Sposoby Programmatic lub interfejs użytkownika, zamknąć Store app nie są dozwolone zgodnie z opisem w [zasady Microsoft Store](/legal/windows/agreements/store-policies). Aby uzyskać więcej informacji, zobacz [cykl życia aplikacji platformy uniwersalnej systemu Windows](/windows/uwp/launch-resume/app-lifecycle).

## <a name="syntax"></a>Składnia

```C
void abort( void );
```

## <a name="return-value"></a>Wartość zwracana

**Przerwij** nie zwraca formantu do procesu wywołującego. Domyślnie sprawdza obsługę sygnału przerwania i zgłasza `SIGABRT` ile jest on ustawiony. Następnie **przerwać** kończy bieżący proces i zwraca kod wyjścia dla procesu nadrzędnego.

## <a name="remarks"></a>Uwagi

**Microsoft Specific**

Domyślnie, gdy aplikacja jest wbudowana w bibliotekę wykonawczej debugowania **przerwać** procedury wyświetli komunikat o błędzie przed `SIGABRT` jest wywoływane. W przypadku aplikacji konsoli uruchomionych w trybie konsoli komunikat jest wysyłany do `STDERR`. Aplikacje komputerowe Windows i aplikacji konsoli w trybie okienkowym wyświetli komunikat w oknie komunikatu. Aby pominąć komunikat, należy użyć [_set_abort_behavior](set-abort-behavior.md) wyczyść `_WRITE_ABORT_MSG` flagi. Wyświetlany komunikat zależy od wersji środowiska wykonawczego. W przypadku aplikacji skompilowanych przy użyciu najnowszej wersji programu Visual C++ komunikat jest podobny do tego:

> R6010 — metodę abort() została wywołana

W poprzednich wersjach biblioteki wykonawczej C ten komunikat został wyświetlony:

> Ta aplikacja zażądała środowiska uruchomieniowego do jej zakończenia w nietypowy sposób. Aby uzyskać więcej informacji, skontaktuj się z zespołem pomocy technicznej w aplikacji.

Gdy program jest skompilowany w trybie debugowania, w oknie komunikatu Wyświetla opcje **przerwać**, **ponów**, lub **Ignoruj**. Jeśli użytkownik wybierze **przerwać**, program kończy działanie natychmiast i zwraca kod zakończenia 3. Jeśli użytkownik wybierze **ponów**, Debuger jest wywoływany dla debugowania just in time, jeśli jest dostępny. Jeśli użytkownik wybierze **Ignoruj**, **przerwać** kontynuuje normalne przetwarzanie.

W kompilacjach do sprzedaży detalicznej i debugowania **przerwać** sprawdza, czy program obsługi sygnału przerwania ustawiono. Jeśli ustawiono program obsługi sygnałów inny niż domyślny, **przerwać** wywołania `raise(SIGABRT)`. Użyj [sygnału](signal.md) funkcję, aby skojarzyć funkcję obsługi sygnału przerwania z `SIGABRT` sygnału. Może wykonywać akcje niestandardowe — na przykład czyścić zasoby lub rejestrować informacje — i kończyć aplikację własnym kodem błędu w funkcji obsługi. Jeśli nie zdefiniowano żadnych programu obsługi sygnałów niestandardowych, **przerwać** zgłaszaj `SIGABRT` sygnału.

Domyślnie w kompilacjach nieprzeznaczonych do debugowania aplikacji pulpitu i konsoli **przerwać** następnie wywołuje mechanizm usługi raportowania błędów Windows (znana wcześniej jako odzyskiwania po awarii. Watson) zgłaszać awarie do firmy Microsoft. To zachowanie może być włączona lub wyłączona przez wywołanie metody `_set_abort_behavior` i ustawianie lub maskowanie `_CALL_REPORTFAULT` flagi. Gdy flaga jest ustawiona, Windows wyświetla okno komunikatu, które zawiera tekst podobny do tego "Problem spowodował program przestanie działać poprawnie." Użytkownik może wybrać wywoływanie debugera za pomocą **debugowania** przycisku, lub wybierz **Zamknij program** przycisk, aby zakończyć aplikację z kodu błędu, który jest zdefiniowany przez system operacyjny.

Jeśli program obsługi raportowania błędów Windows nie zostanie wywołany, następnie **przerwać** wywołania [_exit](exit-exit-exit.md) aby zakończyć proces z zakończenia kodu 3 i zwraca kontrolę do procesu nadrzędnego lub systemu operacyjnego. `_exit` nie opróżnia buforów strumienia lub czy `atexit` / `_onexit` przetwarzania.

Aby uzyskać więcej informacji na temat debugowania CRT, zobacz [techniki testowania CRT](/visualstudio/debugger/crt-debugging-techniques).

**End specyficzny dla Microsoft**

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**abort**|\<process.h > lub \<stdlib.h >|

## <a name="example"></a>Przykład

Poniższy program próbuje otworzyć plik i przerywa, jeśli próba nie powiedzie się.

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