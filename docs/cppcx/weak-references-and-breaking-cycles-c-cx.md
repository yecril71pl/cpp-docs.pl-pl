---
title: Słabe odwołania i cykle podziału (C + +/ CX) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: 1acb6402-05f0-4951-af94-0e9dab41c53e
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 48b5d73d85383056b17c806e061b131b12d821a9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="weak-references-and-breaking-cycles-ccx"></a>Słabe odwołania i cykle podziału (C + +/ CX)
W każdym systemie typu opartego na liczenie odwołań w formularzu można odwołania do typów *cykle*— to znaczy jeden obiekt odwołuje się do innego obiektu, drugi obiekt odwołuje się do innego obiektu, i tak dalej do momentu niektóre końcowego obiektu odwołuje się do pierwszy obiekt. W cyklu nie można usunąć obiektów poprawnie, jeśli jeden obiekt liczba odwołań wynosi zero. Aby rozwiązać ten problem, C + +/ CX zapewnia [klasy Platform::WeakReference](../cppcx/platform-weakreference-class.md) klasy. A `WeakReference` obiekt obsługuje [rozwiązać](../cppcx/platform-weakreference-class.md#resolve) metodę, która zwraca wartość null, jeśli obiekt już istnieje, lub zgłasza [Platform::InvalidCastException](../cppcx/platform-invalidcastexception-class.md) Jeśli obiekt jest aktywna, ale nie jest typu `T`.  
  
 Jeden scenariusz, w którym `WeakReference` musi być używana jest wtedy, gdy `this` wskaźnika jest przechwytywany w wyrażeniu lambda, które służy do definiowania program obsługi zdarzeń. Zalecane jest użycie metody o nazwie podczas definiowania procedury obsługi zdarzeń, ale jeśli chcesz użyć wyrażenia lambda do obsługi zdarzenia — lub jeśli zajdzie potrzeba Podziel zliczanie cyklu w niektórych innych sytuacji — użyj `WeakReference`. Oto przykład:  
  
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
  
 Jeśli program obsługi zdarzeń zgłasza `DisconnectedException`, spowoduje wygenerowanie zdarzenia do usunięcia z listy subskrybentów programu obsługi.  
  
## <a name="see-also"></a>Zobacz też  


