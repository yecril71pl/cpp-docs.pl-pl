---
title: Wątek | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- thread_cpp
dev_langs:
- C++
helpviewer_keywords:
- thread local storage (TLS)
- thread __declspec keyword
- TLS (thread local storage), compiler implementation
- __declspec keyword [C++], thread
ms.assetid: 667f2a77-6d1f-4b41-bee8-05e67324fab8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 80ea212f8c888680edf50e269c89e62988a0ee36
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46104390"
---
# <a name="thread"></a>wątek

**Microsoft Specific**

**Wątku** modyfikator klasy magazynu rozszerzonego służy do deklarowania zmiennej lokalnej wątku. Przenośna równoważne w C ++ 11 i nowsze, można użyć [thread_local](../cpp/storage-classes-cpp.md#thread_local) Specyfikator klasy magazynowania dla przenośnego kodu. Na Windows `thread_local` jest implementowane za pomocą **__declspec(thread)**.

## <a name="syntax"></a>Składnia

> **__declspec (wątek)** *deklaratora*

## <a name="remarks"></a>Uwagi

Pamięć lokalna wątku (TLS) to mechanizm, za pomocą którego każdy wątek w procesie wielowątkowym przydziela pamięć dla danych specyficznych wątku. W standardowych programach wielowątkowych, dane są współużytkowane przez wszystkie wątki danego procesu, natomiast pamięć lokalna wątku jest mechanizmem przydzielania danych osobno dla danego wątku. Aby uzyskać pełne omówienie wątków, zobacz [wielowątkowość](../parallel/multithreading-support-for-older-code-visual-cpp.md).

Deklaracje zmiennych lokalnych wątku muszą używać [rozszerzonej składni atrybutu](../cpp/declspec.md) i **__declspec** — słowo kluczowe z **wątku** — słowo kluczowe. Na przykład, poniższy kod deklaruje lokalną zmienną całkowitą wątku i inicjuje ją wartością:

```cpp
__declspec( thread ) int tls_i = 1;
```

Używając zmiennych thread-local w bibliotekach ładowane dynamicznie, musisz być znane czynniki, które może spowodować, że nie można poprawnie zainicjować zmienną lokalną wątku:

1. Jeśli zmienna jest inicjowana za pomocą wywołania funkcji (w tym konstruktory), ta funkcja tylko będzie wywoływana w wątku, który spowodował pliku binarnego/DLL do załadowania do procesu i te wątki, które są uruchomione, gdy załadowano danych binarnych/DLL. Inicjowanie funkcji nie są wywoływane dla każdego wątku, w którym jest już uruchomiona, gdy biblioteka DLL został załadowany. Dynamiczna Inicjalizacja odbywa się na wywołanie funkcji DllMain DLL_THREAD_ATTACH, ale biblioteki DLL nigdy nie pobiera, które komunikatów Jeśli biblioteka DLL nie jest w trakcie procesu podczas uruchamiania wątku.

1. Zmiennymi lokalnymi wątku, które są statycznie inicjowane przy użyciu stałych wartości zwykle są inicjowane poprawnie we wszystkich wątkach. Jednak grudnia 2017 r. występuje znanej zgodności problem w kompilatorze Microsoft Visual C++, według której otrzymywać zmienne constexpr dynamicznego zamiast statycznego inicjowania.

   Uwaga: Oba powyższe problemy powinny rozwiązany w przyszłych aktualizacji kompilatora.

Ponadto musisz przestrzegać następujących wytycznych podczas deklarowania zmiennych i obiektów lokalnych wątku:

- Można zastosować **wątku** atrybutu tylko do klasy i deklaracje i definicje danych; **wątku** nie można używać w deklaracji lub definicji funkcji.

- Można określić **wątku** atrybutu tylko dla elementów danych ze statycznym okresem magazynu. Obejmuje to globalnych obiektów danych (zarówno **statyczne** i **extern**), lokalnych obiektów statycznych i statycznych składowych danych klas. Nie można deklarować automatycznych obiektów danych z **wątku** atrybutu.

- Należy użyć **wątku** atrybutu dla deklaracji i definicji lokalnego obiektu wątku, czy deklaracja i definicja występują w ten sam plik lub osobnych plikach.

- Nie można użyć **wątku** atrybutu jako modyfikatora typu.

- Ponieważ deklaracja dla obiektów, które używają **wątku** atrybut jest dozwolony, dwa poniższe przykłady są semantycznie równoważne:

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

   Należy pamiętać, że **sizeof** wyrażenie, które zawiera inicjowany obiekt nie stanowi odwołanie do samego siebie i jest dozwolone w językach C i C++.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[__declspec](../cpp/declspec.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[Lokalny magazyn wątków (TLS)](../parallel/thread-local-storage-tls.md)