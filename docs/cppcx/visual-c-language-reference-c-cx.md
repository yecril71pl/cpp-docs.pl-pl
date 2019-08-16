---
title: Odwołanie C++ do języka wizualnego (C++/CX)
ms.date: 09/15/2017
ms.assetid: 3f6abf92-4e5e-4ed8-8e11-f9252380d30a
ms.openlocfilehash: 0b2d344f9889d5669164cd917ba569b5f35d83a5
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498426"
---
# <a name="visual-c-language-reference-ccx"></a>Odwołanie C++ do języka wizualnego (C++/CX)

C++/CX to zestaw rozszerzeń C++ języka, który umożliwia tworzenie aplikacji systemu Windows i składników Środowisko wykonawcze systemu Windows w idiom, które są możliwie jak najbardziej zbliżone do nowoczesnej. C++ Za C++pomocą/CX zapisuj aplikacje i składniki systemu Windows w kodzie natywnym, które łatwo C#współpracują z wizualizacjami, Visual Basic i JavaScript oraz innymi językami, które obsługują środowisko wykonawcze systemu Windows. W tych rzadkich przypadkach, które wymagają bezpośredniego dostępu do nieprzetworzonych interfejsów COM lub niewyjątkowego kodu, można użyć [biblioteki C++ szablonów środowisko wykonawcze systemu Windows (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md).

> [!NOTE]
> **/WinRT jest zalecaną alternatywą C++dla/CX. [ C++](/windows/uwp/cpp-and-winrt-apis/index) Jest to nowy, standardowy Standard języka C++ 17 dla środowisko wykonawcze systemu Windows interfejsów API, dostępny w najnowszym zestawie SDK systemu Windows 10 w wersji 1803. C++/WinRT jest zaimplementowana całkowicie w plikach nagłówkowych i zaprojektowana w celu zapewnienia pierwszej klasy dostępu do nowoczesnego interfejsu API systemu Windows.
>
> Dzięki C++/WinRT można korzystać z interfejsów api i środowisko wykonawcze systemu Windows tworzyć je za pomocą dowolnych zgodnych ze standardami kompilatorów języka c++ 17. C++/WinRT zazwyczaj wykonuje lepsze i produkuje mniejsze pliki binarne niż każda inna opcja języka dla środowisko wykonawcze systemu Windows. Będziemy nadal obsługiwać C++/CX i WRL, ale zdecydowanie zaleca się, aby nowe aplikacje korzystały C++z/WinRT. Aby uzyskać więcej informacji, zobacz [ C++/WinRT](/windows/uwp/cpp-and-winrt-apis/index).

Za pomocą C++/CX, można utworzyć:

- C++Aplikacje platforma uniwersalna systemu Windows (platformy UWP) używające języka XAML do definiowania interfejsu użytkownika i używania stosu natywnego. Aby uzyskać więcej informacji, zobacz [Tworzenie aplikacji "Hello World" w C++ programie (platformy UWP)](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp).

- C++Składniki środowisko wykonawcze systemu Windows, które mogą być używane przez aplikacje systemu Windows oparte na języku JavaScript. Aby uzyskać więcej informacji, zobacz [Tworzenie składników Środowisko wykonawcze systemu Windows C++w programie ](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp).

- Gry Windows DirectX i aplikacje intensywnie korzystające z grafiki. Aby uzyskać więcej informacji, zobacz [Tworzenie prostej gry platformy UWP z DirectX](/windows/uwp/gaming/tutorial--create-your-first-uwp-directx-game).

## <a name="related-articles"></a>Pokrewne artykuły:

|||
|-|-|
|[Krótki przewodnik](../cppcx/quick-reference-c-cx.md)|Tabela słów kluczowych i operatorów dla C++/CX.|
|[System typów](../cppcx/type-system-c-cx.md)|Opisuje podstawowe C++typy/CX i konstrukcje programistyczne oraz sposób używania C++/CX do użycia i tworzenia typów środowisko wykonawcze systemu Windows.|
|[Tworzenie aplikacji i bibliotek](../cppcx/building-apps-and-libraries-c-cx.md)|W tym artykule omówiono sposób użycia środowiska IDE do kompilowania aplikacji i linków do bibliotek statycznych i bibliotek DLL.|
|[Współdziałanie z innymi językami](../cppcx/interoperating-with-other-languages-c-cx.md)|W tym artykule omówiono sposób, w jaki C++składniki, które są zapisywane przy użyciu/CX, mogą być używane ze składnikami, które są zapisywane C++ w języku JavaScript, dowolnego języka zarządzanego lub środowisko wykonawcze systemu Windows bibliotece szablonów.|
|[Wątkowość i marshaling](../cppcx/threading-and-marshaling-c-cx.md)|W tym artykule omówiono sposób określania zachowania wątkowości i organizowania utworzonych składników.|
|[Dokumentacja przestrzeni nazw](../cppcx/namespaces-reference-c-cx.md)|Dokumentacja referencyjna dla domyślnej przestrzeni nazw, przestrzeń nazw platformy, platforma:: Kolekcje i powiązane przestrzenie nazw.|
|[Funkcje CRT nie są obsługiwane w aplikacjach platformy uniwersalnej systemu Windows](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)|Wyświetla listę funkcji CRT, które nie są dostępne do użycia w aplikacjach środowisko wykonawcze systemu Windows.|
|[Wprowadzenie do aplikacji systemu Windows 10](/windows/uwp/get-started/)|Zawiera ogólne wskazówki dotyczące aplikacji systemu Windows 10 i linki do dodatkowych informacji.|
|[C++/CX część 0 z \[n\]: Wprowadzenie](https://blogs.msdn.microsoft.com/vcblog/2012/08/29/ccx-part-0-of-n-an-introduction/)<br /><br />[C++/CX część 1 z \[n\]: Prosta Klasa](https://blogs.msdn.microsoft.com/vcblog/2012/09/05/ccx-part-1-of-n-a-simple-class/)<br /><br />[C++/CX część 2 z \[n\]: Typy, które zużywają systemy](https://blogs.msdn.microsoft.com/vcblog/2012/09/17/ccx-part-2-of-n-types-that-wear-hats/)<br /><br />[C++/CX część 3 z \[n\]: W przygotowaniu](https://blogs.msdn.microsoft.com/vcblog/2012/10/05/ccx-part-3-of-n-under-construction/)<br /><br />[C++/CX część 4 z \[n\]: Statyczne funkcje członkowskie](https://blogs.msdn.microsoft.com/vcblog/2012/10/19/ccx-part-4-of-n-static-member-functions/)|Wstępna seria C++ blogów w C++programie/CX.|
