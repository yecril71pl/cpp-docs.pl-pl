---
title: "Wątek | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: thread_cpp
dev_langs: C++
helpviewer_keywords:
- thread local storage (TLS)
- thread __declspec keyword
- TLS (thread local storage), compiler implementation
- __declspec keyword [C++], thread
ms.assetid: 667f2a77-6d1f-4b41-bee8-05e67324fab8
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7d81cd7e569cd2baa8ab50b1904fa3ac15b36d0b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="thread"></a>wątek

**Dotyczące firmy Microsoft**  
**Wątku** modyfikator klasy magazynu rozszerzonego służy do deklarowania zmiennej lokalnej wątku. Komputer przenośny równoważne w języku C ++ 11 i nowszych można użyć [element thread_local](../cpp/storage-classes-cpp.md#thread_local) Specyfikator klasy magazynu.

## <a name="syntax"></a>Składnia

```
__declspec( thread ) declarator
```

## <a name="remarks"></a>Uwagi

Pamięć lokalna wątku (TLS) to mechanizm, za pomocą którego każdy wątek w procesie wielowątkowym przydziela pamięć dla danych specyficznych wątku. W standardowych programach wielowątkowych, dane są współużytkowane przez wszystkie wątki danego procesu, natomiast pamięć lokalna wątku jest mechanizmem przydzielania danych osobno dla danego wątku. Aby uzyskać szczegółowe omówienie wątków, zobacz [Multithreading](../parallel/multithreading-support-for-older-code-visual-cpp.md).

Deklaracje zmiennych lokalnych wątku należy użyć [rozszerzona Składnia atrybutu](../cpp/declspec.md) i `__declspec` — słowo kluczowe z **wątku** — słowo kluczowe. Na przykład, poniższy kod deklaruje lokalną zmienną całkowitą wątku i inicjuje ją wartością:

```cpp
__declspec( thread ) int tls_i = 1;  
```

Musisz przestrzegać następujących wytycznych podczas deklarowania obiektów i zmiennych lokalnych wątku:

- Możesz zastosować **wątku** atrybutu tylko do klasy i danych deklaracje i definicje; **wątku** nie można użyć w deklaracji lub definicji funkcji.

- Korzystanie z **wątku** atrybut może zakłócać [opóźnienia ładowania](../build/reference/linker-support-for-delay-loaded-dlls.md) biblioteki DLL importuje.

- W systemie XP **wątku** nie może działać prawidłowo, jeśli biblioteka DLL używa danych __declspec(thread) i jest ładowany dynamicznie za pośrednictwem metody LoadLibrary.

- Można określić **wątku** atrybutu tylko dla elementów danych ze statycznym okresem magazynu. Obejmuje to obiekty danych globalnych (zarówno **statycznych** i **extern**), lokalnego obiektu statycznego i danymi statycznymi członkami klas. Nie można zadeklarować obiekty automatyczne dane o **wątku** atrybutu.

- Należy użyć **wątku** atrybutu deklaracji i definicji obiektu lokalnego wątku czy deklaracji i definicji są wykonywane w tym samym pliku lub oddzielnych plików.

- Nie można użyć **wątku** atrybut modyfikator typu.

- Ponieważ deklaracji obiektów, które używają **wątku** atrybut jest dozwolony, te dwa przykłady są semantycznie równoważne:

    ```cpp
    // declspec_thread_2.cpp
    // compile with: /LD
    __declspec( thread ) class B {
    public:
       int data;
    } BObject;   // BObject declared thread local.

    class B2 {
    public:
       int data;
    };
    __declspec( thread ) B2 BObject2;   // BObject2 declared thread local.
    ```

- Standardowy język C umożliwia inicjowanie obiektu lub zmiennej za pomocą wyrażenia zawierającego odwołanie do samego siebie, ale tylko dla obiektów o zakresie niestatycznym. Mimo że język C++ normalnie dopuszcza dynamiczną inicjalizację obiektu za pomocą wyrażenia zawierającego odwołanie do samego siebie, to ten typ inicjalizacji jest niedozwolony dla obiektów lokalnych wątku. Na przykład:

    ```cpp
    // declspec_thread_3.cpp
    // compile with: /LD
    #define Thread __declspec( thread )
    int j = j;   // Okay in C++; C error
    Thread int tls_i = sizeof( tls_i );   // Okay in C and C++
    ```

     Należy pamiętać, że **sizeof** wyrażenia, która zawiera obiekt inicjowany w C i C++ jest dozwolone i nie stanowi odwołanie do samej siebie.

**KOŃCOWY określonych firmy Microsoft**

## <a name="see-also"></a>Zobacz też

[__declspec](../cpp/declspec.md)  
[Słowa kluczowe](../cpp/keywords-cpp.md)  
[Lokalny magazyn wątków (TLS)](../parallel/thread-local-storage-tls.md)
