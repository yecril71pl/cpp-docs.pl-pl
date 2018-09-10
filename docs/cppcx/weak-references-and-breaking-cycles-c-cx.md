---
title: Słabe odwołania i przerywanie cykli (C + +/ CX) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: 1acb6402-05f0-4951-af94-0e9dab41c53e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6a262b608bef9ba2e1393337660f58b7f14fb05c
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44108970"
---
# <a name="weak-references-and-breaking-cycles-ccx"></a>Słabe odwołania i przerywanie cykli (C + +/ CX)

W dowolnym system typu, który opiera się na zliczaniu odwołań, można tworzyć odwołania do typów *cykle*— czyli jeden obiekt, który odwołuje się do drugiego obiektu, drugi obiekt, który odwołuje się do innego obiektu, i tak dalej do momentu końcowego obiektu odwołuje się do pierwszy obiekt. W cyklu nie można usunąć obiektów poprawnie, gdy liczba odwołań w jeden obiekt staje się zerem. Aby rozwiązać ten problem, C + +/ CX zapewnia [Platform::WeakReference, klasa](../cppcx/platform-weakreference-class.md) klasy. A `WeakReference` obiekt obsługuje [rozwiązać](../cppcx/platform-weakreference-class.md#resolve) metody, która zwraca wartość null, jeśli obiekt nie jest już istnieje, lub zgłasza [Platform::InvalidCastException](../cppcx/platform-invalidcastexception-class.md) Jeśli obiekt jest aktywny, ale nie jest typu `T`.

Jeden scenariusz, w którym `WeakReference` musi być używana jest, gdy `this` wskaźnik jest przechwytywane w wyrażeniu lambda, które jest używane do definiowania obsługi zdarzeń. Zalecane jest użycie metody nazwanej, podczas definiowania programów obsługi zdarzeń, ale jeśli chcesz użyć wyrażenia lambda do obsługi zdarzenia — lub jeśli trzeba przerwać zliczanie cyklu w niektórych innych sytuacji — użyj `WeakReference`. Oto przykład:

```

using namespace Platform::Details;
using namespace Windows::UI::Xaml;
using namespace Windows::UI::Xaml::Input;
using namespace Windows::UI::Xaml::Controls;

Class1::Class1()
{
    // Class1 has a reference to m_Page
    m_Page = ref new Page();

    // m_Page will have a reference to this Class1
    // so create a weak reference to this
    WeakReference wr(this);
    m_Page->DoubleTapped += ref new DoubleTappedEventHandler(
        [wr](Object^ sender, DoubleTappedRoutedEventArgs^ args)
    {
       // Use the weak reference to get the object
       Class1^ c = wr.Resolve<Class1>();
       if (c != nullptr)
       {
           c->m_eventFired = true;
       }
       else
       {
           // Inform the event that this handler should be removed
           // from the subscriber list
           throw ref new DisconnectedException();
       }
    });
}

}
```

Gdy program obsługi zdarzeń zgłasza `DisconnectedException`, spowoduje wygenerowanie zdarzenia usunąć program obsługi z listy subskrybentów.

## <a name="see-also"></a>Zobacz też

