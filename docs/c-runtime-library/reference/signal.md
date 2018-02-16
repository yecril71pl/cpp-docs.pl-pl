---
title: "sygnał | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/12/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- signal function
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 23eae404bf5f8e2227d68189938defb2308f5e6b
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="signal"></a>sygnał

Ustawia przerwań Obsługa sygnału.

> [!IMPORTANT]
> Nie należy używać tej metody można zamknąć aplikację Microsoft Store, z wyjątkiem w testowania i debugowania scenariuszy. Programowe lub interfejsu użytkownika sposobów Zamknij aplikację sklepu nie są dozwolone zgodnie z [zasady Microsoft Store](http://go.microsoft.com/fwlink/?LinkId=865936). Aby uzyskać więcej informacji, zobacz [cykl życia aplikacji platformy uniwersalnej systemu Windows](http://go.microsoft.com/fwlink/p/?LinkId=865934).

## <a name="syntax"></a>Składnia

```C
void __cdecl *signal(int sig, int (*func)(int, int));
```

### <a name="parameters"></a>Parametry
_sig_  
Wartość sygnału.

_func_  
Drugi parametr jest wskaźnikiem do funkcji, które mają zostać wykonane. Pierwszy parametr jest wartością sygnału, a drugi parametr jest podrzędnego kod, który może być używana podczas sigfpe — jest pierwszym parametrem.

## <a name="return-value"></a>Wartość zwracana

`signal` Zwraca poprzednią wartość func, który został skojarzony z danym sygnału. Na przykład jeśli poprzednią wartość _func_ został `SIG_IGN`, wartość zwracana jest również `SIG_IGN`. Zwracana wartość `SIG_ERR` wskazuje błąd; w takim przypadku `errno` ma ustawioną wartość `EINVAL`.

Zobacz [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Aby uzyskać więcej informacji na temat kodów powrotnych.

## <a name="remarks"></a>Uwagi

`signal` Funkcja umożliwia procesu można wybrać jeden z kilku sposobów obsługi sygnał przerwania z systemu operacyjnego. _Sig_ przerwań, do którego jest argument `signal` odpowiada; musi być jedną z następujących stałych manifestu, które są zdefiniowane w sygnału. H.

|_SIG_ wartość|Opis|
|-----------------|-----------------|
|`SIGABRT`|Przerwania pracy|
|`SIGFPE`|Błąd liczb zmiennoprzecinkowych|
|`SIGILL`|Niedozwolona instrukcja|
|`SIGINT`|Sygnał CTRL + C|
|`SIGSEGV`|Dostępu do magazynu niedozwolony|
|`SIGTERM`|Zakończenie żądania|

Jeśli _sig_ nie jest jednym z powyższych wartości zostanie wywołany program obsługi nieprawidłowych parametrów, zgodnie z definicją w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md) . Jeśli wykonanie może kontynuować, ta funkcja ustawia `errno` do `EINVAL` i zwraca `SIG_ERR`.

Domyślnie `signal` kończy program wywołujący z kodem zakończenia 3, niezależnie od wartości _sig_.

> [!NOTE]
> `SIGINT` nie jest obsługiwane dla żadnej aplikacji Win32. W przypadku przerwania klawisze CTRL + C systemów operacyjnych Win32 Generowanie nowego wątku, w szczególności obsługi tego przerwania. Może to spowodować aplikacji jednym wątku, na przykład jeden w systemie UNIX wielowątkowe i spowodować nieoczekiwane zachowanie.

_Func_ argument jest adresem do obsługi sygnał, który można zapisać lub do jednego ze wstępnie zdefiniowanych stałych `SIG_DFL` lub `SIG_IGN`, które także są definiowane w sygnału. H. Jeśli _func_ jest funkcją, jest zainstalowana jako program obsługi sygnału dla danego sygnału. Prototyp obsługi sygnałów wymaga jednego argumentu formalne, _sig_, typu `int`. System operacyjny udostępnia rzeczywisty argument za pośrednictwem _sig_ po wystąpieniu przerwania; argument jest sygnał, który wygenerował przerwania. W związku z tym służy sześć stałe manifestu (wymienione w powyższej tabeli) programu obsługi sygnału ustalenie, które przerwań wystąpił i podejmij odpowiednią akcję. Na przykład można wywołać `signal` dwa razy, aby przypisać tej procedury obsługi do dwóch różnych sygnałów, a następnie sprawdź _sig_ argument w obsłudze wykonać różne operacje oparte na Odebrano sygnał.

Jeśli testujesz wyjątki zmiennoprzecinkowe (`SIGFPE`), _func_ wskazuje funkcję, która przyjmuje opcjonalny drugi argument, który jest jednym z kilku stałe manifestu — zdefiniowane w FLOAT. H — w postaci `FPE_xxx`. Gdy `SIGFPE` występuje sygnału, można sprawdzić wartość drugiego argumentu, aby określić rodzajem zmiennoprzecinkowych wyjątków, a następnie podjąć odpowiednie działania. Tego argumentu i jego możliwych wartości są rozszerzenia Microsoft.

Wyjątki zmiennoprzecinkowe, wartość _func_ nie zostanie zresetowana, po odebraniu sygnału. Aby odzyskać wyjątki zmiennoprzecinkowe, używać instrukcji try / except klauzule otaczające wartość zmiennoprzecinkowa punkt operacji. Istnieje również możliwość odzyskiwania przy użyciu [setjmp](../../c-runtime-library/reference/setjmp.md) z [longjmp](../../c-runtime-library/reference/longjmp.md). W obu przypadkach proces wywoływania wznawia wykonywanie i wyjdzie ze stanu zmiennoprzecinkowe procesu niezdefiniowana.

Jeśli zwróci obsługi sygnałów, proces wywoływania wznawia bezpośrednio po punktu, jaką otrzymał sygnał przerwania wykonywania. Dotyczy to niezależnie od rodzaju sygnał lub tryb działania.

Przed wykonaniem określona funkcja wartość _func_ ma ustawioną wartość `SIG_DFL`. Dalej sygnał przerwania jest traktowany jak `SIG_DFL`, chyba że aktywne wywołanie `signal` Określa, w przeciwnym razie wartość. Ta funkcja służy do resetowania sygnałów w wywoływana funkcja.

Ponieważ procedury obsługi sygnałów są zwykle nazywane asynchronicznie, gdy wystąpi przerwania, funkcji obsługi sygnałów może zostać kontroli, gdy operacja czasu wykonywania jest niekompletne i w nieznanym stanie. Poniższa lista zawiera podsumowanie ograniczeń, które określają, jakie funkcje, korzystając z procedury obsługi sygnału.

- Wykonaj niskiego poziomu problem lub stdio —. Procedury we/wy H (na przykład `printf` lub `fread`).

- Nie należy wywoływać procedury sterty lub dowolnej procedury używającej procedury sterty (na przykład `malloc`, `_strdup`, lub `_putenv`). Zobacz [— funkcja malloc](../../c-runtime-library/reference/malloc.md) Aby uzyskać więcej informacji.

- Nie należy używać dowolnej funkcji, które generuje wywołanie systemowe (na przykład `_getcwd` lub `time`).

- Nie używaj `longjmp` , chyba że przerwania jest spowodowany przez zmiennoprzecinkowych wyjątków (to znaczy _sig_ jest `SIGFPE`). W tym przypadku najpierw ponownie zainicjować zmiennoprzecinkowe pakietu przy użyciu wywołania `_fpreset`.

- Nie należy używać dowolnej procedury nakładki.

Program musi zawierać kod liczb zmiennoprzecinkowych, jeśli jest pułapki `SIGFPE` wyjątek przy użyciu funkcji. Jeśli program nie ma kodu liczb zmiennoprzecinkowych, wymaga biblioteki wykonawczej sygnału obsługi kodu zadeklarować volatile wartość o podwójnej precyzji i zainicjować go od zera:

`volatile double d = 0.0f;`

`SIGILL` i `SIGTERM` sygnały nie są generowane w systemie Windows. Są one uwzględniane dla zgodność ANSI. W związku z tym należy określić przy użyciu obsługi sygnału te sygnały `signal`, i może również jawnie generować te sygnały wywołując [podnieść](../../c-runtime-library/reference/raise.md).

Sygnał ustawienia nie są zachowywane w uruchomionego procesu, które zostały utworzone przy użyciu wywołania `_exec` lub `_spawn` funkcji. Ustawienia sygnału są resetowane do wartości domyślnych w nowym procesie.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|`signal`|\<signal.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Poniższy przykład przedstawia użycie `signal` dodanie niektóre niestandardowe zachowania do `SIGABRT` sygnału. Aby uzyskać dodatkowe informacje na temat zachowania przerwania, zobacz [_set_abort_behavior —](../../c-runtime-library/reference/set-abort-behavior.md).

```C
// crt_signal.c
// compile with: /EHsc /W4
// Use signal to attach a signal handler to the abort routine
#include <stdlib.h>
#include <signal.h>
#include <tchar.h>

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

```Output
This application has requested the Runtime to terminate it in an unusual way.
Please contact the application's support team for more information.
```

## <a name="see-also"></a>Zobacz także

[Procedury kontroli środowiska](../../c-runtime-library/process-and-environment-control.md)  
[abort](../../c-runtime-library/reference/abort.md)  
[_exec, _wexec, funkcje](../../c-runtime-library/exec-wexec-functions.md)  
[exit, _Exit, _exit](../../c-runtime-library/reference/exit-exit-exit.md)  
[_fpreset](../../c-runtime-library/reference/fpreset.md)  
[_spawn, _wspawn, funkcje](../../c-runtime-library/spawn-wspawn-functions.md)  
