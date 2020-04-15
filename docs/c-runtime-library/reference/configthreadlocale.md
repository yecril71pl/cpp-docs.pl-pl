---
title: _configthreadlocale
ms.date: 4/2/2020
api_name:
- _configthreadlocale
- _o__configthreadlocale
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 46983843e128b59df89722c8d4694c30a858011f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348546"
---
# <a name="_configthreadlocale"></a>_configthreadlocale

Konfiguruje opcje ustawień regionalnych dla wątku.

## <a name="syntax"></a>Składnia

```C
int _configthreadlocale( int per_thread_locale_type );
```

### <a name="parameters"></a>Parametry

*per_thread_locale_type*<br/>
Opcja, aby ustawić. Jedna z opcji wymienionych w poniższej tabeli.

## <a name="return-value"></a>Wartość zwracana

Poprzedni stan ustawień regionalnych dla wątku **(_DISABLE_PER_THREAD_LOCALE** lub **_ENABLE_PER_THREAD_LOCALE)** lub -1 w przypadku awarii.

## <a name="remarks"></a>Uwagi

Funkcja **_configurethreadlocale** służy do kontrolowania użycia ustawień regionalnych specyficznych dla wątku. Użyj jednej z tych opcji *per_thread_locale_type,* aby określić lub określić stan ustawień regionalnych dla wątku:

| Opcja | Opis |
|-|-|
| **_ENABLE_PER_THREAD_LOCALE** | Upewnij się, że bieżący wątek użyj ustawień regionalnych specyficznych dla wątku. Kolejne wywołania **setlocale** w tym wątku mają wpływ tylko na własne ustawienia regionalne wątku. |
| **_DISABLE_PER_THREAD_LOCALE** | Upewnij się, że bieżący wątek użyj ustawień regionalnych globalnych. Kolejne wywołania **setlocale** w tym wątku wpływają na inne wątki przy użyciu ustawień regionalnych globalnego. |
| **0** | Pobiera bieżące ustawienie dla tego określonego wątku. |

Funkcje te wpływają na zachowanie **setlocale,** **_tsetlocale,** **_wsetlocale**i **_setmbcp**. Gdy ustawienia regionalne dla wątku jest wyłączona, wszelkie kolejne wywołanie **setlocale** lub **_wsetlocale** zmienia ustawienia regionalne wszystkich wątków, które używają ustawień regionalnych globalnego. Gdy ustawienia regionalne dla wątku jest włączona, **setlocale** lub **_wsetlocale** wpływa tylko na ustawienia regionalne bieżącego wątku.

Jeśli używasz **_configurethreadlocale,** aby włączyć ustawienia regionalne dla wątku, zaleca się wywołanie **setlocale** lub **_wsetlocale,** aby ustawić preferowane ustawienia regionalne w tym wątku natychmiast po.

Jeśli *per_thread_locale_type* nie jest jedną z wartości wymienionych w tabeli, ta funkcja wywołuje nieprawidłowy program obsługi parametrów, zgodnie z opisem w [weryfikacji parametrów](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie jest dozwolone, ta funkcja ustawia **errno** na **EINVAL** i zwraca -1.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_configthreadlocale**|\<>|

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

## <a name="see-also"></a>Zobacz też

[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[_beginthread, _beginthreadex](beginthread-beginthreadex.md)<br/>
[Ustawienia regionalne](../../c-runtime-library/locale.md)<br/>
[Wielowątkowe i ustawienia regionalne](../../parallel/multithreading-and-locales.md)<br/>
