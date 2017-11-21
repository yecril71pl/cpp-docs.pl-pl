---
title: "Wielowątkowość i ustawienia regionalne | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- locales [C++], multithreading
- multithreading [C++], locales
- threading [C++], locales
- per-thread locale
ms.assetid: d6fb159a-eaca-4130-a51a-f95d62f71485
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2e60083aa67cc640dafb5c096b83d3097df04db1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="multithreading-and-locales"></a>Wielowątkowość i ustawienia regionalne
Zarówno biblioteki wykonawczej C i standardowa biblioteka C++ zapewniają obsługę zmiany ustawień regionalnych programu. W tym temacie opisano problemy, które wystąpić podczas korzystania z funkcji ustawień regionalnych zarówno bibliotek w aplikacji wielowątkowych.  
  
## <a name="remarks"></a>Uwagi  
 Biblioteka C Runtime Library umożliwia tworzenie aplikacji wielowątkowych przy użyciu `_beginthread` i `_beginthreadex` funkcji. W tym temacie omówiono tylko wielowątkowe aplikacje utworzone przy użyciu tych funkcji. Aby uzyskać więcej informacji, zobacz [_beginthread —, _beginthreadex —](../c-runtime-library/reference/beginthread-beginthreadex.md).  
  
 Aby zmienić ustawienia regionalne, przy użyciu biblioteki wykonawczej C, użyj [setlocale](../preprocessor/setlocale.md) funkcji. W poprzednich wersjach programu Visual C++ ta funkcja będzie zawsze zmodyfikować ustawień regionalnych w całej aplikacji. Brak obsługi teraz ustawienia regionalne na podstawie dla każdego wątku. Jest to realizowane przy użyciu [_configthreadlocale —](../c-runtime-library/reference/configthreadlocale.md) funkcji. Aby określić, że [setlocale](../preprocessor/setlocale.md) tylko należy zmieniać ustawień regionalnych w bieżącym wątku wywołania `_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)` w tym wątku. Z drugiej strony, wywoływania `_configthreadlocale(_DISABLE_PER_THREAD_LOCALE)` spowoduje, że wątek użyć globalnych ustawień regionalnych, a każde wywołanie [setlocale](../preprocessor/setlocale.md) w tym wątku spowoduje zmianę ustawień regionalnych w wszystkie wątki, które nie zostały jawnie włączone ustawienia regionalne dla każdego wątku.  
  
 Aby zmienić ustawienia regionalne, przy użyciu biblioteki wykonawczej języka C++, użyj [locale — klasa](../standard-library/locale-class.md). Wywołując [locale::global](../standard-library/locale-class.md#global) metody, zmiany ustawień regionalnych w każdym wątku, który nie ma jawnie włączone ustawienia regionalne dla każdego wątku. Aby zmienić ustawienia regionalne w jednym wątku lub część aplikacji, po prostu Utwórz wystąpienie `locale` obiektu w tym wątku lub części kodu.  
  
> [!NOTE]
>  Wywoływanie [locale::global](../standard-library/locale-class.md#global) zmienia ustawienia regionalne dla standardowa biblioteka C++ i C Biblioteka środowiska uruchomieniowego. Jednak podczas wywoływania [setlocale](../preprocessor/setlocale.md) tylko zmiany ustawień regionalnych nie dotyczy biblioteki C Runtime; standardowa biblioteka C++.  
  
 W poniższych przykładach pokazano, jak używać [setlocale](../preprocessor/setlocale.md) funkcji [locale — klasa](../standard-library/locale-class.md)i [_configthreadlocale —](../c-runtime-library/reference/configthreadlocale.md) funkcji, aby zmienić ustawienia regionalne aplikacji w różnych scenariuszy.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie wątku głównego spowoduje utworzenie dwóch wątków podrzędnych. Pierwszym wątkiem wątku A, umożliwia ustawienia regionalne dla każdego wątku przez wywołanie metody `_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)`. Drugi wątku wątku B, jak również wątku głównego, nie należy włączać ustawienia regionalne dla każdego wątku. Wątek, następnie będzie kontynuowana, aby zmienić ustawienia regionalne, przy użyciu [setlocale](../preprocessor/setlocale.md) funkcja biblioteki wykonawczej C.  
  
 Ponieważ wątku A ma na ustawienia regionalne wątku włączone, tylko funkcje Biblioteka środowiska wykonawczego języka C w wątku A start przy użyciu ustawień regionalnych "francuskim". Funkcje Biblioteka środowiska wykonawczego języka C w wątku B i w głównym wątku w dalszym ciągu korzystać z ustawieniami regionalnymi "C". Ponadto ponieważ [setlocale](../preprocessor/setlocale.md) nie ma wpływu na ustawienia regionalne standardowa biblioteka C++ wszystkich standardowa biblioteka C++ obiektów w dalszym ciągu korzystać z ustawieniami regionalnymi "C".  
  
```  
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
 W tym przykładzie wątku głównego spowoduje utworzenie dwóch wątków podrzędnych. Pierwszym wątkiem wątku A, umożliwia ustawienia regionalne dla każdego wątku przez wywołanie metody `_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)`. Drugi wątku wątku B, jak również wątku głównego, nie należy włączać ustawienia regionalne dla każdego wątku. Wątek, następnie będzie kontynuowana, aby zmienić ustawienia regionalne, przy użyciu [locale::global](../standard-library/locale-class.md#global) metoda standardowa biblioteka C++.  
  
 Ponieważ wątku A ma na ustawienia regionalne wątku włączone, tylko funkcje Biblioteka środowiska wykonawczego języka C w wątku A start przy użyciu ustawień regionalnych "francuskim". Funkcje Biblioteka środowiska wykonawczego języka C w wątku B i w głównym wątku w dalszym ciągu korzystać z ustawieniami regionalnymi "C". Ponieważ jednak [locale::global](../standard-library/locale-class.md#global) metody zmiany ustawień regionalnych "globalny", wszystkie obiekty standardowa biblioteka C++ wszystkie wątki rozpocząć korzystanie z ustawień regionalnych "francuskim".  
  
```  
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
 W tym przykładzie wątku głównego spowoduje utworzenie dwóch wątków podrzędnych. Pierwszym wątkiem wątku A, umożliwia ustawienia regionalne dla każdego wątku przez wywołanie metody `_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)`. Drugi wątku wątku B, jak również wątku głównego, nie należy włączać ustawienia regionalne dla każdego wątku. Wątek B, a następnie będzie kontynuowana, aby zmienić ustawienia regionalne, przy użyciu [setlocale](../preprocessor/setlocale.md) funkcja biblioteki wykonawczej C.  
  
 Ponieważ B wątku nie ma ustawienia regionalne dla każdego wątku włączone, funkcje Biblioteka środowiska wykonawczego języka C w wątku B i w głównym wątku uruchomiony przy użyciu ustawień regionalnych "francuskim". Funkcje Biblioteka środowiska wykonawczego języka C w wątku A Kontynuuj do użycia z ustawieniami regionalnymi "C", ponieważ wątek A ma ustawienia regionalne dla każdego wątku włączone. Ponadto ponieważ [setlocale](../preprocessor/setlocale.md) nie ma wpływu na ustawienia regionalne standardowa biblioteka C++ wszystkich standardowa biblioteka C++ obiektów w dalszym ciągu korzystać z ustawieniami regionalnymi "C".  
  
```  
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
 W tym przykładzie wątku głównego spowoduje utworzenie dwóch wątków podrzędnych. Pierwszym wątkiem wątku A, umożliwia ustawienia regionalne dla każdego wątku przez wywołanie metody `_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)`. Drugi wątku wątku B, jak również wątku głównego, nie należy włączać ustawienia regionalne dla każdego wątku. Wątek B, a następnie będzie kontynuowana, aby zmienić ustawienia regionalne, przy użyciu [locale::global](../standard-library/locale-class.md#global) metoda standardowa biblioteka C++.  
  
 Ponieważ B wątku nie ma ustawienia regionalne dla każdego wątku włączone, funkcje Biblioteka środowiska wykonawczego języka C w wątku B i w głównym wątku uruchomiony przy użyciu ustawień regionalnych "francuskim". Funkcje Biblioteka środowiska wykonawczego języka C w wątku A Kontynuuj do użycia z ustawieniami regionalnymi "C", ponieważ wątek A ma ustawienia regionalne dla każdego wątku włączone. Ponieważ jednak [locale::global](../standard-library/locale-class.md#global) metody zmiany ustawień regionalnych "globalny", wszystkie obiekty standardowa biblioteka C++ wszystkie wątki rozpocząć korzystanie z ustawień regionalnych "francuskim".  
  
```  
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
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa wielowątkowości w przypadku starszego kodu (Visual C++)](../parallel/multithreading-support-for-older-code-visual-cpp.md)   
 [_beginthread —, _beginthreadex —](../c-runtime-library/reference/beginthread-beginthreadex.md)   
 [_configthreadlocale —](../c-runtime-library/reference/configthreadlocale.md)   
 [setLocale](../preprocessor/setlocale.md)   
 [Przystosowywanie do warunków międzynarodowych](../c-runtime-library/internationalization.md)   
 [Ustawienia regionalne](../c-runtime-library/locale.md)   
 [\<clocale — >](../standard-library/clocale.md)   
 [\<Ustawienia regionalne >](../standard-library/locale.md)   
 [Locale — klasa](../standard-library/locale-class.md)