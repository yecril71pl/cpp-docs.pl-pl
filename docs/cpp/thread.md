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
ms.workload: cplusplus
ms.openlocfilehash: b26487e7f5f11bb32f418b438e9d0396b5854a91
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="thread"></a>wątek

**Dotyczące firmy Microsoft**  
**Wątku** modyfikator klasy magazynu rozszerzonego służy do deklarowania zmiennej lokalnej wątku. Komputer przenośny równoważne w języku C ++ 11 i nowszych można użyć [element thread_local](../cpp/storage-classes-cpp.md#thread_local) Specyfikator klasy magazynu dla przenośnego kodu. W systemie Windows **element thread_local** jest realizowana za pomocą **__declspec(thread)**.

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

Używając zmiennych thread-local w bibliotekach ładowane dynamicznie, należy zwrócić uwagę czynników, które mogą spowodować zmiennej lokalnej wątku nie można poprawnie zainicjować:

1) Jeśli zmienna jest inicjowany z wywołania funkcji (łącznie z konstruktorów), ta funkcja będzie można wywołać tylko dla wątku, który spowodował binary/DLL załadować w procesie, a dla tych wątków, które są uruchomione, gdy załadowano danych binarnych/DLL. Funkcje inicjowania nie są nazywane do innego wątku, który jest już uruchomiona, gdy biblioteka DLL została załadowana. Dynamiczna Inicjalizacja występuje na wywołanie funkcji DllMain dla DLL_THREAD_ATTACH, ale plik DLL, który nigdy nie pobiera, które komunikatów, jeśli plik DLL, który nie jest w procesie uruchomienia wątku. 

2) Zmienne lokalne wątków, zawierającymi statycznie o stałej wartości zwykle są poprawnie zainicjowane na wszystkie wątki. Począwszy od grudnia 2017 istnieje jednak problem znane zgodność kompilatora C++ firmy Microsoft zgodnie z którymi odbierania constexpr zmienne dynamiczne zamiast statycznego inicjowania.  
  
   Uwaga: Oba te problemy mogą naprawiony w przyszłych aktualizacji kompilatora.


Ponadto narzucają wytyczne podczas deklarowania zmiennych i obiektów lokalnej wątku:

- Możesz zastosować **wątku** atrybutu tylko do klasy i danych deklaracje i definicje; **wątku** nie można użyć w deklaracji lub definicji funkcji.

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
