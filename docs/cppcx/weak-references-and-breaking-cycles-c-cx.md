---
title: Słabe odwołania i przerywanie cykli (C++/CX)
ms.date: 01/22/2017
ms.assetid: 1acb6402-05f0-4951-af94-0e9dab41c53e
ms.openlocfilehash: 04ba70c148121de520b470bd727b26e756858011
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214935"
---
# <a name="weak-references-and-breaking-cycles-ccx"></a>Słabe odwołania i przerywanie cykli (C++/CX)

W każdym systemie typu, który jest oparty na zliczaniu odwołań, odwołania do typów mogą tworzyć *cykle*— to znaczy, że jeden obiekt odwołuje się do drugiego obiektu, drugi obiekt odwołuje się do trzeciego obiektu itd. do momentu, gdy jakiś końcowy obiekt odwołuje się do pierwszego obiektu. W cyklu nie można prawidłowo usunąć obiektów, gdy liczba odwołań jednego obiektu zmieni się na zero. Aby pomóc w rozwiązaniu tego problemu, C++/CX udostępnia klasę [klasy platform:: WeakReference](../cppcx/platform-weakreference-class.md) . `WeakReference`Obiekt obsługuje metodę [Rozwiązuj](../cppcx/platform-weakreference-class.md#resolve) , która zwraca wartość null, jeśli obiekt już nie istnieje lub zgłasza [platformę:: InvalidCastException](../cppcx/platform-invalidcastexception-class.md) , jeśli obiekt jest aktywny, ale nie jest typu `T` .

W `WeakReference` przypadku, gdy **`this`** wskaźnik jest przechwytywany w wyrażeniu lambda, które jest używane do definiowania programu obsługi zdarzeń, należy użyć jednego scenariusza. Zalecamy używanie nazwanych metod podczas definiowania programów obsługi zdarzeń, ale jeśli chcesz użyć wyrażenia lambda dla programu obsługi zdarzeń — lub jeśli musisz przerwać cykl zliczania odwołań w innej sytuacji — użyj `WeakReference` . Oto przykład:

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

Gdy procedura obsługi zdarzeń zgłasza `DisconnectedException` , spowoduje to usunięcie programu obsługi z listy subskrybentów.
