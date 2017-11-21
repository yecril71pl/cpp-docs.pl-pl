---
title: "_configthreadlocale — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _configthreadlocale
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
dev_langs: C++
helpviewer_keywords:
- configthreadlocale function
- locales, per-thread
- _configthreadlocale function
- per-thread locale
- thread locale
ms.assetid: 10e4050e-b587-4f30-80bc-6c76b35fc770
caps.latest.revision: "24"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a86fd9be56b18c3ad51e3b24e965ae67b6b38fe4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="configthreadlocale"></a>_configthreadlocale
Służy do konfigurowania opcji ustawienia regionalne dla każdego wątku.  
  
## <a name="syntax"></a>Składnia  
  
```  
int _configthreadlocale(  
   int type  
);  
```  
  
### <a name="parameters"></a>Parametry  
 `type`  
 Opcja ustawienia. Jedną z opcji wymienionych w poniższej tabeli.  
  
## <a name="return-value"></a>Wartość zwracana  
 Poprzedni stan ustawienia regionalne dla każdego wątku (`_DISABLE_PER_THREAD_LOCALE` lub `_ENABLE_PER_THREAD_LOCALE`), lub wartość -1 w przypadku awarii.  
  
## <a name="remarks"></a>Uwagi  
 `_configurethreadlocale` Funkcja jest używana w celu kontroli użycia ustawień regionalnych właściwe dla wątków. Użyj jednej z tych opcji do określania stanu ustawienia regionalne dla każdego wątku:  
  
 `_ENABLE_PER_THREAD_LOCALE`  
 Wprowadź bieżące ustawienia regionalne wątku Użyj właściwe dla wątków. Kolejne wywołania `setlocale` wpływają tylko ustawień regionalnych dla wątku w tym wątku.  
  
 `_DISABLE_PER_THREAD_LOCALE`  
 Wprowadź bieżący wątek globalne ustawienia regionalne. Kolejne wywołania `setlocale` w tym wątku mają wpływ na inne wątki używające globalnych ustawień regionalnych.  
  
 `0`  
 Pobiera bieżące ustawienia dla tego konkretnego wątku.  
  
 Te funkcje wpłynąć na zachowanie `setlocale`, `_tsetlocale`, `_wsetlocale`, i `_setmbcp`. Jeśli ustawienia regionalne dla każdego wątku jest wyłączona, wszelkie kolejne wywołanie `setlocale` lub `_wsetlocale` zmiany ustawień regionalnych wszystkie wątki globalnych ustawień regionalnych. Po włączeniu ustawienia regionalne dla każdego wątku `setlocale` lub `_wsetlocale` wpływa tylko na ustawienia regionalne bieżącego wątku.  
  
 Jeśli używasz `_configurethreadlocale` Aby włączyć ustawienia regionalne dla każdego wątku, firma Microsoft zaleca, należy wywołać `setlocale` lub `_wsetlocale` można ustawić preferowanych ustawień regionalnych natychmiast później w tym wątku.  
  
 Jeśli `type` nie jest jedną z wartości wymienionych w tabeli, ta funkcja wywołuje program obsługi nieprawidłowych parametrów, z zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może kontynuować, ta funkcja ustawia `errno` do `EINVAL` i zwraca wartość -1.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_configthreadlocale`|\<Locale.h >|  
  
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
 [setLocale, _wsetlocale —](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [_beginthread —, _beginthreadex —](../../c-runtime-library/reference/beginthread-beginthreadex.md)   
 [Ustawienia regionalne](../../c-runtime-library/locale.md)   
 [Wielowątkowość i ustawienia regionalne](../../parallel/multithreading-and-locales.md)  
