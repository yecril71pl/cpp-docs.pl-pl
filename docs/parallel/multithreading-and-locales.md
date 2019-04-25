---
title: Wielowątkowość i ustawienia regionalne
ms.date: 11/04/2016
helpviewer_keywords:
- locales [C++], multithreading
- multithreading [C++], locales
- threading [C++], locales
- per-thread locale
ms.assetid: d6fb159a-eaca-4130-a51a-f95d62f71485
ms.openlocfilehash: c12a3fa1922db7a1ec0a7bcd43ddf09000d97961
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62213254"
---
# <a name="multithreading-and-locales"></a>Wielowątkowość i ustawienia regionalne

Biblioteka uruchomieniowa C i standardowej biblioteki języka C++ zapewnia obsługę zmiany ustawień regionalnych programu. W tym temacie omówiono problemy, które powstają, gdy za pomocą funkcji ustawień regionalnych, zarówno biblioteki aplikacji wielowątkowych.

## <a name="remarks"></a>Uwagi

Biblioteka uruchomieniowa C umożliwia tworzenie aplikacji wielowątkowych, za pomocą `_beginthread` i `_beginthreadex` funkcji. W tym temacie omówiono tylko aplikacje wielowątkowe utworzone za pomocą tych funkcji. Aby uzyskać więcej informacji, zobacz [_beginthread, _beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md).

Aby zmienić ustawienia regionalne, przy użyciu biblioteki środowiska uruchomieniowego języka C, należy użyć [setlocale](../preprocessor/setlocale.md) funkcji. W poprzednich wersjach programu Visual C++ ta funkcja zawsze będzie modyfikować ustawienia regionalne w całej aplikacji. Jest teraz obsługiwane ustawienia regionalne na zasadzie na wątek. Odbywa się przy użyciu [_configthreadlocale](../c-runtime-library/reference/configthreadlocale.md) funkcji. Aby określić, że [setlocale](../preprocessor/setlocale.md) tylko należy zmienić ustawienia regionalne w bieżącym wątku wywołania `_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)` w tym wątku. Z drugiej strony, wywołanie `_configthreadlocale(_DISABLE_PER_THREAD_LOCALE)` spowoduje, że wątek do użycia globalnych ustawień regionalnych, a każde wywołanie [setlocale](../preprocessor/setlocale.md) w tym wątku spowoduje zmianę ustawienia regionalne wszystkich wątków, które nie zostały jawnie włączone ustawienia regionalne dla wątku.

Aby zmienić ustawienia regionalne, przy użyciu biblioteki środowiska uruchomieniowego języka C++, użyj [locale — klasa](../standard-library/locale-class.md). Przez wywołanie metody [locale::global](../standard-library/locale-class.md#global) metody, możesz zmienić ustawienia regionalne w każdym wątku, który nie ma jawnie włączone ustawienia regionalne dla wątku. Aby zmienić ustawienia regionalne w jednym wątku lub jego części aplikacji, po prostu Utwórz wystąpienie obiektu `locale` obiektu w tym wątku lub jego części kodu.

> [!NOTE]
> Wywoływanie [locale::global](../standard-library/locale-class.md#global) zmieniają ustawienia regionalne dla standardowej biblioteki języka C++ i Biblioteka uruchomieniowa C. Jednak podczas wywoływania [setlocale](../preprocessor/setlocale.md) tylko zmieniają ustawienia regionalne dla biblioteki wykonawczej C; standardowej biblioteki języka C++ nie ma wpływu.

W poniższych przykładach pokazano sposób użycia [setlocale](../preprocessor/setlocale.md) funkcji [locale — klasa](../standard-library/locale-class.md)i [_configthreadlocale](../c-runtime-library/reference/configthreadlocale.md) funkcję, aby zmienić ustawienia regionalne aplikacji w kilku różnych scenariuszy.

## <a name="example"></a>Przykład

W tym przykładzie w wątku głównym, spowoduje utworzenie dwóch wątków podrzędnych. Pierwszy wątek, wątek A, umożliwia ustawień regionalnych na wątek wywołując `_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)`. Drugi wątek, wątek B, a także wątku głównym, nie należy włączać ustawienia regionalne dla wątku. Wątek, następnie przechodzi do zmiany, przy użyciu ustawień regionalnych [setlocale](../preprocessor/setlocale.md) funkcji biblioteki wykonawczej C.

Ponieważ wątek A ma na ustawienia regionalne wątku włączone, tylko funkcje biblioteki wykonawczej języka C w menu start wątku, A za pomocą ustawień regionalnych "Francuska". Funkcje biblioteki wykonawczej języka C w B wątku i wątku głównego w dalszym ciągu używają ustawień regionalnych "C". Ponadto ponieważ [setlocale](../preprocessor/setlocale.md) nie ma wpływu na ustawienia regionalne standardowej biblioteki języka C++, wszystkie biblioteki standardowej języka C++, które obiekty w dalszym ciągu używają ustawień regionalnych "C".

```cpp
// multithread_locale_1.cpp
// compile with: /EHsc /MD
#include <clocale>
#include <cstdio>
#include <locale>
#include <process.h>
#include <windows.h>

#define NUM_THREADS 2
using namespace std;

unsigned __stdcall RunThreadA(void *params);
unsigned __stdcall RunThreadB(void *params);

BOOL localeSet = FALSE;
HANDLE printMutex = CreateMutex(NULL, FALSE, NULL);

int main()
{
    HANDLE threads[NUM_THREADS];

    unsigned aID;
    threads[0] = (HANDLE)_beginthreadex(
        NULL, 0, RunThreadA, NULL, 0, &aID);

    unsigned bID;
    threads[1] = (HANDLE)_beginthreadex(
        NULL, 0, RunThreadB, NULL, 0, &bID);

    WaitForMultipleObjects(2, threads, TRUE, INFINITE);

    printf_s("[Thread main] Per-thread locale is NOT enabled.\n");
    printf_s("[Thread main] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread main] locale::global is set to \"%s\"\n",
        locale().name().c_str());

    CloseHandle(threads[0]);
    CloseHandle(threads[1]);
    CloseHandle(printMutex);

    return 0;
}

unsigned __stdcall RunThreadA(void *params)
{
    _configthreadlocale(_ENABLE_PER_THREAD_LOCALE);
    setlocale(LC_ALL, "french");
    localeSet = TRUE;

    WaitForSingleObject(printMutex, INFINITE);
    printf_s("[Thread A] Per-thread locale is enabled.\n");
    printf_s("[Thread A] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread A] locale::global is set to \"%s\"\n\n",
        locale().name().c_str());
    ReleaseMutex(printMutex);

    return 1;
}

unsigned __stdcall RunThreadB(void *params)
{
    while (!localeSet)
        Sleep(100);

    WaitForSingleObject(printMutex, INFINITE);
    printf_s("[Thread B] Per-thread locale is NOT enabled.\n");
    printf_s("[Thread B] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread B] locale::global is set to \"%s\"\n\n",
        locale().name().c_str());
    ReleaseMutex(printMutex);

    return 1;
}
```

```Output
[Thread A] Per-thread locale is enabled.
[Thread A] CRT locale is set to "French_France.1252"
[Thread A] locale::global is set to "C"

[Thread B] Per-thread locale is NOT enabled.
[Thread B] CRT locale is set to "C"
[Thread B] locale::global is set to "C"

[Thread main] Per-thread locale is NOT enabled.
[Thread main] CRT locale is set to "C"
[Thread main] locale::global is set to "C"
```

## <a name="example"></a>Przykład

W tym przykładzie w wątku głównym, spowoduje utworzenie dwóch wątków podrzędnych. Pierwszy wątek, wątek A, umożliwia ustawień regionalnych na wątek wywołując `_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)`. Drugi wątek, wątek B, a także wątku głównym, nie należy włączać ustawienia regionalne dla wątku. Wątek, następnie przechodzi do zmiany, przy użyciu ustawień regionalnych [locale::global](../standard-library/locale-class.md#global) metody standardowej biblioteki języka C++.

Ponieważ wątek A ma na ustawienia regionalne wątku włączone, tylko funkcje biblioteki wykonawczej języka C w menu start wątku, A za pomocą ustawień regionalnych "Francuska". Funkcje biblioteki wykonawczej języka C w B wątku i wątku głównego w dalszym ciągu używają ustawień regionalnych "C". Jednak ponieważ [locale::global](../standard-library/locale-class.md#global) metody zmieniają ustawienia regionalne "globalny", wszystkie obiekty standardowej biblioteki języka C++ w wszystkie wątki uruchomienie, przy użyciu ustawień regionalnych "Francuska".

```cpp
// multithread_locale_2.cpp
// compile with: /EHsc /MD
#include <clocale>
#include <cstdio>
#include <locale>
#include <process.h>
#include <windows.h>

#define NUM_THREADS 2
using namespace std;

unsigned __stdcall RunThreadA(void *params);
unsigned __stdcall RunThreadB(void *params);

BOOL localeSet = FALSE;
HANDLE printMutex = CreateMutex(NULL, FALSE, NULL);

int main()
{
    HANDLE threads[NUM_THREADS];

    unsigned aID;
    threads[0] = (HANDLE)_beginthreadex(
        NULL, 0, RunThreadA, NULL, 0, &aID);

    unsigned bID;
    threads[1] = (HANDLE)_beginthreadex(
        NULL, 0, RunThreadB, NULL, 0, &bID);

    WaitForMultipleObjects(2, threads, TRUE, INFINITE);

    printf_s("[Thread main] Per-thread locale is NOT enabled.\n");
    printf_s("[Thread main] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread main] locale::global is set to \"%s\"\n",
        locale().name().c_str());

    CloseHandle(threads[0]);
    CloseHandle(threads[1]);
    CloseHandle(printMutex);

    return 0;
}

unsigned __stdcall RunThreadA(void *params)
{
    _configthreadlocale(_ENABLE_PER_THREAD_LOCALE);
    locale::global(locale("french"));
    localeSet = TRUE;

    WaitForSingleObject(printMutex, INFINITE);
    printf_s("[Thread A] Per-thread locale is enabled.\n");
    printf_s("[Thread A] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread A] locale::global is set to \"%s\"\n\n",
        locale().name().c_str());
    ReleaseMutex(printMutex);

    return 1;
}

unsigned __stdcall RunThreadB(void *params)
{
    while (!localeSet)
        Sleep(100);

    WaitForSingleObject(printMutex, INFINITE);
    printf_s("[Thread B] Per-thread locale is NOT enabled.\n");
    printf_s("[Thread B] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread B] locale::global is set to \"%s\"\n\n",
        locale().name().c_str());
    ReleaseMutex(printMutex);

    return 1;
}
```

```Output
[Thread A] Per-thread locale is enabled.
[Thread A] CRT locale is set to "French_France.1252"
[Thread A] locale::global is set to "French_France.1252"

[Thread B] Per-thread locale is NOT enabled.
[Thread B] CRT locale is set to "C"
[Thread B] locale::global is set to "French_France.1252"

[Thread main] Per-thread locale is NOT enabled.
[Thread main] CRT locale is set to "C"
[Thread main] locale::global is set to "French_France.1252"
```

## <a name="example"></a>Przykład

W tym przykładzie w wątku głównym, spowoduje utworzenie dwóch wątków podrzędnych. Pierwszy wątek, wątek A, umożliwia ustawień regionalnych na wątek wywołując `_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)`. Drugi wątek, wątek B, a także wątku głównym, nie należy włączać ustawienia regionalne dla wątku. Wątek B, a następnie przechodzi do zmiany, przy użyciu ustawień regionalnych [setlocale](../preprocessor/setlocale.md) funkcji biblioteki wykonawczej C.

Ponieważ B wątku nie ma ustawień regionalnych na wątek, włączone, funkcji biblioteki wykonawczej języka C w B wątku i wątku głównego zacząć korzystać z ustawień regionalnych "Francuska". Funkcje biblioteki wykonawczej języka C w wątku, A Kontynuuj, aby użyć ustawień regionalnych "C", ponieważ wątek A ma ustawień regionalnych na wątek włączone. Ponadto ponieważ [setlocale](../preprocessor/setlocale.md) nie ma wpływu na ustawienia regionalne standardowej biblioteki języka C++, wszystkie biblioteki standardowej języka C++, które obiekty w dalszym ciągu używają ustawień regionalnych "C".

```cpp
// multithread_locale_3.cpp
// compile with: /EHsc /MD
#include <clocale>
#include <cstdio>
#include <locale>
#include <process.h>
#include <windows.h>

#define NUM_THREADS 2
using namespace std;

unsigned __stdcall RunThreadA(void *params);
unsigned __stdcall RunThreadB(void *params);

BOOL localeSet = FALSE;
BOOL configThreadLocaleCalled = FALSE;
HANDLE printMutex = CreateMutex(NULL, FALSE, NULL);

int main()
{
    HANDLE threads[NUM_THREADS];

    unsigned aID;
    threads[0] = (HANDLE)_beginthreadex(
        NULL, 0, RunThreadA, NULL, 0, &aID);

    unsigned bID;
    threads[1] = (HANDLE)_beginthreadex(
        NULL, 0, RunThreadB, NULL, 0, &bID);

    WaitForMultipleObjects(2, threads, TRUE, INFINITE);

    printf_s("[Thread main] Per-thread locale is NOT enabled.\n");
    printf_s("[Thread main] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread main] locale::global is set to \"%s\"\n",
        locale().name().c_str());

    CloseHandle(threads[0]);
    CloseHandle(threads[1]);
    CloseHandle(printMutex);

    return 0;
}

unsigned __stdcall RunThreadA(void *params)
{
    _configthreadlocale(_ENABLE_PER_THREAD_LOCALE);
    configThreadLocaleCalled = TRUE;
    while (!localeSet)
        Sleep(100);

    WaitForSingleObject(printMutex, INFINITE);
    printf_s("[Thread A] Per-thread locale is enabled.\n");
    printf_s("[Thread A] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread A] locale::global is set to \"%s\"\n\n",
        locale().name().c_str());
    ReleaseMutex(printMutex);

    return 1;
}

unsigned __stdcall RunThreadB(void *params)
{
    while (!configThreadLocaleCalled)
        Sleep(100);
    setlocale(LC_ALL, "french");
    localeSet = TRUE;

    WaitForSingleObject(printMutex, INFINITE);
    printf_s("[Thread B] Per-thread locale is NOT enabled.\n");
    printf_s("[Thread B] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread B] locale::global is set to \"%s\"\n\n",
        locale().name().c_str());
    ReleaseMutex(printMutex);

    return 1;
}
```

```Output
[Thread B] Per-thread locale is NOT enabled.
[Thread B] CRT locale is set to "French_France.1252"
[Thread B] locale::global is set to "C"

[Thread A] Per-thread locale is enabled.
[Thread A] CRT locale is set to "C"
[Thread A] locale::global is set to "C"

[Thread main] Per-thread locale is NOT enabled.
[Thread main] CRT locale is set to "French_France.1252"
[Thread main] locale::global is set to "C"
```

## <a name="example"></a>Przykład

W tym przykładzie w wątku głównym, spowoduje utworzenie dwóch wątków podrzędnych. Pierwszy wątek, wątek A, umożliwia ustawień regionalnych na wątek wywołując `_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)`. Drugi wątek, wątek B, a także wątku głównym, nie należy włączać ustawienia regionalne dla wątku. Wątek B, a następnie przechodzi do zmiany, przy użyciu ustawień regionalnych [locale::global](../standard-library/locale-class.md#global) metody standardowej biblioteki języka C++.

Ponieważ B wątku nie ma ustawień regionalnych na wątek, włączone, funkcji biblioteki wykonawczej języka C w B wątku i wątku głównego zacząć korzystać z ustawień regionalnych "Francuska". Funkcje biblioteki wykonawczej języka C w wątku, A Kontynuuj, aby użyć ustawień regionalnych "C", ponieważ wątek A ma ustawień regionalnych na wątek włączone. Jednak ponieważ [locale::global](../standard-library/locale-class.md#global) metody zmieniają ustawienia regionalne "globalny", wszystkie obiekty standardowej biblioteki języka C++ w wszystkie wątki uruchomienie, przy użyciu ustawień regionalnych "Francuska".

```cpp
// multithread_locale_4.cpp
// compile with: /EHsc /MD
#include <clocale>
#include <cstdio>
#include <locale>
#include <process.h>
#include <windows.h>

#define NUM_THREADS 2
using namespace std;

unsigned __stdcall RunThreadA(void *params);
unsigned __stdcall RunThreadB(void *params);

BOOL localeSet = FALSE;
BOOL configThreadLocaleCalled = FALSE;
HANDLE printMutex = CreateMutex(NULL, FALSE, NULL);

int main()
{
    HANDLE threads[NUM_THREADS];

    unsigned aID;
    threads[0] = (HANDLE)_beginthreadex(
        NULL, 0, RunThreadA, NULL, 0, &aID);

    unsigned bID;
    threads[1] = (HANDLE)_beginthreadex(
        NULL, 0, RunThreadB, NULL, 0, &bID);

    WaitForMultipleObjects(2, threads, TRUE, INFINITE);

    printf_s("[Thread main] Per-thread locale is NOT enabled.\n");
    printf_s("[Thread main] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread main] locale::global is set to \"%s\"\n",
        locale().name().c_str());

    CloseHandle(threads[0]);
    CloseHandle(threads[1]);
    CloseHandle(printMutex);

    return 0;
}

unsigned __stdcall RunThreadA(void *params)
{
    _configthreadlocale(_ENABLE_PER_THREAD_LOCALE);
    configThreadLocaleCalled = TRUE;
    while (!localeSet)
        Sleep(100);

    WaitForSingleObject(printMutex, INFINITE);
    printf_s("[Thread A] Per-thread locale is enabled.\n");
    printf_s("[Thread A] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread A] locale::global is set to \"%s\"\n\n",
        locale().name().c_str());
    ReleaseMutex(printMutex);

    return 1;
}

unsigned __stdcall RunThreadB(void *params)
{
    while (!configThreadLocaleCalled)
        Sleep(100);
    locale::global(locale("french"));
    localeSet = TRUE;

    WaitForSingleObject(printMutex, INFINITE);
    printf_s("[Thread B] Per-thread locale is NOT enabled.\n");
    printf_s("[Thread B] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread B] locale::global is set to \"%s\"\n\n",
        locale().name().c_str());
    ReleaseMutex(printMutex);

    return 1;
}
```

```Output
[Thread B] Per-thread locale is NOT enabled.
[Thread B] CRT locale is set to "French_France.1252"
[Thread B] locale::global is set to "French_France.1252"

[Thread A] Per-thread locale is enabled.
[Thread A] CRT locale is set to "C"
[Thread A] locale::global is set to "French_France.1252"

[Thread main] Per-thread locale is NOT enabled.
[Thread main] CRT locale is set to "French_France.1252"
[Thread main] locale::global is set to "French_France.1252"
```

## <a name="see-also"></a>Zobacz także

[Obsługa wielowątkowości w przypadku starszego kodu (Visual C++)](multithreading-support-for-older-code-visual-cpp.md)<br/>
[_beginthread, _beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md)<br/>
[_configthreadlocale](../c-runtime-library/reference/configthreadlocale.md)<br/>
[setlocale](../preprocessor/setlocale.md)<br/>
[Internacjonalizacja](../c-runtime-library/internationalization.md)<br/>
[Wersja regionalna](../c-runtime-library/locale.md)<br/>
[\<clocale>](../standard-library/clocale.md)<br/>
[\<locale>](../standard-library/locale.md)<br/>
[locale, klasa](../standard-library/locale-class.md)
