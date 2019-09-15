---
title: _configthreadlocale
ms.date: 11/04/2016
api_name:
- _configthreadlocale
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
- api-ms-win-crt-locale-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _configthreadlocale
- configthreadlocale
helpviewer_keywords:
- configthreadlocale function
- locales, per-thread
- _configthreadlocale function
- per-thread locale
- thread locale
ms.assetid: 10e4050e-b587-4f30-80bc-6c76b35fc770
ms.openlocfilehash: aac0d36654a81e5d616ffff28e5a254fe06628a3
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939021"
---
# <a name="_configthreadlocale"></a>_configthreadlocale

Konfiguruje Opcje regionalne dla poszczególnych wątków.

## <a name="syntax"></a>Składnia

```C
int _configthreadlocale( int per_thread_locale_type );
```

### <a name="parameters"></a>Parametry

*per_thread_locale_type*<br/>
Opcja ustawiona. Jedna z opcji wymienionych w poniższej tabeli.

## <a name="return-value"></a>Wartość zwracana

Poprzednie Stany ustawień regionalnych poszczególnych wątków ( **_DISABLE_PER_THREAD_LOCALE** lub **_ENABLE_PER_THREAD_LOCALE**) lub-1 w przypadku niepowodzenia.

## <a name="remarks"></a>Uwagi

Funkcja **_configurethreadlocale** służy do kontrolowania użycia ustawień regionalnych specyficznych dla wątku. Użyj jednej z następujących opcji *per_thread_locale_type* , aby określić lub określić stan ustawień regionalnych dla wątku:

| Opcja | Opis |
|-|-|
| **_ENABLE_PER_THREAD_LOCALE** | Zmień bieżący wątek na Użyj ustawień regionalnych specyficznych dla wątku. Kolejne wywołania metody **setlocals** w tym wątku mają wpływ tylko na własne ustawienia regionalne wątku. |
| **_DISABLE_PER_THREAD_LOCALE** | Zmień globalne ustawienia regionalne bieżącego wątku. Kolejne wywołania w tym wątku mają **wpływ na inne** wątki korzystające z globalnych ustawień regionalnych. |
| **0** | Pobiera bieżące ustawienie dla tego określonego wątku. |

Te funkcje mają wpływ na zachowanie funkcji **setlocals**, **_tsetlocale**, **_wsetlocale**i **_setmbcp**. Gdy ustawienia regionalne dla wątku są wyłączone, każde kolejne wywołanie metody **setlocale** lub **_wsetlocale** zmienia ustawienia regionalne wszystkich wątków, które używają globalnych ustawień regionalnych. Gdy włączone są ustawienia regionalne dla wątku, funkcja **setlocale** lub **_wsetlocale** ma wpływ tylko na ustawienia regionalne bieżącego wątku.

Jeśli używasz **_configurethreadlocale** , aby włączyć ustawienia regionalne dla wątku, zalecamy wywołanie metody **setlocale** lub **_wsetlocale** w celu natychmiastowego ustawienia ustawień regionalnych w tym wątku.

Jeśli *per_thread_locale_type* nie jest jedną z wartości wymienionych w tabeli, ta funkcja wywołuje procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, ta funkcja ustawia **errno** na **EINVAL** i zwraca wartość-1.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_configthreadlocale**|\<locale.h>|

## <a name="example"></a>Przykład

```cpp
// crt_configthreadlocale.cpp
//
// This program demonstrates the use of _configthreadlocale when
// using two independent threads.
//
// Compile by using: cl /EHsc /W4 crt_configthreadlocale.cpp

#include <locale.h>
#include <mbctype.h>
#include <process.h>
#include <windows.h>
#include <stdio.h>
#include <time.h>

#define BUFF_SIZE 100

// Retrieve the date and time in the current
// locale's format.
int get_time(unsigned char* str)
{
    __time64_t  ltime;
    struct tm   thetime;

    // Retieve the time
    _time64(&ltime);
    _gmtime64_s(&thetime, &ltime);

    // Format the current time structure into a string
    // using %#x is the long date representation,
    // appropriate to the current locale
    if (!strftime((char *)str, BUFF_SIZE, "%#x",
                  (const struct tm*)&thetime))
    {
        printf("strftime failed!\n");
        return -1;
    }
    return 0;
}

// This thread sets its locale to German
// and prints the time.
unsigned __stdcall SecondThreadFunc( void* /*pArguments*/ )
{
    unsigned char str[BUFF_SIZE];

    _configthreadlocale(_ENABLE_PER_THREAD_LOCALE);

    // Set the thread code page
    _setmbcp(_MB_CP_ANSI);

    // Set the thread locale
    printf("The thread locale is now set to %s.\n",
           setlocale(LC_ALL, "German"));

    // Retrieve the time string from the helper function
    if (get_time(str) == 0)
    {
        printf("The time in German locale is: '%s'\n", str);
    }

    _endthreadex( 0 );
    return 0;
}

// The main thread spawns a second thread (above) and then
// sets the locale to English and prints the time.
int main()
{
    HANDLE          hThread;
    unsigned        threadID;
    unsigned char   str[BUFF_SIZE];

    // Enable per-thread locale causes all subsequent locale
    // setting changes in this thread to only affect this thread.
    _configthreadlocale(_ENABLE_PER_THREAD_LOCALE);

    // Retrieve the time string from the helper function
    printf("The thread locale is now set to %s.\n",
           setlocale(LC_ALL, "English"));

    // Create the second thread.
    hThread = (HANDLE)_beginthreadex( NULL, 0, &SecondThreadFunc,
                                      NULL, 0, &threadID );

    if (get_time(str) == 0)
    {
        // Retrieve the time string from the helper function
        printf("The time in English locale is: '%s'\n\n", str);
    }

    // Wait for the created thread to finish.
    WaitForSingleObject( hThread, INFINITE );

    // Destroy the thread object.
    CloseHandle( hThread );
}
```

```Output
The thread locale is now set to English_United States.1252.
The time in English locale is: 'Wednesday, May 12, 2004'

The thread locale is now set to German_Germany.1252.
The time in German locale is: 'Mittwoch, 12. Mai 2004'
```

## <a name="see-also"></a>Zobacz także

[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[_beginthread, _beginthreadex](beginthread-beginthreadex.md)<br/>
[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[Wielowątkowość i ustawienia regionalne](../../parallel/multithreading-and-locales.md)<br/>
