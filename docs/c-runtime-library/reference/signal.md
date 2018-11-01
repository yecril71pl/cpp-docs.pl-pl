---
title: sygnał
ms.date: 04/12/2018
apiname:
- signal
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
- signal
helpviewer_keywords:
- signal function
ms.openlocfilehash: 1a0f9f8448149ce18155e0f5b88343c56d9b3d7c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50660710"
---
# <a name="signal"></a>sygnał

Ustawia przerwanie obsługi sygnałów.

> [!IMPORTANT]
> Nie należy używać tej metody do zamykania aplikacji Microsoft Store, z wyjątkiem testowania i debugowania scenariuszy. Sposoby Programmatic lub interfejs użytkownika, zamknąć Store app nie są dozwolone zgodnie z opisem w [zasady Microsoft Store](/legal/windows/agreements/store-policies). Aby uzyskać więcej informacji, zobacz [cykl życia aplikacji platformy uniwersalnej systemu Windows](/windows/uwp/launch-resume/app-lifecycle).

## <a name="syntax"></a>Składnia

```C
void __cdecl *signal(int sig, int (*func)(int, int));
```

### <a name="parameters"></a>Parametry

*SIG*<br/>
Wartość sygnału.

*FUNC*<br/>
Drugi parametr jest wskaźnikiem do funkcji, które mają zostać wykonane. Pierwszy parametr jest wartością sygnału, a drugi parametr jest podkodem, który można użyć, gdy pierwszym parametrem jest SIGFPE.

## <a name="return-value"></a>Wartość zwracana

**sygnał** zwraca poprzednią wartość func, która jest skojarzona z danego sygnału. Na przykład jeśli poprzednią wartością *func* został **SIG_IGN**, zwracana wartość jest również **SIG_IGN**. Zwracana wartość wynosząca **SIG_ERR** wskazuje błąd; w takim przypadku **errno** ustawiono **EINVAL**.

Zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Aby uzyskać więcej informacji na temat kodów powrotnych.

## <a name="remarks"></a>Uwagi

**Sygnału** funkcja pozwala procesowi wybrać jeden z kilku sposobów, aby obsłużyć sygnał przerwania od systemu operacyjnego. *Sig* argument jest przerwań, do którego **sygnału** odpowiedział; musi być jednym z następujących stałych manifestu, które są zdefiniowane w sygnału. H.

|*SIG* wartość|Opis|
|-----------------|-----------------|
|**SIGABRT**|Nienormalne zakończenie|
|**SIGFPE**|Błąd wartości zmiennoprzecinkowej|
|**SIGILL**|Niedozwolona instrukcja|
|**SIGINT**|CTRL + C sygnalizuje|
|**SIGSEGV**|Niedozwolony dostęp do magazynu|
|**SIGTERM**|Zakończenie żądania|

Jeśli *sig* nie jest jednym z powyższych wartości, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z definicją w [Parameter Validation](../../c-runtime-library/parameter-validation.md) . Jeśli wykonanie może być kontynuowane, funkcja ta ustawia **errno** do **EINVAL** i zwraca **SIG_ERR**.

Domyślnie **sygnału** kończy program wywołujący z kodem zakończenia 3, niezależnie od wartości *sig*.

> [!NOTE]
> **SIGINT** nie jest obsługiwana dla żadnej aplikacji systemu Win32. Po wystąpieniu przerwania klawisze CTRL + C, system operacyjny Win32 generuje nowy wątek, aby specjalnie obsługiwać to przerwanie. Może to spowodować aplikacją pojedynczego wątku, na przykład jednego w systemie UNIX, aby stać się wielowątkowe i spowodować nieoczekiwane zachowanie.

*Func* argument jest adresem do obsługi sygnałów, które piszesz lub do jednego z wstępnie zdefiniowanych stałych **SIG_DFL** lub **SIG_IGN**, które są również określone w sygnału. H. Jeśli *func* jest funkcją, jest on instalowany jako procedura obsługi sygnału dla danego sygnału. Prototyp obsługi sygnałów wymaga jednego argumentu formalnego, *sig*, typu **int**. System operacyjny udostępnia rzeczywisty argument poprzez *sig* po wystąpieniu przerwania; argument jest sygnałem, który wygenerował przerwanie. W związku z tym możesz można użyć sześciu stałych manifestów (wymienionych w powyższej tabeli) w sieci obsługi sygnałów do określenia przerwania, które miały miejsce i podejmą odpowiednie działania. Na przykład, można wywołać **sygnału** dwa razy, aby przypisać tę samą procedurę obsługi dwóm różnym sygnałom, a następnie przetestować *sig* argument w procedurze obsługi Aby wykonać różne operacje oparciu o otrzymany sygnał.

Jeśli testujesz wyjątki zmiennoprzecinkowe (**SIGFPE**), *func* wskazuje funkcję, która przyjmuje opcjonalny drugi argument, który jest jednym z kilku stałych manifestu, określonych w FLOAT. Godz., w postaci **FPE_xxx**. Gdy **SIGFPE** sygnał występuje, można sprawdzić wartość drugiego argumentu, aby określić rodzaj wyjątku zmiennoprzecinkowego i wtedy podjąć odpowiednie działania. Ten argument i jego możliwe wartości są rozszerzeniami Microsoft.

Przypadku wyjątków zmiennoprzecinkowych, wartość *func* nie jest resetowana po odebraniu sygnału. Aby odzyskać wyjątki zmiennoprzecinkowe, użyj spróbuj /z wyjątkiem klauzul do otoczenia zmiennoprzecinkowego punkt operacji. Istnieje również możliwość odzyskać za pomocą [setjmp](setjmp.md) z [longjmp](longjmp.md). W obu przypadkach proces wywołujący wznawia wykonanie i pozostawia stan zapisu zmiennoprzecinkowego procesu niezdefiniowane.

Jeśli procedura obsługi sygnału powraca, proces wywołujący wznawia wykonanie następując bezpośrednio po punkcie, w którym otrzymał sygnał przerwania. Ta zasada obowiązuje niezależnie od rodzaju sygnału lub trybu pracy.

Przed wykonaniem określonej funkcji, wartość *func* ustawiono **SIG_DFL**. Kolejny sygnał przerwania jest traktowany jak opisano dla **SIG_DFL**, chyba że wywołanie interwencyjne **sygnału** określi inaczej. Ta funkcja służy do resetowania sygnałów w wywołanej funkcja.

Ponieważ procedury obsługi sygnału są zwykle wywoływane asynchronicznie po wystąpieniu przerwania, funkcję obsługi sygnałów może uzyskać kontrolę, kiedy operacja środowiska uruchomieniowego jest niekompletna i w nieznanym stanie. Na poniższej liście podsumowano ograniczenia, które określają funkcje, których można użyć w rutynowej obsłudze sygnałów, usługi.

- Do niskiego poziomu problem lub stdio —. Procedury we/wy H (na przykład **printf** lub **fread —**).

- Nie wywołuj sterty procedur lub dowolnej procedury korzystającej z procedury sterty (na przykład **— funkcja malloc**, **_strdup —**, lub **_putenv**). Zobacz [— funkcja malloc](malloc.md) Aby uzyskać więcej informacji.

- Nie używaj żadnej funkcji, która generuje wywołanie systemowego (na przykład **_getcwd —** lub **czasu**).

- Nie używaj **longjmp** , chyba że przerwanie jest spowodowane wyjątkiem zmiennoprzecinkowym (to znaczy *sig* jest **SIGFPE**). W tym przypadku najpierw inicjuje ponownie pakiet zmiennoprzecinkowy za pomocą wywołania **_fpreset —**.

- Nie używaj żadnych procedur nakładki.

Program musi zawierać kod zmiennoprzecinkowy, jeżeli ma wyłapać **SIGFPE** wyjątek przy użyciu funkcji. Jeśli program nie posiada kodu zmiennoprzecinkowego ale wymaga kodu obsługi sygnałów biblioteki wykonawczej, Zadeklaruj volatile wartość o podwójnej precyzji i zainicjuj ją na zero:

```C
volatile double d = 0.0f;
```

**SIGILL** i **SIGTERM** sygnały nie są generowane w obszarze Windows. Są one włączone dla zachowania zgodności z ANSI. W związku z tym, można ustawić programy obsługi sygnału dla tych sygnałów za pomocą **sygnału**, i można także jawnie generować te sygnały poprzez wywołanie [podnieść](raise.md).

Ustawienia sygnału nie są zachowywane w zduplikowanych procesach, które są tworzone przez wywołania [_exec](../../c-runtime-library/exec-wexec-functions.md) lub [_spawn](../../c-runtime-library/spawn-wspawn-functions.md) funkcji. Ustawienia sygnału są resetowane do wartości domyślnych w nowym procesie.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**signal**|\<signal.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak używać **sygnału** dodać niektóre zachowania niestandardowe do **SIGABRT** sygnału. Aby uzyskać dodatkowe informacje na temat zachowań przerywania, zobacz [_set_abort_behavior](set-abort-behavior.md).

```C
// crt_signal.c
// compile with: /EHsc /W4
// Use signal to attach a signal handler to the abort routine
#include <stdlib.h>
#include <signal.h>
#include <tchar.h>

void SignalHandler(int signal)
{
    if (signal == SIGABRT) {
        // abort signal handler code
    } else {
        // ...
    }
}

int main()
{
    typedef void (*SignalHandlerPointer)(int);

    SignalHandlerPointer previousHandler;
    previousHandler = signal(SIGABRT, SignalHandler);

    abort();
}
```

```Output
This application has requested the Runtime to terminate it in an unusual way.
Please contact the application's support team for more information.
```

## <a name="see-also"></a>Zobacz także

[Procedury kontroli środowiska](../../c-runtime-library/process-and-environment-control.md)<br/>
[abort](abort.md)<br/>
[_exec, _wexec, funkcje](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_fpreset](fpreset.md)<br/>
[_spawn, _wspawn, funkcje](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
