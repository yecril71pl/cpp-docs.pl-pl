---
title: Przerwij | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 1/02/2018
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: abort
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
f1_keywords: Abort
dev_langs: C++
helpviewer_keywords:
- aborting current process
- abort function
- processes, aborting
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e6577ca7927d42e12aa62ed100b9572b7270208f
ms.sourcegitcommit: a5d8f5b92cb5e984d5d6c9d67fe8a1241f3fe184
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/05/2018
---
# <a name="abort"></a>przerwij

Przerywa proces bieżącego i zwraca kod błędu.

> [!NOTE]
> Nie używaj tej metody w celu zamknięcia aplikacji Microsoft Store lub [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplikacji, z wyjątkiem testowania i debugowania scenariuszy. Programowe lub interfejsu użytkownika sposobów Zamknij aplikację sklepu nie są dozwolone zgodnie z [zasady Microsoft Store](/legal/windows/agreements/store-policies). Aby uzyskać więcej informacji, zobacz [cykl życia aplikacji platformy uniwersalnej systemu Windows](/windows/uwp/launch-resume/app-lifecycle).

## <a name="syntax"></a>Składnia

```c
void abort( void );
```

## <a name="return-value"></a>Wartość zwracana

`abort`Formant nie powróci do procesu wywołującego. Domyślnie sprawdza obsługi sygnał przerwania i zgłasza `SIGABRT` Jeśli jest on ustawiony. Następnie `abort` przerywa proces bieżącego i zwraca kod zakończenia procesu nadrzędnego.

## <a name="remarks"></a>Uwagi

**Dotyczące firmy Microsoft**

Domyślnie po utworzeniu aplikacji z bibliotek środowiska uruchomieniowego debugowania `abort` procedury wyświetla komunikat o błędzie przed `SIGABRT` jest wywoływane. W przypadku aplikacji konsoli w trybie konsoli, komunikat jest wysyłany do `STDERR`. Windows aplikacji klasycznych i aplikacji konsoli działających w trybie okna wyświetlania komunikatu w oknie komunikatu. Aby Pomiń komunikat, należy użyć [_set_abort_behavior —](../../c-runtime-library/reference/set-abort-behavior.md) wyczyść `_WRITE_ABORT_MSG` flagi. Komunikat wyświetlany jest zależna od wersji środowiska uruchomieniowego używane. Komunikat podobny dla aplikacji tworzonych przy użyciu najnowszej wersji programu Visual C++, to:

> R6010 - abort() została wywołana

Ten komunikat został wyświetlony w poprzednich wersji biblioteki środowiska uruchomieniowego C:

> Ta aplikacja zażądała zakończenia działania w nietypowego środowiska uruchomieniowego. Aby uzyskać więcej informacji, skontaktuj się z zespołem pomocy technicznej aplikacji.

Gdy program jest kompilowany w trybie debugowania, w oknie komunikatu Wyświetla opcje do **przerwać**, **ponów**, lub **Ignoruj**. Jeśli użytkownik zdecyduje się **przerwać**, program zakończy się natychmiast i zwraca kod zakończenia 3. Jeśli użytkownik zdecyduje się **ponów**, debugera jest wywoływanym w celu debugowania just in time, jeśli jest dostępna. Jeśli użytkownik zdecyduje się **Ignoruj**, `abort` kontynuowanie normalnego przetwarzania.

W kompilacjach zarówno handlowych i debugowania `abort` sprawdza, czy program obsługi sygnał przerwania jest ustawiony. Jeśli ustawiono obsługi innych niż domyślne sygnałów, `abort` wywołania `raise(SIGABRT)`. Użyj [sygnału](../../c-runtime-library/reference/signal.md) funkcji, aby skojarzyć funkcji obsługi sygnał przerwania z `SIGABRT` sygnału. Niestandardowe akcje — na przykład wyczyścić zasoby lub rejestrowania informacji — i zakończyć aplikację z własnego kodu błędu w funkcji programu obsługi. Jeśli zdefiniowano bez obsługi niestandardowych sygnału, `abort` nie zgłaszał `SIGABRT` sygnału.

Domyślnie w kompilacjach bez debugowania aplikacji pulpitu lub konsoli `abort` następnie wywołuje mechanizmu usługi raportowania błędów systemu Windows (wcześniej znane jako odzyskiwania po awarii. Watson) do raportu błędów do firmy Microsoft. To zachowanie może być włączona lub wyłączona przez wywołanie metody `_set_abort_behavior` i ustawienie lub maskowania `_CALL_REPORTFAULT` flagi. Gdy flaga jest ustawiona, system Windows wyświetli okno komunikatu zawierający tekst coś, takich jak "Problem spowodowany program przestał działać poprawnie." Użytkownik może wywołać debugera z **debugowania** przycisk lub wybierz **Zamknij program** przycisk, aby zakończyć aplikację z kodu błędu, który jest zdefiniowany przez system operacyjny.

Jeśli program obsługi raportowania błędów systemu Windows nie jest wywoływany, następnie `abort` wywołania [_exit —](../../c-runtime-library/reference/exit-exit-exit.md) zakończenie procesu z zakończenia kontroli 3 i zwraca kodu do procesu nadrzędnego lub systemu operacyjnego. `_exit`Opróżnienia buforów strumienia lub do `atexit` / `_onexit` przetwarzania.

Aby uzyskać więcej informacji na temat debugowania CRT, zobacz [techniki testowania CRT](/visualstudio/debugger/crt-debugging-techniques).

**Końcowy określonych firmy Microsoft**

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|`abort`|\<process.h > lub \<stdlib.h >|

## <a name="example"></a>Przykład

Następujący program podejmuje próbę otwarcia pliku i przerywa, jeśli próba nie powiedzie się.

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

[Użycie funkcji abort](../../cpp/using-abort.md)  
[abort, funkcja](../../c-language/abort-function-c.md)  
[Procedury kontroli środowiska](../../c-runtime-library/process-and-environment-control.md)  
[_exec, _wexec, funkcje](../../c-runtime-library/exec-wexec-functions.md)  
[exit, _Exit, _exit](../../c-runtime-library/reference/exit-exit-exit.md)  
[raise](../../c-runtime-library/reference/raise.md)  
[signal](../../c-runtime-library/reference/signal.md)  
[_spawn, _wspawn, funkcje](../../c-runtime-library/spawn-wspawn-functions.md)  
[_DEBUG](../../c-runtime-library/debug.md)  
[_set_abort_behavior](../../c-runtime-library/reference/set-abort-behavior.md)  
