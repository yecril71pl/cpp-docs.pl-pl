---
title: Lokalny magazyn wątków (TLS) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- multithreading [C++], Thread Local Storage
- TLS [C++]
- threading [C++], Thread Local Storage
- storing thread-specific data
- thread attribute
- Thread Local Storage [C++]
ms.assetid: 80801907-d792-45ca-b776-df0cf2e9f197
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a71ed98e550d9db43a42289cfb26e3daaaf68027
ms.sourcegitcommit: b92ca0b74f0b00372709e81333885750ba91f90e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/16/2018
ms.locfileid: "42465901"
---
# <a name="thread-local-storage-tls"></a>Lokalny magazyn wątków (TLS)
Lokalnego magazynu wątków (TLS) to metoda, za pomocą którego każdy wątek w danym procesie wielowątkowym można przydzielić lokalizacji do przechowywania danych specyficznych wątku. Dynamicznie danych specyficznych wątku granica (run-time) jest obsługiwana za pomocą interfejsu API protokołu TLS ([TlsAlloc](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-tlsalloc).  Win32 i kompilator języka Visual C++ obsługuje obecnie danych statycznie powiązanej (czas ładowania) na wątek, oprócz istniejącej implementacji interfejsu API.  
  
##  <a name="_core_compiler_implementation_for_tls"></a> Implementacja kompilatora protokołu TLS  
 
**C ++ 11:** `thread_local` specyfikatora klasy magazynu jest to zalecany sposób, aby określić lokalny magazyn wątków dla obiektów i składowych klasy. Aby uzyskać więcej informacji, zobacz [klasy magazynu (C++)](../cpp/storage-classes-cpp.md).  
  
Visual C++ zapewnia również atrybut specyficzne dla firmy Microsoft, [wątku](../cpp/thread.md), jako modyfikator klasy magazynu rozszerzonego. Użyj **__declspec** — słowo kluczowe do deklarowania **wątku** zmiennej. Na przykład, poniższy kod deklaruje lokalną zmienną całkowitą wątku i inicjuje ją wartością:  
  
```  
__declspec( thread ) int tls_i = 1;  
```  
  
## <a name="rules-and-limitations"></a>Reguły i ograniczenia  
 
Należy przestrzegać następujących wytycznych podczas deklarowania statycznie wiązania zmiennych i obiektów lokalnych wątku. Niniejsze wytyczne mają zastosowanie zarówno do [wątku](../cpp/thread.md)i w większości przypadków [thread_local](../cpp/storage-classes-cpp.md):  
  
- **Wątku** atrybut można stosować tylko do definicje i deklaracje klas i danych. Nie można używać w deklaracji lub definicji funkcji. Na przykład poniższy kod generuje błąd kompilatora:  
  
    ```  
    __declspec( thread )void func();     // This will generate an error.  
    ```  
  
- **Wątku** modyfikator może być określony tylko dla elementów danych ze **statyczne** zakresu. Obejmuje to globalnych obiektów danych (zarówno **statyczne** i **extern**), lokalnych obiektów statycznych i statycznych składowych danych klas języka C++. Nie można zadeklarować automatycznych obiektów danych z **wątku** atrybutu. Poniższy kod generuje błędy kompilatora:  
  
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
  
- Deklaracji i definicji lokalnego obiektu wszystkie określić wątku **wątku** atrybutu. Na przykład poniższy kod generuje błąd:  
  
    ```  
    #define Thread  __declspec( thread )  
    extern int tls_i;        // This will generate an error, since the  
    int __declspec( thread )tls_i;        // declaration and definition differ.  
    ```  
  
- **Wątku** atrybutu nie można użyć jako modyfikatora typu. Na przykład poniższy kod generuje błąd kompilatora:  
  
    ```  
    char __declspec( thread ) *ch;        // Error  
    ```  
  
- Ponieważ deklaracja C++ obiektów używających **wątku** atrybut jest dozwolony, dwa poniższe przykłady są semantycznie równoważne:  
  
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
  
- Adres lokalnego obiektu wątku nie jest traktowany jako stała i dowolne wyrażenie obejmujące takiego adresu nie uznaje się za wyrażeniem stałym. W standardowej C efekt działania tej jest zabraniają użycie adresu zmiennej lokalnej wątku jako inicjatora dla obiektu lub wskaźnika. Na przykład poniższy kod jest oznaczany jako błąd przez kompilator C:  
  
    ```  
    __declspec( thread )int tls_i;  
    int *p = &tls_i;       //This will generate an error in C.  
    ```  
  
     To ograniczenie nie ma zastosowania w języku C++. Ponieważ C++ pozwala na dynamiczne zainicjowanie wszystkich obiektów, należy zainicjować obiekt, za pomocą wyrażenia, który używa adresu zmiennej lokalnej wątku. Można to osiągnąć, podobnie jak konstrukcji obiektów lokalnych wątku. Na przykład kodu pokazanego wcześniej nie generuje błąd, gdy jest ona kompilowana jako pliku źródłowego języka C++. Należy pamiętać, że adres zmiennej lokalnej wątku prawidłowe tylko tak długo, jak wątek, w którym została wykonana adres nadal istnieje.  
  
- Standard języka C umożliwia inicjowania obiektu lub zmiennej za pomocą wyrażenia zawierającego odwołanie do samego siebie, ale tylko w przypadku obiektów o zakresie niestatycznym. Mimo iż język C++ ogólnie dopuszcza dynamiczną inicjalizację obiektu za pomocą wyrażenia zawierającego odwołanie do samego siebie, tento typ inicializace nie jest dozwolony z obiektów lokalnych wątku. Na przykład:  
  
    ```  
    __declspec( thread )int tls_i = tls_i;                // Error in C and C++   
    int j = j;                               // OK in C++, error in C  
    __declspec( thread )int tls_i = sizeof( tls_i )       // Legal in C and C++  
    ```  
  
     Należy pamiętać, że `sizeof` wyrażenie, które zawiera inicjowany obiekt nie reprezentuje odwołanie do samego siebie i jest włączone w C i C++.  
  
     C++ nie dopuszcza dynamiczną inicjalizację danych wątku ze względu na możliwe przyszłe rozszerzenia będą miały do infrastruktury magazynu lokalnego wątku.  
  
- W systemach operacyjnych Windows przed Windows Vista `__declspec`(wątek) ma pewne ograniczenia. Jeśli biblioteka DLL deklaruje żadnych danych ani obiektu jako `__declspec`(wątek), może to spowodować błąd ochrony Jeśli dynamicznie załadowane. Po załadowaniu pliku DLL za pomocą [LoadLibrary](http://msdn.microsoft.com/library/windows/desktop/ms684175), sprawia, że wystąpił błąd systemu zawsze wtedy, gdy kod odwołuje się do `__declspec`danych (wątek). Ponieważ zmiennej globalnej przestrzeni na wątek jest przydzielany w czasie wykonywania, rozmiar to miejsce opiera się na obliczanie wymagań aplikacji, a także wymagania wszystkie biblioteki dll, które są statycznie łączone. Kiedy używasz `LoadLibrary`, nie można rozszerzyć tego miejsca, aby umożliwić zadeklarowane za pomocą zmiennych lokalnych wątku `__declspec`(wątek). Używanie interfejsów API protokołu TLS, takiej jak [TlsAlloc](http://msdn.microsoft.com/library/windows/desktop/ms686801), w bibliotece DLL, można przydzielić TLS, jeśli biblioteka DLL jest obciążany `LoadLibrary`.  
  
## <a name="see-also"></a>Zobacz też  
 
[Wielowątkowość z językiem C i podsystemem Win32](../parallel/multithreading-with-c-and-win32.md)   