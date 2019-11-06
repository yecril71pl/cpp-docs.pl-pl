---
title: sygnał
ms.date: 04/12/2018
api_name:
- signal
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- signal
helpviewer_keywords:
- signal function
ms.openlocfilehash: 232bf7bc518907db8744fbb85e0f3a33c9296006
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2019
ms.locfileid: "73625852"
---
# <a name="signal"></a>sygnał

Ustawia obsługę sygnałów przerwań.

> [!IMPORTANT]
> Nie należy używać tej metody do zamykania aplikacji Microsoft Store, z wyjątkiem scenariuszy testowania lub debugowania. Sposób programistyczny lub interfejs użytkownika służący do zamykania aplikacji ze sklepu nie są dozwolone zgodnie z [zasadami Microsoft Storeymi](/legal/windows/agreements/store-policies). Aby uzyskać więcej informacji, zobacz [cykl życia aplikacji platformy UWP](/windows/uwp/launch-resume/app-lifecycle).

## <a name="syntax"></a>Składnia

```C
void __cdecl *signal(int sig, int (*func)(int, int));
```

### <a name="parameters"></a>Parametry

*SIG*<br/>
Wartość sygnału.

*func*<br/>
Drugi parametr jest wskaźnikiem do funkcji, która ma zostać wykonana. Pierwszy parametr jest wartością sygnału, a drugi parametr jest kodem podrzędnym, który może być używany, gdy pierwszy parametr to SIGFPE.

## <a name="return-value"></a>Wartość zwracana

**sygnał** zwraca poprzednią wartość funkcji Func, która jest skojarzona z danym sygnałem. Na przykład jeśli Poprzednia wartość *Func* została **SIG_IGN**, zwracana wartość jest również **SIG_IGN**. Wartość zwracana przez **SIG_ERR** wskazuje na błąd; w takim przypadku **errno** jest ustawiony na **EINVAL**.

Aby uzyskać więcej informacji na temat kodów powrotnych, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) .

## <a name="remarks"></a>Uwagi

Funkcja **sygnałów** umożliwia procesowi wybranie jednego z kilku sposobów obsługi sygnału przerwania z systemu operacyjnego. Argument *SIG* to przerwa, do którego reaguje **sygnał** ; musi to być jeden z następujących stałych manifestu, które są zdefiniowane w SYGNALe. C.

|wartość *SIG*|Opis|
|-----------------|-----------------|
|**SIGABRT**|Nietypowe zakończenie|
|**SIGFPE**|Błąd zmiennoprzecinkowy|
|**SIGILL**|Niedozwolona instrukcja|
|**SIGINT**|CTRL + sygnał C|
|**SIGSEGV**|Niedozwolony dostęp do magazynu|
|**SIGTERM**|Żądanie zakończenia|

Jeśli *SIG* nie jest jedną z powyższych wartości, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z definicją w [walidacji parametru](../../c-runtime-library/parameter-validation.md) . Jeśli wykonanie może być kontynuowane, ta funkcja ustawia **errno** na **EINVAL** i zwraca **SIG_ERR**.

Domyślnie **sygnał** kończy program wywołujący z kodem zakończenia 3, niezależnie od wartości *SIG*.

> [!NOTE]
> **SIGINT** nie jest obsługiwana dla żadnej aplikacji Win32. Gdy wystąpi przerwa CTRL + C, systemy operacyjne Win32 generują nowy wątek do obsługi tego przerwania. Może to spowodować, że aplikacja jednowątkowa, taka jak jedna w systemie UNIX, będzie pełnić funkcję wielowątkowości i spowodować nieoczekiwane zachowanie.

Argument *Func* jest adresem do programu obsługi sygnałów, który można napisać lub do jednej ze wstępnie zdefiniowanych stałych **SIG_DFL** lub **SIG_IGN**, które są również zdefiniowane w sygnale. C. Jeśli *Func* jest funkcją, jest ona instalowana jako program obsługi sygnałów dla danego sygnału. Prototyp programu obsługi sygnałów wymaga jednego formalnego argumentu, *SIG*, typu **int**. System operacyjny udostępnia rzeczywisty argument za pomocą *SIG* w przypadku wystąpienia przerwania; argument jest sygnałem, który wygenerował przerwanie. W związku z tym można użyć sześciu stałych manifestu (wymienionych w powyższej tabeli) w programie obsługi sygnałów, aby określić, które przerwanie wystąpiło i podjąć odpowiednie działania. Na przykład można wywołać **sygnał** dwa razy, aby przypisać tę samą procedurę obsługi do dwóch różnych sygnałów, a następnie przetestować argument *SIG* w programie obsługi, aby wykonać różne akcje na podstawie otrzymanego sygnału.

Jeśli testujesz wyjątki zmiennoprzecinkowe (**SIGFPE**), *Func* wskazuje funkcję, która przyjmuje opcjonalny drugi argument, który jest jednym z kilku stałych manifestu, zdefiniowanych w float. H formularza **FPE_xxx**. Gdy wystąpi sygnał **SIGFPE** , można przetestować wartość drugiego argumentu, aby określić rodzaj wyjątku zmiennoprzecinkowego, a następnie podjąć odpowiednie działania. Ten argument i jego możliwe wartości to rozszerzenia Microsoft.

Dla wyjątków zmiennoprzecinkowych wartość *Func* nie jest resetowana po odebraniu sygnału. Aby wykonać odzyskiwanie z wyjątków zmiennoprzecinkowych, należy użyć klauzul try/except do obsłużenia operacji zmiennoprzecinkowych. Możliwe jest również odzyskanie za pomocą [setjmp](setjmp.md) z [longjmp](longjmp.md). W obu przypadkach proces wywołujący wznawia wykonywanie i pozostawia stan zmiennoprzecinkowy niezdefiniowanego procesu.

Jeśli program obsługi sygnałów zwraca, proces wywołujący wznawia wykonywanie natychmiast po punkcie, w którym otrzymał sygnał przerwania. Ta wartość jest prawdziwa niezależnie od rodzaju sygnału lub trybu operacyjnego.

Przed wykonaniem określonej funkcji wartość *Func* jest ustawiana na **SIG_DFL**. Następny sygnał przerwania jest traktowany jak opisano dla **SIG_DFL**, chyba że wywołanie wywołujące do **sygnału** określa inaczej. Tej funkcji można użyć do resetowania sygnałów w wywołanej funkcji.

Ponieważ procedury obsługi sygnałów są zwykle wywoływane asynchronicznie w przypadku wystąpienia przerwania, funkcja obsługi sygnałów może uzyskać kontrolę, gdy operacja czasu wykonywania jest niekompletna i w nieznanym stanie. Poniższa lista zawiera podsumowanie ograniczeń, które określają funkcje, których można użyć w procedurze obsługi sygnałów.

- Nie należy wydawać niskiego poziomu ani STDIO. H procedury we/wy (na przykład **printf** lub **fread**).

- Nie wywołuj procedur sterty ani żadnej procedury korzystającej z procedur sterty (na przykład **malloc**, **_strdup**lub **_putenv**). Aby uzyskać więcej informacji, zobacz [malloc](malloc.md) .

- Nie należy używać żadnej funkcji generującej wywołanie systemowe (na przykład **_getcwd** lub **Time**).

- Nie należy używać **longjmp** , chyba że przerwanie jest spowodowane przez wyjątek zmiennoprzecinkowy (czyli *SIG* to **SIGFPE**). W takim przypadku należy najpierw ponownie zainicjować pakiet zmiennoprzecinkowy przy użyciu wywołania do **_fpreset**.

- Nie należy używać żadnych procedur nakładki.

Program musi zawierać kod zmiennoprzecinkowy, jeśli jest to pułapka wyjątku **SIGFPE** przy użyciu funkcji. Jeśli program nie ma kodu zmiennoprzecinkowego i wymaga kodu obsługi sygnałów biblioteki wykonawczej, po prostu Zadeklaruj nietrwałą wartość podwójną i zainicjuj ją jako zero:

```C
volatile double d = 0.0f;
```

Sygnały **SIGILL** i **SIGTERM** nie są generowane w systemie Windows. Są one dołączone do zgodności ANSI. W związku z tym, można ustawić programy obsługi sygnałów dla tych sygnałów przy użyciu **sygnału**i można również jawnie wygenerować te sygnały przez wywołanie metody [podnieść](raise.md).

Ustawienia sygnałów nie są zachowywane w procesach duplikowanych, które są tworzone przez wywołania funkcji [_exec](../../c-runtime-library/exec-wexec-functions.md) lub [_spawn](../../c-runtime-library/spawn-wspawn-functions.md) . Ustawienia sygnału są resetowane do wartości domyślnych w nowym procesie.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**signal**|\<sygnał. h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak za pomocą **sygnału** dodać niestandardowe zachowanie do sygnału **SIGABRT** . Aby uzyskać dodatkowe informacje na temat zachowania przerwania, zobacz [_set_abort_behavior](set-abort-behavior.md).

```C
// crt_signal.c
// compile with: /EHsc /W4
// Use signal to attach a signal handler to the abort routine
#include <stdlib.h>
#include <signal.h>

void SignalHandler(int signal)
{
    if (signal == SIGABRT) {
        // abort signal handler code
    } else {
        // ...
    }
}

int main()
{
    typedef void (*SignalHandlerPointer)(int);

    SignalHandlerPointer previousHandler;
    previousHandler = signal(SIGABRT, SignalHandler);

    abort();
}
```

Dane wyjściowe są zależne od używanej wersji środowiska uruchomieniowego, bez względu na to, czy aplikacja jest konsolą lub aplikacją systemu Windows, czy w ustawieniach rejestru systemu Windows. W przypadku aplikacji konsolowej można wysłać do stderr następujący komunikat podobny do następującego:

```Output
Debug Error!

Program: c:\Projects\crt_signal\Debug\crt_signal.exe

R6010

- abort() has been called
```

## <a name="see-also"></a>Zobacz także

[Procedury kontroli środowiska](../../c-runtime-library/process-and-environment-control.md)<br/>
[abort](abort.md)<br/>
[_exec, _wexec, funkcje](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_fpreset](fpreset.md)<br/>
[_spawn, _wspawn, funkcje](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
