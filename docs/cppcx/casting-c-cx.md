---
title: RzutowanieC++(/CX)
ms.date: 06/19/2018
ms.assetid: 5247f6c7-6a0a-4021-97c9-21c868bd9455
ms.openlocfilehash: 6711320fd9ca52360f702e029fdc8e129c90c6cd
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740542"
---
# <a name="casting-ccx"></a>RzutowanieC++(/CX)

Cztery różne Operatory rzutowania stosują się do typów środowisko wykonawcze systemu Windows: [operatora static_cast](../cpp/static-cast-operator.md), operatora [dynamic_cast](../cpp/dynamic-cast-operator.md), **operatora safe_cast**i [operatora reinterpret_cast](../cpp/reinterpret-cast-operator.md). **safe_cast** i **static_cast** zgłasza wyjątek, jeśli nie można wykonać konwersji; [Operator static_cast](../cpp/static-cast-operator.md) wykonuje także sprawdzanie typu w czasie kompilacji. **dynamic_cast** zwraca **nullptr** , jeśli nie można skonwertować typu. Chociaż element **reinterpret_cast** zwraca wartość różną od null, może być nieprawidłowy. Z tego powodu zaleca się, aby nie używać **operatora reinterpret_cast** , chyba że wiadomo, że rzutowanie zakończy się pomyślnie. Ponadto zaleca się, aby nie używać rzutowania w stylu języka C w kodzie C++/CX, ponieważ są one takie same jak **operatora reinterpret_cast**.

Kompilator i środowisko uruchomieniowe również wykonuje niejawne rzutowania — na przykład w operacjach pakowania, gdy typ wartości lub typ wbudowany są przekazane jako argumenty do metody, której typem parametru `Object^`jest. W teorii niejawne rzutowanie nigdy nie powinno spowodować wyjątku w czasie wykonywania; Jeśli kompilator nie może wykonać konwersji niejawnej, zgłasza błąd w czasie kompilacji.

Środowisko wykonawcze systemu Windows jest abstrakcją nad modelem COM, który używa kodów błędów HRESULT zamiast wyjątków. Ogólnie rzecz biorąc, [platforma:: InvalidCastException](../cppcx/platform-invalidcastexception-class.md) wskazuje błąd modelu COM niskiego poziomu wynoszący E_NOINTERFACE.

## <a name="static_cast"></a>static_cast

**Static_cast** jest sprawdzana w czasie kompilacji w celu ustalenia, czy istnieje relacja dziedziczenia między tymi dwoma typami. Rzutowanie powoduje błąd kompilatora, jeśli typy nie są powiązane.

**Static_cast** w klasie ref również powoduje, że sprawdzanie czasu wykonywania jest wykonywane. **Static_cast** w klasie ref może przekazać weryfikację czasu kompilacji, ale nadal kończy się niepowodzeniem w czasie wykonywania; w tym przypadku `Platform::InvalidCastException` jest zgłaszany. Ogólnie rzecz biorąc nie trzeba obsługiwać tych wyjątków, ponieważ niemal zawsze wskazują błędy programistyczne, które można wyeliminować podczas tworzenia i testowania.

Użyj **static_cast** , jeśli kod jawnie deklaruje relację między dwoma typami, i w związku z tym upewnij się, że rzutowanie powinno być wykonane.

```cpp
    interface class A{};
    public ref class Class1 sealed : A { };
    // ...
    A^ obj = ref new Class1(); // Class1 is an A
    // You know obj is a Class1. The compiler verifies that this is possible, and in C++/CX a run-time check is also performed.
    Class1^ c = static_cast<Class1^>(obj);
```

## <a name="safe_cast"></a>safe_cast

Operator **safe_cast** jest częścią środowisko wykonawcze systemu Windows. Wykonuje sprawdzanie typu w czasie wykonywania i zgłasza `Platform::InvalidCastException` , jeśli konwersja nie powiedzie się. Użyj **safe_cast** , gdy błąd czasu wykonywania wskazuje na wyjątkowe warunki. Głównym celem **safe_cast** jest pomaganie zidentyfikować błędy programowania w fazach tworzenia i testowania w momencie ich wystąpienia. Nie musisz obsługiwać wyjątku, ponieważ nieobsłużony wyjątek identyfikuje punkt awarii.

Użyj safe_cast, jeśli kod nie deklaruje relacji, ale masz pewność, że rzutowanie powinno być wykonane.

```cpp
    // A and B are not related
    interface class A{};
    interface class B{};
    public ref class Class1 sealed : A, B { };
    // ...
    A^ obj = ref new Class1();

    // You know that obj’s backing type implements A and B, but
    // the compiler can’t tell this by comparing A and B. The run-time type check succeeds.
    B^ obj2 = safe_cast<B^>(obj);
```

## <a name="dynamic_cast"></a>dynamic_cast

Użyj **dynamic_cast** podczas rzutowania obiektu (dokładniej, Hat **^** ) na bardziej pochodny typ, spodziewasz się, że obiekt docelowy może być czasami **nullptr** lub że rzutowanie może się nie powieść i chcesz obsłużyć ten warunek jako zwykła ścieżka kodu zamiast wyjątku. Na przykład w szablonie projektu **pusta aplikacja (uniwersalna systemu Windows)** `OnLaunched` Metoda w aplikacji App. XAMP. cpp używa **dynamic_cast** , aby sprawdzić, czy okno aplikacji ma zawartość. Nie jest to błąd, jeśli nie ma zawartości; jest to oczekiwany warunek. `Windows::Current::Content`to a i konwersja to `Windows::UI.XAML::Controls::Frame`, który jest bardziej pochodnym typem w hierarchii dziedziczenia. `Windows::UI::XAML::UIElement`

```cpp
void App::OnLaunched(Windows::ApplicationModel::Activation::LaunchActivatedEventArgs^ args)
{
    auto rootFrame = dynamic_cast<Frame^>(Window::Current->Content);

    // Do not repeat app initialization when the window already has content,
    // just ensure that the window is active
    if (rootFrame == nullptr)
    {
        // Create a Frame to act as the navigation context and associate it with
        // a SuspensionManager key
        rootFrame = ref new Frame();
        // ...
    }
}
```

Innym wykorzystaniem **dynamic_cast** jest sondowanie `Object^` w celu ustalenia, czy zawiera on opakowany typ wartości. W takim przypadku próbka `dynamic_cast<Platform::Box>` `dynamic_cast<Platform::IBox>`lub.

## <a name="dynamic_cast-and-tracking-references-"></a>odwołania dynamic_cast i śledzące (%)

Można również zastosować **dynamic_cast** do odwołania śledzenia, ale w tym przypadku rzutowanie zachowuje się jak **safe_cast**. Zgłasza `Platform::InvalidCastException` błąd, ponieważ odwołanie śledzące nie może mieć wartości **nullptr**.

## <a name="reinterpret_cast"></a>reinterpret_cast

Nie zaleca się używania [operatora reinterpret_cast](../cpp/reinterpret-cast-operator.md) , ponieważ nie jest wykonywane sprawdzanie czasu kompilacji ani sprawdzanie czasu wykonywania. W najgorszym przypadku, funkcja **reinterpret_cast** umożliwia programowanie błędów, które nie zostały wykryte w czasie projektowania i powoduje drobne lub katastrofalne błędy w zachowaniu programu. W związku z tym zaleca się używanie **operatora reinterpret_cast** tylko w tych rzadkich przypadkach, gdy trzeba rzutować między niepowiązanymi typami i wiadomo, że rzutowanie zakończy się pomyślnie. Przykładem rzadkich użycia jest przekonwertowanie typu środowisko wykonawcze systemu Windows na jego podstawowy typ ABI. oznacza to, że przejęcie kontroli nad zliczaniem odwołań dla obiektu. W tym celu zalecamy użycie inteligentnego wskaźnika [klasy ComPtr](../cpp/com-ptr-t-class.md) . W przeciwnym razie należy wywołać Release w interfejsie. Poniższy przykład pokazuje, jak Klasa ref może być rzutowana na `IInspectable*`.

```cpp
#include <wrl.h>
using namespace Microsoft::WRL;
auto winRtObject = ref new SomeWinRTType();
ComPtr<IInspectable> inspectable = reinterpret_cast<IInspectable*>(winRtObject);
// ...
```

Jeśli używasz **operatora reinterpret_cast** do konwersji z interfejsu środowiska uruchomieniowego oneWindows na inny, spowoduje to dwukrotne wydanie obiektu. W związku z tym używaj tego rzutowania tylko podczas konwertowania na interfejs rozszerzeńC++ nieskładnikowych.

## <a name="abi-types"></a>Typy ABI

- ABI typy na żywo w nagłówkach w Windows SDK. Wygodnie nagłówki są nazwane po przestrzeni nazw — na przykład `windows.storage.h`.

- ABI typy na żywo w specjalnej przestrzeni nazw ABI — na przykład `ABI::Windows::Storage::Streams::IBuffer*`.

- Konwersje między typem interfejsu środowisko wykonawcze systemu Windows i jego odpowiednikiem ABI są zawsze bezpieczne — to znaczy, `IBuffer^` do. `ABI::IBuffer*`

- Klasa środowiska uruchomieniowego środowisko wykonawcze systemu Windows powinna zawsze być konwertowana `IInspectable*` do interfejsu domyślnego lub jego domyślny interfejs, jeśli jest znany.

- Po przeprowadzeniu konwersji do typów ABI należy posiadać okres istnienia typu i musi on być zgodny z regułami modelu COM. Zalecamy korzystanie `WRL::ComPtr` z programu w celu uproszczenia zarządzania wskaźnikami ABI.

Poniższa tabela zawiera podsumowanie przypadków bezpiecznego używania **operatora reinterpret_cast**. W każdym przypadku Rzutowanie jest bezpieczne w obu kierunkach.

|||
|-|-|
|`HSTRING`|`String^`|
|`HSTRING*`|`String^*`|
|`IInspectable*`|`Object^`|
|`IInspectable**`|`Object^*`|
|`IInspectable-derived-type*`|`same-interface-from-winmd^`|
|`IInspectable-derived-type**`|`same-interface-from-winmd^*`|
|`IDefault-interface-of-RuntimeClass*`|`same-RefClass-from-winmd^`|
|`IDefault-interface-of-RuntimeClass**`|`same-RefClass-from-winmd^*`|

## <a name="see-also"></a>Zobacz także

- [System typów](../cppcx/type-system-c-cx.md)
- [Dokumentacja języka C++/CX](../cppcx/visual-c-language-reference-c-cx.md)
- [Dokumentacja przestrzeni nazw](../cppcx/namespaces-reference-c-cx.md)
