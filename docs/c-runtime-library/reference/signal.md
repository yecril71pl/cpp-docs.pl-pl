---
title: "sygnał | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: signal
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
f1_keywords: signal
dev_langs: C++
helpviewer_keywords: signal function
ms.assetid: 094118de-d789-4063-b4f4-cffcc80bf29d
caps.latest.revision: "26"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 125512ba670c438ff7694b05fa73822273aba664
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="signal"></a>sygnał
Ustawia przerwań Obsługa sygnału.  
  
> [!IMPORTANT]
>  Nie używaj tej metody można zamknąć [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplikacji, z wyjątkiem testowania i debugowania scenariuszy. Programowe lub interfejsu użytkownika sposób, aby zamknąć [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplikacji nie są dozwolone zgodnie z sekcji 3,6 z [wymagania dotyczące certyfikacji aplikacji systemu Windows 8](http://go.microsoft.com/fwlink/?LinkId=262889). Aby uzyskać więcej informacji, zobacz [cyklem życia aplikacji (aplikacje ze Sklepu Windows)](http://go.microsoft.com/fwlink/?LinkId=262853).  
  
## <a name="syntax"></a>Składnia  
  
```  
void (__cdecl *signal(  
   int sig,   
   void (__cdecl *func ) (int [, int ] )))   
   (int);  
```  
  
#### <a name="parameters"></a>Parametry  
 `sig`  
 Wartość sygnału.  
  
 `func`  
 Funkcja do wykonania. Pierwszy parametr jest wartością sygnału, a drugi parametr jest podrzędnego kod, który może być używana podczas sigfpe — jest pierwszym parametrem.  
  
## <a name="return-value"></a>Wartość zwracana  
 `signal`Zwraca poprzednią wartość `func` który skojarzone z danym sygnału. Na przykład jeśli poprzednią wartość `func` został `SIG_IGN`, wartość zwracana jest również `SIG_IGN`. Zwracana wartość `SIG_ERR` wskazuje błąd; w takim przypadku `errno` ma ustawioną wartość `EINVAL`.  
  
 Zobacz [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Aby uzyskać więcej informacji na temat kodów powrotnych.  
  
## <a name="remarks"></a>Uwagi  
 `signal` Funkcja umożliwia procesu można wybrać jeden z kilku sposobów obsługi sygnał przerwania z systemu operacyjnego. `sig` Przerwań, do którego jest argument `signal` odpowiada; musi być jedną z następujących stałych manifestu, które są zdefiniowane w sygnału. H.  
  
|`sig`wartość|Opis|  
|-----------------|-----------------|  
|`SIGABRT`|Przerwania pracy|  
|`SIGFPE`|Błąd liczb zmiennoprzecinkowych|  
|`SIGILL`|Niedozwolona instrukcja|  
|`SIGINT`|Sygnał CTRL + C|  
|`SIGSEGV`|Dostępu do magazynu niedozwolony|  
|`SIGTERM`|Zakończenie żądania|  
  
 Jeśli `sig` nie jest jednym z powyższych wartości zostanie wywołany program obsługi nieprawidłowych parametrów, zgodnie z definicją w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md) . Jeśli wykonanie może kontynuować, ta funkcja ustawia `errno` do `EINVAL` i zwraca `SIG_ERR`.  
  
 Domyślnie `signal` kończy program wywołujący z kodem zakończenia 3, niezależnie od wartości `sig`.  
  
> [!NOTE]
>  `SIGINT`nie jest obsługiwane dla żadnej aplikacji Win32. W przypadku przerwania klawisze CTRL + C systemów operacyjnych Win32 Generowanie nowego wątku, w szczególności obsługi tego przerwania. Może to spowodować aplikacji jednym wątku, na przykład jeden w systemie UNIX wielowątkowe i spowodować nieoczekiwane zachowanie.  
  
 `func` Argument jest adresem do obsługi sygnał, który można zapisać lub do jednego ze wstępnie zdefiniowanych stałych `SIG_DFL` lub `SIG_IGN`, które także są definiowane w sygnału. H. Jeśli `func` jest funkcją, jest zainstalowana jako program obsługi sygnału dla danego sygnału. Prototyp obsługi sygnałów wymaga jednego argumentu formalne, `sig`, typu `int`. System operacyjny udostępnia rzeczywisty argument za pośrednictwem `sig` po wystąpieniu przerwania; argument jest sygnał, który wygenerował przerwania. W związku z tym służy sześć stałe manifestu (wymienione w powyższej tabeli) programu obsługi sygnału ustalenie, które przerwań wystąpił i podejmij odpowiednią akcję. Na przykład można wywołać `signal` dwa razy, aby przypisać tej procedury obsługi do dwóch różnych sygnałów, a następnie sprawdź `sig` argument w obsłudze wykonać różne operacje oparte na Odebrano sygnał.  
  
 Jeśli testujesz wyjątki zmiennoprzecinkowe (`SIGFPE`), `func` wskazuje funkcję, która przyjmuje opcjonalny drugi argument, który jest jednym z kilku stałe manifestu — zdefiniowane w FLOAT. H — w postaci `FPE_xxx`. Gdy `SIGFPE` występuje sygnału, można sprawdzić wartość drugiego argumentu, aby określić rodzajem zmiennoprzecinkowych wyjątków, a następnie podjąć odpowiednie działania. Tego argumentu i jego możliwych wartości są rozszerzenia Microsoft.  
  
 Wyjątki zmiennoprzecinkowe, wartość `func` nie zostanie zresetowana, po odebraniu sygnału. Aby odzyskać wyjątki zmiennoprzecinkowe, używać instrukcji try / except klauzule otaczające wartość zmiennoprzecinkowa punkt operacji. Istnieje również możliwość odzyskiwania przy użyciu [setjmp](../../c-runtime-library/reference/setjmp.md) z [longjmp](../../c-runtime-library/reference/longjmp.md). W obu przypadkach proces wywoływania wznawia wykonywanie i wyjdzie ze stanu zmiennoprzecinkowe procesu niezdefiniowana.  
  
 Jeśli zwróci obsługi sygnałów, proces wywoływania wznawia bezpośrednio po punktu, jaką otrzymał sygnał przerwania wykonywania. Dotyczy to niezależnie od rodzaju sygnał lub tryb działania.  
  
 Przed wykonaniem określona funkcja wartość `func` ma ustawioną wartość `SIG_DFL`. Dalej sygnał przerwania jest traktowany jak `SIG_DFL`, chyba że aktywne wywołanie `signal` Określa, w przeciwnym razie wartość. Ta funkcja służy do resetowania sygnałów w wywoływana funkcja.  
  
 Ponieważ procedury obsługi sygnałów są zwykle nazywane asynchronicznie, gdy wystąpi przerwania, funkcji obsługi sygnałów może zostać kontroli, gdy operacja czasu wykonywania jest niekompletne i w nieznanym stanie. Poniższa lista zawiera podsumowanie ograniczeń, które określają, jakie funkcje, korzystając z procedury obsługi sygnału.  
  
-   Wykonaj niskiego poziomu problem lub stdio —. Procedury we/wy H (na przykład `printf` lub `fread`).  
  
-   Nie należy wywoływać procedury sterty lub dowolnej procedury używającej procedury sterty (na przykład `malloc`, `_strdup`, lub `_putenv`). Zobacz [— funkcja malloc](../../c-runtime-library/reference/malloc.md) Aby uzyskać więcej informacji.  
  
-   Nie należy używać dowolnej funkcji, które generuje wywołanie systemowe (na przykład `_getcwd` lub `time`).  
  
-   Nie używaj `longjmp` , chyba że przerwania jest spowodowany przez zmiennoprzecinkowych wyjątków (to znaczy `sig` jest `SIGFPE`). W tym przypadku najpierw ponownie zainicjować zmiennoprzecinkowe pakietu przy użyciu wywołania `_fpreset`.  
  
-   Nie należy używać dowolnej procedury nakładki.  
  
 Program musi zawierać kod liczb zmiennoprzecinkowych, jeśli jest pułapki `SIGFPE` wyjątek przy użyciu funkcji. Jeśli program nie ma kodu liczb zmiennoprzecinkowych, wymaga biblioteki wykonawczej sygnału obsługi kodu zadeklarować volatile wartość o podwójnej precyzji i zainicjować go od zera:  
  
`volatile double d = 0.0f;`  
  
 `SIGILL` i `SIGTERM` sygnały nie są generowane w systemie Windows. Są one uwzględniane dla zgodność ANSI. W związku z tym należy określić przy użyciu obsługi sygnału te sygnały `signal`, i może również jawnie generować te sygnały wywołując [podnieść](../../c-runtime-library/reference/raise.md).  
  
 Sygnał ustawienia nie są zachowywane w uruchomionego procesu, które zostały utworzone przy użyciu wywołania `_exec` lub `_spawn` funkcji. Ustawienia sygnału są resetowane do wartości domyślnych w nowym procesie.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`signal`|\<Signal.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `signal` dodanie niektóre niestandardowe zachowania do `SIGABRT` sygnału. Aby uzyskać dodatkowe informacje na temat zachowania przerwania, zobacz [_set_abort_behavior —](../../c-runtime-library/reference/set-abort-behavior.md).  
  
```cpp  
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
  
## <a name="see-also"></a>Zobacz też  
 [Proces i kontroli środowiska](../../c-runtime-library/process-and-environment-control.md)   
 [przerwania](../../c-runtime-library/reference/abort.md)   
 [_execwexec — funkcje](../../c-runtime-library/exec-wexec-functions.md)   
 [exit, _exit — _exit —](../../c-runtime-library/reference/exit-exit-exit.md)   
 [_fpreset —](../../c-runtime-library/reference/fpreset.md)   
 [_spawn, _wspawn — funkcje](../../c-runtime-library/spawn-wspawn-functions.md)