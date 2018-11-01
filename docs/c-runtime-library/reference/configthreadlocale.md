---
title: _configthreadlocale
ms.date: 11/04/2016
apiname:
- _configthreadlocale
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
- api-ms-win-crt-locale-l1-1-0.dll
apitype: DLLExport
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
ms.openlocfilehash: 244ef9ce93e39bef23a9d5d6792a10ca25355f5a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50648386"
---
# <a name="configthreadlocale"></a>_configthreadlocale

Konfiguruje opcje ustawień regionalnych na wątek.

## <a name="syntax"></a>Składnia

```C
int _configthreadlocale( int per_thread_locale_type );
```

### <a name="parameters"></a>Parametry

*per_thread_locale_type*<br/>
Możliwość ustawienia. Jedną z opcji wymienionych w poniższej tabeli.

## <a name="return-value"></a>Wartość zwracana

Poprzedni stan ustawień regionalnych na wątek (**_DISABLE_PER_THREAD_LOCALE** lub **_ENABLE_PER_THREAD_LOCALE**), lub wartość -1 w przypadku niepowodzenia.

## <a name="remarks"></a>Uwagi

**_Configurethreadlocale** funkcja służy do kontrolowania użycia ustawień regionalnych właściwych dla wątku. Użyj jednej z tych *per_thread_locale_type* sposoby określania lub ustalania stanu ustawień regionalnych na wątek:

|||
|-|-|
**_ENABLE_PER_THREAD_LOCALE**|Upewnij się użycie właściwych dla wątku ustawień regionalnych bieżącego wątku. Kolejne wywołania **setlocale** w tym wątku wpływają tylko ustawienia regionalne dla wątku.
**_DISABLE_PER_THREAD_LOCALE**|Należy bieżący wątek, użyj globalnych ustawień regionalnych. Kolejne wywołania **setlocale** w tym wątku wpływają na inne wątki przy użyciu globalnych ustawień regionalnych.
**0**|Pobiera bieżące ustawienie dla tego określonego wątku.

Te funkcje mają wpływ na zachowanie **setlocale**, **_tsetlocale —**, **_wsetlocale**, i **_setmbcp**. Gdy ustawienia regionalne na wątek jest wyłączone, wszelkie następne wywołania **setlocale** lub **_wsetlocale** zmieniają ustawienia regionalne wszystkich wątków, które używają globalnych ustawień regionalnych. Po włączeniu ustawień regionalnych na wątek **setlocale** lub **_wsetlocale** ma wpływ tylko na ustawienia regionalne bieżącego wątku.

Jeśli używasz **_configurethreadlocale** Aby włączyć ustawienia regionalne na wątek, firma Microsoft zaleca, należy wywołać **setlocale** lub **_wsetlocale** można ustawić preferowane ustawienia regionalne w tym wątku zaraz potem.

Jeśli *per_thread_locale_type* nie jest jedną z wartości wymienionych w tabeli, funkcja wywoła procedurę obsługi nieprawidłowego parametru, z zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, funkcja ta ustawia **errno** do **EINVAL** i zwraca wartość -1.

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
