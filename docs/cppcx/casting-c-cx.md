---
title: Rzutowanie (C++/CX)
ms.date: 06/19/2018
ms.assetid: 5247f6c7-6a0a-4021-97c9-21c868bd9455
ms.openlocfilehash: 65d489d14c91b462e5a2bbe8bd60fce2657904a7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62258216"
---
# <a name="casting-ccx"></a>Rzutowanie (C++/CX)

Cztery operatory rzutowania różnych dotyczą typów środowiska wykonawczego Windows: [static_cast Operator](../cpp/static-cast-operator.md), [dynamic_cast Operator](../cpp/dynamic-cast-operator.md), **operatora safe_cast**, i [ reinterpret_cast Operator](../cpp/reinterpret-cast-operator.md). **safe_cast** i **static_cast** zgłoszenie wyjątku, gdy nie można wykonać konwersji; [static_cast Operator](../cpp/static-cast-operator.md) wykonuje sprawdzanie typów w czasie kompilacji. **dynamic_cast** zwraca **nullptr** ich powodzenia konwersji typu. Mimo że **reinterpret_cast** zwraca wartość inną niż null, być może jest ono nieprawidłowe. Z tego powodu zaleca się, że nie używasz **reinterpret_cast** Jeśli nie masz pewności, że rzutowanie zakończy się powodzeniem. Ponadto zalecamy nieużywanie rzutowań w stylu języka C w swojej C++/CX kodu, ponieważ są one identyczne **reinterpret_cast**.

Kompilator i środowisko uruchomieniowe również wykonywać rzutowania niejawnego — na przykład w konwersja boxing operacji, gdy typ wartości lub wbudowany typ są przekazywane jako argumenty do metody, której parametr typu jest `Object^`. Teoretycznie niejawne rzutowanie nigdy nie powinna spowodować wyjątek w czasie wykonywania. Jeśli kompilator nie można wykonać niejawnej konwersji, zgłasza błąd w czasie kompilacji.

Środowisko uruchomieniowe Windows jest klasą abstrakcyjną za pośrednictwem modelu COM, używający HRESULT kodów błędów zamiast wyjątków. Ogólnie rzecz biorąc [Platform::InvalidCastException](../cppcx/platform-invalidcastexception-class.md) wskazuje niskiego poziomu błędu modelu COM z E_NOINTERFACE.

## <a name="staticcast"></a>static_cast

A **static_cast** jest sprawdzany w czasie kompilacji, aby ustalić, czy jest relacji dziedziczenia między dwoma typami. Rzutowanie powoduje błąd kompilatora, jeśli typy nie są powiązane.

A **static_cast** parametrami "ref" klasy również powoduje, że sprawdzanie w czasie wykonania do wykonania. A **static_cast** parametrami "ref" klasy można przekazać weryfikacji czasu kompilacji, ale nadal się nie powieść w czasie wykonywania; w tym przypadku `Platform::InvalidCastException` zgłaszany. Ogólnie rzecz biorąc nie trzeba obsługiwać te wyjątki, ponieważ prawie zawsze wskazują błędy programowania, które możesz wyeliminować podczas opracowywania i testowania.

Użyj **static_cast** Jeśli kod deklaruje jawnie relacji między tymi dwoma typami, a zatem masz pewność, że rzutowanie powinny działać.

```cpp
    interface class A{};
    public ref class Class1 sealed : A { };
    // ...
    A^ obj = ref new Class1(); // Class1 is an A
    // You know obj is a Class1. The compiler verifies that this is possible, and in C++/CX a run-time check is also performed.
    Class1^ c = static_cast<Class1^>(obj);
```

## <a name="safecast"></a>safe_cast

**Safe_cast** operator jest częścią środowiska wykonawczego Windows. Przeprowadza sprawdzanie typu run-time i zgłasza `Platform::InvalidCastException` Jeśli konwersja nie powiedzie się. Użyj **safe_cast** kiedy wskazuje wyjątkowy warunek, błąd czasu wykonywania. Głównym celem **safe_cast** mają na celu ułatwienie identyfikacji błędy programowania podczas opracowywania i testowania fazy w punkcie, w którym wystąpią. Nie trzeba obsłużyć wyjątek, ponieważ nieobsługiwany wyjątek, sama identyfikuje punkt awarii.

Korzystanie z polecenia safe_cast, jeśli kod nie deklaruje relacji, ale masz pewność, że rzutowanie powinny działać.

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

## <a name="dynamiccast"></a>dynamic_cast

Użyj **dynamic_cast** Jeśli zrzutować obiektu (w szczególności hat **^**) do typu bardziej pochodnego oczekujesz, że element docelowy obiekt czasami może być **nullptr** lub Rzutowanie może zakończyć się niepowodzeniem, a chcesz obsługiwać ten warunek jako ścieżka kodu regularnego zamiast wyjątku. Na przykład w **pusta aplikacja (Windows Universal)** szablonu projektu `OnLaunched` metody w zastosowaniach app.xamp.cpp **dynamic_cast** do sprawdzenia, czy zawartość jest okna aplikacji. Nie jest błąd, jeśli nie ma zawartości; jest oczekiwany warunek. `Windows::Current::Content` jest `Windows::UI::XAML::UIElement` i konwersji `Windows::UI.XAML::Controls::Frame`, który jest bardziej pochodnego typu w hierarchii dziedziczenia.

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

Używanie innego **dynamic_cast** jest badanie `Object^` do określenia, czy zawiera on opakowanym typem wartościowym. W tym przypadku próba `dynamic_cast<Platform::Box>` lub `dynamic_cast<Platform::IBox>`.

## <a name="dynamiccast-and-tracking-references-"></a>dynamic_cast i śledzenie odwołania (%)

Można również zastosować **dynamic_cast** do odwołania śledzenia, ale w tym przypadku rzutowania zachowuje się jak **safe_cast**. Wyniku weryfikacji zgłasza wyjątek `Platform::InvalidCastException` w przypadku niepowodzenia ponieważ odwołania śledzenia nie może mieć wartość **nullptr**.

## <a name="reinterpretcast"></a>reinterpret_cast

Firma Microsoft zaleca, aby używać [reinterpret_cast](../cpp/reinterpret-cast-operator.md) ponieważ jest wykonywane sprawdzanie w czasie kompilacji ani sprawdzanie w czasie wykonania. W najgorszym przypadku **reinterpret_cast** umożliwia programowanie błędy, aby niezauważona w czasie tworzenia i spowodować błędy subtelne lub krytyczny w zachowanie programu. Dlatego zaleca się używanie **reinterpret_cast** tylko w tych rzadkich przypadkach, gdy należy rzutować między typami niepowiązanych i wiesz, że rzutowanie zakończy się powodzeniem. Przykładem użycia rzadko jest konwersja typu środowiska uruchomieniowego Windows na jej typ podstawowy ABI — oznacza to, że trwa kontrolę nad Zliczanie dla obiektu. Aby to zrobić, zaleca się, że używasz [comptr — klasa](../cpp/com-ptr-t-class.md) inteligentnego wskaźnika. W przeciwnym razie w szczególności należy wywołać wydania w interfejsie. W poniższym przykładzie pokazano, jak klasa ref mogą być rzutowane na `IInspectable*`.

```cpp
#include <wrl.h>
using namespace Microsoft::WRL;
auto winRtObject = ref new SomeWinRTType();
ComPtr<IInspectable> inspectable = reinterpret_cast<IInspectable*>(winRtObject);
// ...
```

Jeśli używasz **reinterpret_cast** do konwersji z interfejsu środowiska wykonawczego oneWindows do innego, powoduje, że obiekt, które mogą być wprowadzane na dwa razy. W związku z tym używać tylko to rzutowanie podczas konwertowania interfejsu rozszerzenia składnika C++ inny niż Visual.

## <a name="abi-types"></a>Typy interfejsu ABI

- Typy interfejsu ABI na żywo w nagłówkach w zestawie Windows SDK. Wygodne nagłówki są nazwane jego imieniem przestrzenie nazw — na przykład `windows.storage.h`.

- Typy interfejsu ABI na żywo w specjalne nazw interfejsu ABI — na przykład `ABI::Windows::Storage::Streams::IBuffer*`.

- Konwersje między typem interfejs Windows Runtime i typu interfejsu ABI równoważne są zawsze bezpieczne — czyli `IBuffer^` do `ABI::IBuffer*`.

- Klasy środowiska wykonawczego Windows Runtime zawsze powinny być konwertowane na `IInspectable*` lub jego domyślny interfejs, który jest znany.

- Po konwersji na typy interfejsu ABI własny okres istnienia tego typu i musi być zgodne z regułami modelu COM. Firma Microsoft zaleca użycie `WRL::ComPtr` do uproszczenia zarządzania okresem istnienia wskaźniki interfejsu ABI.

Poniższa tabela zawiera podsumowanie przypadki, w których jest bezpieczny w użyciu **reinterpret_cast**. W każdym przypadku rzutowanie jest bezpieczny w obu kierunkach.

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
- [Dokumentacja języka Visual C++](../cppcx/visual-c-language-reference-c-cx.md)
- [Dokumentacja przestrzeni nazw](../cppcx/namespaces-reference-c-cx.md)
