---
title: Rzutowanie (C + +/ CX) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 5247f6c7-6a0a-4021-97c9-21c868bd9455
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5e16aacdf713d1f9ff2b40532abfd2b5d6316f7a
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="casting-ccx"></a>Rzutowanie (C + +/ CX)
Cztery operatory rzutowania różnych dotyczą typów środowiska wykonawczego systemu Windows: [static_cast Operator](../cpp/static-cast-operator.md), [dynamic_cast Operator](../cpp/dynamic-cast-operator.md), **operatora safe_cast**, i [ reinterpret_cast Operator](../cpp/reinterpret-cast-operator.md). `safe_cast` i `static_cast` zgłosić wyjątek, gdy nie można wykonać konwersji; [static_cast Operator](../cpp/static-cast-operator.md) oraz wykonuje sprawdzanie typów w czasie kompilacji. `dynamic_cast` Zwraca `nullptr` Jeżeli nie Konwertuj typu. Mimo że `reinterpret_cast` zwraca wartość inną niż null, może być nieprawidłowy. Z tego powodu zaleca się, że nie używasz `reinterpret_cast` chyba że rzutowanie powiedzie się. Ponadto zaleca się nie używać rzutowania w stylu języka C w języku C + +/ CX kodu, ponieważ są one takie same jak `reinterpret_cast`.  
  
 Kompilator i środowiska uruchomieniowego również wykonywać niejawnego rzutowania — na przykład w konwersja boxing operacji, gdy typ wartości lub typ wbudowany są przekazywane jako argumenty do metody którego parametr typu jest `Object^`. Teoretycznie niejawne rzutowanie nigdy nie powinno powodować Wystąpił wyjątek w czasie wykonywania. Jeśli kompilator nie można wykonać niejawnej konwersji, zgłasza błąd w czasie kompilacji.  
  
Środowisko wykonawcze systemu Windows jest abstrakcji za pośrednictwem modelu COM, używający kody błędów HRESULT zamiast wyjątki. Ogólnie rzecz biorąc [Platform::InvalidCastException](../cppcx/platform-invalidcastexception-class.md) wskazuje niskiego poziomu błąd COM z E_NOINTERFACE.  
  
## <a name="staticcast"></a>static_cast  
 A `static_cast` zaznaczono w czasie kompilacji, aby ustalić, czy jest relację dziedziczenia między tymi dwoma typami. Rzutowanie powoduje błąd kompilatora w przypadku typów nie są powiązane.  
  
 A `static_cast` na ref klasy powoduje także, że kontrola czasu wykonywania do wykonania. A `static_cast` na ref klasy można przekazać weryfikacji czasu kompilacji, ale nadal się nie powieść w czasie wykonywania; w takim przypadku `Platform::InvalidCastException` jest generowany. Ogólnie rzecz biorąc nie trzeba obsłużyć te wyjątki, ponieważ prawie zawsze wskazują one programowania błędów, które można wyeliminować podczas projektowania i testowania.  
  
 Użyj `static_cast` Jeśli kod deklaruje jawnie relacji między tymi dwoma typami, a zatem masz pewność, że rzutowanie powinny działać.  
  
```
    interface class A{};  
    public ref class Class1 sealed : A { };  
...  
    A^ obj = ref new Class1(); // Class1 is an A  
    // You know obj is a Class1. The compiler verifies that this is possible, and in C++/CX a run-time check is also performed.  
    Class1^ c = static_cast<Class1^>(obj);
```  
  
## <a name="safecast"></a>safe_cast  
 `safe_cast` Operator jest ofWindows części środowiska wykonawczego. Przeprowadza sprawdzanie typu run-time i zgłasza `Platform::InvalidCastException` Jeśli konwersji nie powiedzie się. Użyj `safe_cast` gdy błąd czasu wykonywania określa warunek wyjątkowych. Głównym celem `safe_cast` jest zidentyfikować programowania błędy podczas opracowywania i testowania fazy w momencie, w którym występują. Nie masz do obsługi wyjątku, ponieważ nieobsługiwany wyjątek, sama identyfikuje punkt awarii.  
  
 Korzystanie z polecenia safe_cast, jeśli kod nie deklaruje relacji, ale masz pewność, że rzutowanie powinny działać.  
  
```  
    // A and B are not related  
    interface class A{};  
    interface class B{};  
    public ref class Class1 sealed : A, B { };  
...  
    A^ obj = ref new Class1();  
  
    // You know that obj’s backing type implements A and B, but  
    // the compiler can’t tell this by comparing A and B. The run-time type check succeeds.  
    B^ obj2 = safe_cast<B^>(obj);  
```  
  
## <a name="dynamiccast"></a>dynamic_cast  
 Użyj `dynamic_cast` przypadku rzutowania obiektu (w szczególności hat `^`) do typu bardziej pochodnego przypuszczasz, że element docelowy obiekt czasami może być `nullptr` lub Rzutowanie może zakończyć się niepowodzeniem, którą chcesz obsługiwać tego warunku jako regularne kodu Ścieżka zamiast Wystąpił wyjątek. Na przykład w **pusta aplikacja (uniwersalna systemu Windows)** szablonu projektu `OnLaunched` metody w `app.xamp.cpp` używa `dynamic_cast` Aby sprawdzić, czy okno aplikacji ma zawartość. Nie jest błąd, jeśli nie ma zawartości; jest oczekiwany warunek. `Windows::Current::Content` jest `Windows::UI::XAML::UIElement` i konwersji `Windows::UI.XAML::Controls::Frame`, który jest bardziej pochodny typ w hierarchii dziedziczenia.  
```
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
...  
```  
 Użycie innego `dynamic_cast` jest badanie `Object^` ustalenie, czy zawiera on opakowanym typem wartościowym. W takim przypadku można spróbować `dynamic_cast<Platform::Box>` lub `dynamic_cast<Platform::IBox>`.  
  
 **dynamic_cast oraz śledzenie odwołań (%)**  
  
 Można także zastosować `dynamic_cast` odwołaniem śledzącym, ale w tym przypadku rzutowanie zachowuje się jak `safe_cast`. Zgłasza `Platform::InvalidCastException` na niepowodzenie, ponieważ odwołanie śledzenia nie może mieć wartości `nullptr`.  
  
## <a name="reinterpretcast"></a>reinterpret_cast  
 Firma Microsoft zaleca, aby nie używać [reinterpret_cast](../cpp/reinterpret-cast-operator.md) wyboru kompilacji ani wyboru czasu wykonywania nie jest wykonywana. W najgorszym przypadku `reinterpret_cast` umożliwia błędy wykryte w czasie opracowywania i spowodować błędy niewielkie lub krytyczny w zachowanie programu programowania. Dlatego zaleca się używanie `reinterpret_cast` tylko w tych rzadkich przypadkach, gdy należy rzutować między niepowiązanych typów i wiesz, że rzutowanie powiedzie się. Przykład użycia rzadkich jest konwersja aWindows typ środowiska uruchomieniowego na jego typem podstawowym ABI — to oznacza, że trwa kontrolę nad Zliczanie dla obiektu. Aby to zrobić, firma Microsoft zaleca się używanie [comptr — klasa](../cpp/com-ptr-t-class.md) wskaźnika inteligentnego. W przeciwnym razie w szczególności należy wywołać wersji w interfejsie. W poniższym przykładzie pokazano, jak można rzutować klasy ref `IInspectable*`.  
  
```  
#include <wrl.h>  
using namespace Microsoft::WRL;  
auto winRtObject = ref new SomeWinRTType();  
ComPtr<IInspectable> inspectable = reinterpret_cast<IInspectable*>(winRtObject);  
...
```  
  
 Jeśli używasz `reinterpret_cast` Aby przekonwertować się z interfejsu środowiska wykonawczego oneWindows, powoduje, że obiekt do zwolnienia dwa razy. W związku z tym używać tylko tego rzutowania podczas konwertowania niż[!INCLUDE[cppwrt](../cppcx/includes/cppwrt-md.md)] interfejsu.  
  
 **Typy ABI**  
  
-   Typy ABI na żywo w nagłówkach w zestawie Windows SDK. Wygodnie nagłówki są nazywane po przestrzenie nazw — na przykład `windows.storage.h`.  
  
-   Typy ABI na żywo w przestrzeni nazw specjalne ABI — na przykład `ABI::Windows::Storage::Streams::IBuffer*`.  
  
-   Konwersje między typem interfejsu środowiska wykonawczego aWindows i jego odpowiednik typu ABI zawsze są bezpieczne — to znaczy `IBuffer^` do `ABI::IBuffer*`.  
  
-   Klasa czasu wykonywania AWindows środowiska uruchomieniowego zawsze powinny być konwertowane na `IInspectable*` lub jego domyślny interfejs, jeśli wiadomo, że.  
  
-   Po konwersji na typy ABI właścicielem okres istnienia typu i musi być zgodne z regułami modelu COM. Firma Microsoft zaleca użycie `WRL::ComPtr` Aby uprościć zarządzanie okresem istnienia ABI wskaźników.  
  
 W poniższej tabeli przedstawiono przypadki, w których jest bezpiecznie korzystać `reinterpret_cast`. W każdym przypadku rzutowanie jest bezpieczne w obu kierunkach.  
  
|||  
|-|-|  
|HSTRING|String^|  
|HSTRING *|String^*|  
|IInspectable *|Obiekt ^|  
|IInspectable**|Obiekt ^ *|  
|IInspectable-pochodnych — typ *|same-interface-from-winmd^|  
|IInspectable-derived-type**|same-interface-from-winmd^*|  
|IDefault-interface-of-RuntimeClass*|same-RefClass-from-winmd^|  
|IDefault-interface-of-RuntimeClass**|same-RefClass-from-winmd^*|  
  
## <a name="see-also"></a>Zobacz też  
 [System typów](../cppcx/type-system-c-cx.md)   
 [Dokumentacja języka Visual C++](../cppcx/visual-c-language-reference-c-cx.md)   
 [Odwołanie do przestrzeni nazw](../cppcx/namespaces-reference-c-cx.md)
