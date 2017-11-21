---
title: "Lokalny magazyn wątków | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- thread-local variables
- TLS (thread local storage)
- thread storage-class attribute
- thread-local storage
- storage, thread local storage
ms.assetid: a0f1b109-c953-4079-aa10-e47f5483173d
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 46aaf6677a779ada2457814aecba5c84a59e1f1c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="thread-local-storage"></a>Lokalny magazyn wątków
**Dotyczące firmy Microsoft**  
  
 Lokalnego magazynu wątków (TLS) to mechanizm, za pomocą której każdy wątek w danym procesie wielowątkowe przydziela magazynu dla danych właściwych dla wątku. W standardowych programach wielowątkowych, dane są współużytkowane przez wszystkie wątki danego procesu, natomiast pamięć lokalna wątku jest mechanizmem przydzielania danych osobno dla danego wątku. Aby uzyskać szczegółowe omówienie wątków, zobacz [procesów i wątków](http://msdn.microsoft.com/library/windows/desktop/ms684841) w [!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)].  
  
 Języka Microsoft C zawiera atrybut klasy magazynu rozszerzonego, wątek, który jest używany z __declspec — słowo kluczowe do zadeklarować zmiennej lokalnej wątku. Na przykład, poniższy kod deklaruje lokalną zmienną całkowitą wątku i inicjuje ją wartością:  
  
```  
__declspec( thread ) int tls_i = 1;  
```  
  
 Kiedy są deklarowanie statycznie powiązanej wątku ich w zmiennych lokalnych należy przestrzegać poniższych wskazówek:  
  
-   Korzystanie z **__declspec(thread)** może zakłócać [opóźnienia ładowania](../build/reference/linker-support-for-delay-loaded-dlls.md) biblioteki DLL importuje**.**  
  
-   Atrybut wątku można stosować tylko do danych deklaracje i definicje. Nie można użyć w deklaracji lub definicji funkcji. Na przykład następujący kod generowany jest błąd kompilatora:  
  
    ```  
    #define Thread   __declspec( thread )  
    Thread void func();      /* Error */  
    ```  
  
-   Atrybut wątku można określić tylko dla elementów danych ze statycznym okresem magazynu. Obejmuje to dane globalne (statyczne i zewnętrzne) i lokalnych danych statycznych. Nie można zadeklarować automatyczne dane z atrybutem wątku. Na przykład następujący kod generuje błędy kompilatora:  
  
    ```  
    #define Thread   __declspec( thread )  
    void func1()  
    {  
        Thread int tls_i;            /* Error */  
    }  
  
    int func2( Thread int tls_i )    /* Error */  
    {  
       return tls_i;  
    }  
    ```  
  
-   Należy użyć atrybut wątku dla deklaracji i definicji danych lokalnych wątku, niezależnie od tego, czy wystąpienia deklaracji i definicji w tym samym pliku lub oddzielnych plików. Na przykład następujący kod generuje błąd:  
  
    ```  
    #define Thread   __declspec( thread )  
    extern int tls_i;     /* This generates an error, because the   */  
    int Thread tls_i;     /* declaration and the definition differ. */  
    ```  
  
-   Atrybut wątku nie można użyć jako modyfikator typu. Na przykład następujący kod generowany jest błąd kompilatora:  
  
    ```  
    char *ch __declspec( thread );      /* Error */  
    ```  
  
-   Adres zmiennej lokalnej wątku nie jest uważana za stałej, i dowolne wyrażenie obejmujące takiego adresu nie jest uznawany za wyrażenie stałe. Oznacza to, że nie możesz użyć adresu zmiennej lokalnej wątku jako inicjator dla wskaźnika. Na przykład kompilator flagi następujący kod jako błąd:  
  
    ```  
    #define Thread   __declspec( thread )  
    Thread int tls_i;  
    int *p = &tls_i;      /* Error */  
    ```  
  
-   C umożliwia inicjowanie zmiennej z wyrażenie obejmujące odwołanie do samej siebie, ale tylko w przypadku obiektów Niestatyczne zakresu. Na przykład:  
  
    ```  
    #define Thread   __declspec( thread )  
    Thread int tls_i = tls_i;             /* Error */  
    int j = j;                            /* Error */  
    Thread int tls_i = sizeof( tls_i )    /* Okay  */  
    ```  
  
     Należy pamiętać, że wyrażenie sizeof, które obejmuje Zainicjowanie nie stanowi odwołanie do samej siebie, czy jest dozwolone.  
  
-   Korzystanie z **__declspec(thread)** może zakłócać [opóźnienia ładowania](../build/reference/linker-support-for-delay-loaded-dlls.md) biblioteki DLL importuje**.**  
  
 Aby uzyskać więcej informacji o używaniu atrybut wątku, zobacz [wielowątkowość tematy](../parallel/multithreading-support-for-older-code-visual-cpp.md).  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [C rozszerzone atrybuty klasy magazynu](../c-language/c-extended-storage-class-attributes.md)