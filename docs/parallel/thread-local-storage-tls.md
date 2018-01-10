---
title: "Lokalny magazyn wątków (TLS) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- multithreading [C++], Thread Local Storage
- TLS [C++]
- threading [C++], Thread Local Storage
- storing thread-specific data
- thread attribute
- Thread Local Storage [C++]
ms.assetid: 80801907-d792-45ca-b776-df0cf2e9f197
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 47e6be3645e03892d17e45256a5a003d982d973f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="thread-local-storage-tls"></a>Lokalny magazyn wątków (TLS)
Lokalnego magazynu wątków (TLS) to metoda, za pomocą której każdy wątek w danym procesie wielowątkowe można przydzielić lokalizacje, w którym będą przechowywane dane specyficzne dla danego wątku. Dynamicznie dane właściwe dla wątków granica (run-time) są obsługiwane i interfejsu API protokołu TLS ([TlsAlloc](https://msdn.microsoft.com/en-us/library/windows/desktop/ms686801), [TlsGetValue](https://msdn.microsoft.com/en-us/library/windows/desktop/ms686812), [TlsSetValue](https://msdn.microsoft.com/en-us/library/windows/desktop/ms686818), i [TlsFree](https://msdn.microsoft.com/en-us/library/windows/desktop/ms686804)). Aby uzyskać więcej informacji na temat implementowania lokalny magazyn wątków w systemie Windows, zobacz [lokalny magazyn wątków (system Windows)](https://msdn.microsoft.com/en-us/library/windows/desktop/ms686749\(v=vs.85\).aspx).  Win32 i kompilatora języka Visual C++ obsługuje teraz statycznie powiązanej (czas ładowania) dla każdego wątku danych oprócz istniejącej implementacji interfejsu API.  
  
##  <a name="_core_compiler_implementation_for_tls"></a>Implementacja kompilatora dla protokołu TLS  
 **C ++ 11:** `thread_local` Specyfikator klasy magazynu jest zalecany sposób, aby określić lokalny magazyn wątków dla obiektów i klasy elementów członkowskich. Aby uzyskać więcej informacji, zobacz [klasy magazynu (C++)](../cpp/storage-classes-cpp.md).  
  
 Udostępnia atrybut specyficzne dla firmy Microsoft, Visual C++ [wątku](../cpp/thread.md), jako modyfikator klasy magazynu rozszerzonego. Użyj `__declspec` — słowo kluczowe, aby zadeklarować **wątku** zmiennej. Na przykład, poniższy kod deklaruje lokalną zmienną całkowitą wątku i inicjuje ją wartością:  
  
```  
__declspec( thread ) int tls_i = 1;  
```  
  
## <a name="rules-and-limitations"></a>Reguły i ograniczenia  
 Deklarowanie statycznie powiązany lokalnych obiektów wątków i zmienne należy przestrzegać następujących wytycznych. Te wytyczne mają zastosowanie zarówno do [wątku](../cpp/thread.md)i w większości przypadków [element thread_local](../cpp/storage-classes-cpp.md):  
  
-   `thread` Atrybut można stosować tylko do klasy i dane deklaracje i definicje. Nie można użyć w deklaracji lub definicji funkcji. Na przykład następujący kod generowany jest błąd kompilatora:  
  
    ```  
  
    __declspec( thread )void func();     // This will generate an error.  
    ```  
  
-   `thread` Modyfikator może być określony tylko dla elementów danych z `static` zakres. Obejmuje to obiekty danych globalnych (zarówno `static` i `extern`), lokalnego obiektu statycznego i danymi statycznymi członkami klas C++. Obiekty danych nie można zadeklarować ze `thread` atrybutu. Poniższy kod generuje błędy kompilatora:  
  
    ```  
  
    void func1()  
    {  
        __declspec( thread )int tls_i;            // This will generate an error.  
    }  
  
    int func2(__declspec( thread )int tls_i )    // This will generate an error.  
    {  
        return tls_i;  
    }  
    ```  
  
-   Deklaracji i definicji wątku lokalny obiekt wszystkie określić `thread` atrybutu. Na przykład następujący kod generuje błąd:  
  
    ```  
    #define Thread  __declspec( thread )  
    extern int tls_i;        // This will generate an error, since the  
    int __declspec( thread )tls_i;        // declaration and definition differ.  
    ```  
  
-   `thread` Atrybutu nie można użyć jako modyfikator typu. Na przykład następujący kod generowany jest błąd kompilatora:  
  
    ```  
    char __declspec( thread ) *ch;        // Error  
    ```  
  
-   Ponieważ deklaracja C++ obiekty używające `thread` atrybut jest dozwolony, semantycznie równoważne są dwa poniższe przykłady:  
  
    ```  
  
    __declspec( thread ) class B  
    {  
    // Code  
    } BObject;  // OK--BObject is declared thread local.  
  
    class B  
    {  
    // Code  
    };  
    __declspec( thread ) B BObject;  // OK--BObject is declared thread local.  
    ```  
  
-   Adres lokalnego obiektu wątek nie jest uważana za stałej, i dowolne wyrażenie obejmujące takiego adresu nie jest uznawany za wyrażenie stałe. W języku C standard efekt działania tej jest zabraniać użyciem adresu zmiennej lokalnej wątku inicjatora dla obiekt lub wskaźnik. Na przykład następujący kod jest traktowane jako błąd przez kompilator C:  
  
    ```  
  
    __declspec( thread )int tls_i;  
    int *p = &tls_i;       //This will generate an error in C.  
    ```  
  
     To ograniczenie nie ma zastosowania w języku C++. Ponieważ C++ pozwala uzyskać dynamiczna Inicjalizacja wszystkich obiektów, można zainicjować obiektu za pomocą wyrażenia, który korzysta z adresu zmiennej lokalnej wątku. Można to osiągnąć, podobnie jak konstrukcji obiektów lokalnych wątku. Na przykład kodu pokazano wcześniej nie generuje błąd, gdy jest on skompilowany jako plik źródłowy języka C++. Należy pamiętać, że adres zmiennej lokalnej wątku prawidłowe tylko tak długo, jak długo wątku, w którym została wykonana adres nadal istnieje.  
  
-   Standardowe C pozwala na zainicjowanie obiektu lub zmienna o wyrażenie obejmujące odwołanie do samej siebie, ale tylko w przypadku obiektów Niestatyczne zakresu. Mimo że C++ zwykle pozwala takie dynamiczna Inicjalizacja obiektów z wyrażenie obejmujące odwołanie do samej siebie, ten rodzaj inicjacji nie jest dozwolony z obiektów lokalnej wątku. Na przykład:  
  
    ```  
    __declspec( thread )int tls_i = tls_i;                // Error in C and C++   
    int j = j;                               // OK in C++, error in C  
    __declspec( thread )int tls_i = sizeof( tls_i )       // Legal in C and C++  
    ```  
  
     Należy pamiętać, że `sizeof` wyrażenia, która zawiera obiekt inicjowany nie reprezentuje odwołanie do samego siebie i jest włączony w C i C++.  
  
     C++ z powodu możliwych przyszłe ulepszenia funkcji magazynu lokalnego wątku nie zezwala na takie dynamiczna inicjalizacja danych wątku.  
  
-   W systemach operacyjnych Windows przed [!INCLUDE[wiprlhext](../c-runtime-library/reference/includes/wiprlhext_md.md)], `__declspec`(wątek) ma pewne ograniczenia. Jeśli biblioteki DLL deklaruje żadnych danych lub obiekt jako `__declspec`(wątek) może spowodować błąd ochrony po załadowaniu dynamicznie. Po załadowaniu biblioteki DLL z [LoadLibrary](http://msdn.microsoft.com/library/windows/desktop/ms684175), powoduje awarii systemu zawsze, gdy kod odwołuje się do `__declspec`danych (wątek). Ponieważ zmiennej globalnej przestrzeni dla wątku jest przydzielane w czasie wykonywania, rozmiar tego miejsca jest oparta na obliczanie wymagań aplikacji oraz wymagania wszystkie biblioteki DLL połączone statycznie. Jeśli używasz `LoadLibrary`, nie można rozszerzyć to miejsce, aby umożliwić zmienne lokalne wątków zadeklarowana z `__declspec`(wątek). Użyj TLS interfejsów API, takiego jak [TlsAlloc](http://msdn.microsoft.com/library/windows/desktop/ms686801), w bibliotece DLL przydzielić TLS, jeśli biblioteka DLL może być załadowany z `LoadLibrary`.  
  
## <a name="see-also"></a>Zobacz też  
 [Wielowątkowość z językiem C i podsystemem Win32](../parallel/multithreading-with-c-and-win32.md)   
