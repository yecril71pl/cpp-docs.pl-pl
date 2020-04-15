---
title: przerwij
ms.date: 4/2/2020
api_name:
- abort
- _o_abort
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
- Abort
helpviewer_keywords:
- aborting current process
- abort function
- processes, aborting
ms.openlocfilehash: 1f70f54783ce6f6d28fdda028af4fd5a205aeb0b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81350919"
---
# <a name="abort"></a>przerwij

Przerywa bieżący proces i zwraca kod błędu.

> [!NOTE]
> Nie należy używać tej metody do zamykania aplikacji ze Sklepu Microsoft lub aplikacji platformy uniwersalnej systemu Windows (UWP), z wyjątkiem scenariuszy testowania lub debugowania. Sposób zamykania aplikacji ze Sklepu jest zabroniony zgodnie z [zasadami sklepu Microsoft Store.](/legal/windows/agreements/store-policies) Aby uzyskać więcej informacji, zobacz [cykl życia aplikacji platformy uniwersalnej](/windows/uwp/launch-resume/app-lifecycle)systemu .

## <a name="syntax"></a>Składnia

```C
void abort( void );
```

## <a name="return-value"></a>Wartość zwracana

**abort** nie zwraca kontroli do procesu wywołującego. Domyślnie sprawdza, czy program obsługi sygnału `SIGABRT` przerwania i podnosi, jeśli jeden jest ustawiony. Następnie **przerwania** kończy bieżący proces i zwraca kod zakończenia do procesu nadrzędnego.

## <a name="remarks"></a>Uwagi

**Specyficzne dla firmy Microsoft**

Domyślnie, gdy aplikacja jest zbudowana z biblioteki wykonawczej debugowania, `SIGABRT` procedura **przerwania** wyświetla komunikat o błędzie przed wywoływaniem. W przypadku aplikacji konsoli działających w trybie konsoli wiadomość jest wysyłana do . `STDERR` Aplikacje klasyczne systemu Windows i aplikacje konsoli działające w trybie okienkowym wyświetlają komunikat w oknie komunikatu. Aby pominąć wiadomość, użyj [_set_abort_behavior,](set-abort-behavior.md) `_WRITE_ABORT_MSG` aby wyczyścić flagę. Wyświetlany komunikat zależy od wersji używanego środowiska wykonawczego. W przypadku aplikacji utworzonych przy użyciu najnowszych wersji programu Visual C++komunikat przypomina następującą następującą:

> R6010 - abort() został nazwany

W poprzednich wersjach biblioteki wykonawczej języka C wyświetlany był ten komunikat:

> Ta aplikacja zażądała środowiska wykonawczego, aby zakończyć go w nietypowy sposób. Aby uzyskać więcej informacji, skontaktuj się z zespołem pomocy technicznej aplikacji.

Gdy program jest kompilowany w trybie debugowania, w oknie komunikatu są wyświetlane opcje **Przerwania,** **Ponów próbę**lub **Ignoruj**. Jeśli użytkownik wybierze **abort,** program kończy się natychmiast i zwraca kod zakończenia 3. Jeśli użytkownik wybierze **ponów próbę,** debuger jest wywoływany do debugowania just-in-time, jeśli jest dostępny. Jeśli użytkownik wybierze **opcję Ignoruj,** **przerwanie** kontynuuje normalne przetwarzanie.

W kompilacjach zarówno detalicznych, jak i debugowania **przerwać** następnie sprawdza, czy program obsługi sygnału przerwania jest ustawiony. Jeśli ustawiono nieobe domyślny program `raise(SIGABRT)`obsługi sygnału, **przerwanie** wywołania . Użyj funkcji [sygnału,](signal.md) aby skojarzyć `SIGABRT` funkcję obsługi sygnału przerwania z sygnałem. Można wykonać akcje niestandardowe — na przykład oczyścić zasoby lub informacje dziennika — i zakończyć aplikację za pomocą własnego kodu błędu w funkcji obsługi. Jeśli nie zdefiniowano niestandardowego obsługi sygnału, **przerwanie** nie podnosi sygnału. `SIGABRT`

Domyślnie w kompilacjach innych niż debugowanie aplikacji klasycznych lub konsoli **przerwać** następnie wywołuje mechanizm raportowania błędów systemu Windows (dawniej znany jako Dr Watson) do zgłaszania błędów do firmy Microsoft. To zachowanie można włączyć lub `_set_abort_behavior` wyłączyć, wywołując i `_CALL_REPORTFAULT` ustawiając lub maskując flagę. Gdy flaga jest ustawiona, system Windows wyświetla okno komunikatu z tekstem o treści "Problem spowodował, że program przestał działać poprawnie". Użytkownik może wywołać debuger za pomocą przycisku **debugowania** lub wybrać przycisk **Zamknij program,** aby zakończyć aplikację kodem błędu zdefiniowanym przez system operacyjny.

Jeśli program obsługi raportowania błędów systemu Windows nie jest wywoływany, a następnie **przerwać** wywołania [_exit,](exit-exit-exit.md) aby zakończyć proces z kodem zakończenia 3 i zwraca kontrolę do procesu nadrzędnego lub systemu operacyjnego. `_exit`nie opróżnia buforów `atexit` / `_onexit` strumienia ani nie przetwarza.

Aby uzyskać więcej informacji na temat debugowania CRT, zobacz [Techniki debugowania CRT](/visualstudio/debugger/crt-debugging-techniques).

**Koniec z programem Microsoft**

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**Przerwać**|\<> lub \<>|

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

## <a name="see-also"></a>Zobacz też

[Użycie przerywania](../../cpp/using-abort.md)<br/>
[funkcja przerwania](../../c-language/abort-function-c.md)<br/>
[Kontrola procesu i środowiska](../../c-runtime-library/process-and-environment-control.md)<br/>
[_exec, funkcje _wexec](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[wywołaj](raise.md)<br/>
[sygnał](signal.md)<br/>
[_spawn, _wspawn, funkcje](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[_debug](../../c-runtime-library/debug.md)<br/>
[_set_abort_behavior](set-abort-behavior.md)
