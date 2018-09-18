---
title: Lokalny magazyn wątków | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- thread-local variables
- TLS (thread local storage)
- thread storage-class attribute
- thread-local storage
- storage, thread local storage
ms.assetid: a0f1b109-c953-4079-aa10-e47f5483173d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2884abbf02c9eb244d6fb446c7158b708c211557
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46066456"
---
# <a name="thread-local-storage"></a>Lokalny magazyn wątków

**Microsoft Specific**

Lokalny magazyn wątku (TLS) to mechanizm, za pomocą którego każdy wątek w danym procesie wielowątkowym przydziela pamięć dla danych specyficznych wątku. W standardowych programach wielowątkowych, dane są współużytkowane przez wszystkie wątki danego procesu, natomiast pamięć lokalna wątku jest mechanizmem przydzielania danych osobno dla danego wątku. Aby uzyskać pełne omówienie wątków, zobacz [procesy i wątki](/windows/desktop/ProcThread/processes-and-threads) w zestawie Windows SDK.

Język Microsoft C zawiera atrybuty rozszerzone klasy magazynu, wątek, który jest używany z __declspec — słowo kluczowe, aby zadeklarować zmienną lokalną wątku. Na przykład, poniższy kod deklaruje lokalną zmienną całkowitą wątku i inicjuje ją wartością:

```
__declspec( thread ) int tls_i = 1;
```

Po użytkownik deklaruje wątku statycznie powiązanych zmiennych lokalnych należy przestrzegać następujących wytycznych:

- Zmiennymi lokalnymi wątku, które mają dynamiczna Inicjalizacja są inicjowane tylko na wątek, który powoduje, że biblioteki DLL do załadowania i wątki, które zostały już uruchomione w procesie. Aby uzyskać więcej informacji, zobacz [wątku](../cpp/thread.md).

- Atrybut wątku można zastosować tylko do deklaracje i definicje danych. Nie można używać w deklaracji lub definicji funkcji. Na przykład poniższy kod generuje błąd kompilatora:

    ```C
    #define Thread   __declspec( thread )
    Thread void func();      /* Error */
    ```

- Atrybut wątku można określić tylko dla elementów danych ze statycznym okresem magazynu. Obejmuje to dane globalne (statyczne i zewnętrzne) i lokalnych danych statycznych. Nie można zadeklarować automatyczne danych za pomocą atrybut wątku. Na przykład poniższy kod generuje błędy kompilatora:

    ```C
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

- Musisz podać atrybut wątku dla deklaracji i definicji danych lokalnych wątku, niezależnie od tego, czy deklaracja i definicja występują w tym samym pliku lub osobnych plikach. Na przykład poniższy kod generuje błąd:

    ```C
    #define Thread   __declspec( thread )
    extern int tls_i;     /* This generates an error, because the   */
    int Thread tls_i;     /* declaration and the definition differ. */
    ```

- Atrybut wątku nie można użyć jako modyfikatora typu. Na przykład poniższy kod generuje błąd kompilatora:

    ```C
    char *ch __declspec( thread );      /* Error */
    ```

- Adres zmiennej lokalnej wątku nie jest uważany za stałą i dowolne wyrażenie obejmujące takiego adresu nie uznaje się za wyrażeniem stałym. Oznacza to, że adres zmiennej lokalnej wątku nie można użyć jako inicjator dla wskaźnika. Na przykład kompilator następujący kod jako błąd:

    ```C
    #define Thread   __declspec( thread )
    Thread int tls_i;
    int *p = &tls_i;      /* Error */
    ```

- Język C umożliwia inicjowanie zmiennej za pomocą wyrażenia zawierającego odwołanie do samego siebie, ale tylko w przypadku obiektów o zakresie niestatycznym. Na przykład:

    ```C
    #define Thread   __declspec( thread )
    Thread int tls_i = tls_i;             /* Error */
    int j = j;                            /* Error */
    Thread int tls_i = sizeof( tls_i )    /* Okay  */
    ```

     Pamiętaj, że wyrażenie sizeof, która zawiera zmienną inicjowany nie stanowi odwołanie do samego siebie jest dozwolone.

- Korzystanie z **__declspec(thread)** może zakłócać [opóźnienie ładowania](../build/reference/linker-support-for-delay-loaded-dlls.md) importowanych bibliotek DLL **.**

Aby uzyskać więcej informacji o używaniu atrybut wątku, zobacz [tematy o wielowątkowości](../parallel/multithreading-support-for-older-code-visual-cpp.md).

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz też

[Rozszerzone atrybuty klasy magazynu języka C](../c-language/c-extended-storage-class-attributes.md)