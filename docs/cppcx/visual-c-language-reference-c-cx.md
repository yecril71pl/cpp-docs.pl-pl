---
title: Dokumentacja języka C++/CX
ms.date: 09/15/2017
ms.assetid: 3f6abf92-4e5e-4ed8-8e11-f9252380d30a
ms.openlocfilehash: 4f3816280630a6a061eb037a33367ef4e9d90375
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/15/2020
ms.locfileid: "86403858"
---
# <a name="ccx-language-reference"></a>Dokumentacja języka C++/CX

C++/CX to zestaw rozszerzeń języka C++, które umożliwiają tworzenie aplikacji systemu Windows i środowisko wykonawcze systemu Windows składników w idiom, który jest możliwie blisko nowoczesnego języka C++. Za pomocą języka C++/CX zapisuj aplikacje i składniki systemu Windows w kodzie natywnym, które łatwo współpracują z językami Visual C#, Visual Basic i JavaScript oraz innymi językami, które obsługują środowisko wykonawcze systemu Windows. W tych rzadkich przypadkach, które wymagają bezpośredniego dostępu do nieprzetworzonych interfejsów COM lub niewyjątkowego kodu, można użyć [środowisko wykonawcze systemu Windows biblioteki szablonów C++ (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md).

> [!NOTE]
> Język ** [c++/WinRT](/windows/uwp/cpp-and-winrt-apis/index) jest zalecaną alternatywą dla języka c++/CX**. Jest to nowy, standardowy Standard języka C++ 17 dla środowisko wykonawcze systemu Windows interfejsów API, dostępny w najnowszym zestawie SDK systemu Windows 10 w wersji 1803. Język C++/WinRT jest implementowany całkowicie w plikach nagłówkowych i zaprojektowany w celu zapewnienia pierwszej klasy dostępu do nowoczesnego interfejsu API systemu Windows.
>
> Za pomocą języka C++/WinRT można zarówno używać interfejsów API, jak i tworzyć ich środowisko wykonawcze systemu Windows za pomocą dowolnych zgodnych ze standardami kompilatorów języka C++ 17. C++/WinRT zazwyczaj wykonuje lepsze i tworzy mniejsze pliki binarne niż każda inna opcja języka dla środowisko wykonawcze systemu Windows. Będziemy nadal obsługiwać C++/CX i WRL, ale zdecydowanie zaleca się, aby nowe aplikacje korzystały z języka C++/WinRT. Aby uzyskać więcej informacji, zobacz [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/index).

Za pomocą języka C++/CX można tworzyć:

- Aplikacje C++ platforma uniwersalna systemu Windows (platformy UWP), które używają języka XAML do definiowania interfejsu użytkownika i używania stosu natywnego. Aby uzyskać więcej informacji, zobacz [Tworzenie aplikacji "Hello World" w języku C++ (platformy UWP)](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp).

- Składniki języka C++ środowisko wykonawcze systemu Windows, które mogą być używane przez aplikacje systemu Windows oparte na języku JavaScript. Aby uzyskać więcej informacji, zobacz [Tworzenie składników Środowisko wykonawcze systemu Windows w języku C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp).

- Gry Windows DirectX i aplikacje intensywnie korzystające z grafiki. Aby uzyskać więcej informacji, zobacz [Tworzenie prostej gry platformy UWP z DirectX](/windows/uwp/gaming/tutorial--create-your-first-uwp-directx-game).

## <a name="related-articles"></a>Pokrewne artykuły:

| Link | Opis |
|--|--|
| [Krótki przewodnik](../cppcx/quick-reference-c-cx.md) | Tabela słów kluczowych i operatorów dla C++/CX. |
| [System typów](../cppcx/type-system-c-cx.md) | Opisuje podstawowe typy/CX języka C++ i konstrukcje programistyczne oraz sposób używania języka C++/CX do użycia i tworzenia typów środowisko wykonawcze systemu Windows. |
| [Kompilowanie aplikacji i bibliotek](../cppcx/building-apps-and-libraries-c-cx.md) | W tym artykule omówiono sposób użycia środowiska IDE do kompilowania aplikacji i linków do bibliotek statycznych i bibliotek DLL. |
| [Współdziałanie z innymi językami](../cppcx/interoperating-with-other-languages-c-cx.md) | W tym artykule omówiono sposób, w jaki składniki, które są zapisywane przy użyciu języka C++/CX, mogą być używane ze składnikami, które są zapisywane w języku JavaScript, dowolnego języka zarządzanego lub w bibliotece szablonów języka C++ środowisko wykonawcze systemu Windows. |
| [Wątkowość i kierowanie](../cppcx/threading-and-marshaling-c-cx.md) | W tym artykule omówiono sposób określania zachowania wątkowości i organizowania utworzonych składników. |
| [Dokumentacja przestrzeni nazw](../cppcx/namespaces-reference-c-cx.md) | Dokumentacja referencyjna dla domyślnej przestrzeni nazw, przestrzeń nazw platformy, platforma:: Kolekcje i powiązane przestrzenie nazw. |
| [Funkcje CRT nie są obsługiwane w aplikacjach platformy uniwersalnej systemu Windows](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) | Wyświetla listę funkcji CRT, które nie są dostępne do użycia w aplikacjach środowisko wykonawcze systemu Windows. |
| [Wprowadzenie do aplikacji systemu Windows 10](/windows/uwp/get-started/) | Zawiera ogólne wskazówki dotyczące aplikacji systemu Windows 10 i linki do dodatkowych informacji. |
| [C++/CX — część 0 z \[ n \] : wprowadzenie](https://devblogs.microsoft.com/cppblog/ccx-part-0-of-n-an-introduction/)<br /><br />[C++/CX część 1 z \[ n \] : prosta Klasa](https://devblogs.microsoft.com/cppblog/ccx-part-1-of-n-a-simple-class/)<br /><br />[C++/CX — część 2 of \[ n \] : typy, które zużywają systemy](https://devblogs.microsoft.com/cppblog/ccx-part-2-of-n-types-that-wear-hats/)<br /><br />[C++/CX, część 3 z \[ n \] : w konstrukcji](https://devblogs.microsoft.com/cppblog/ccx-part-3-of-n-under-construction/)<br /><br />[C++/CX część 4 of \[ n \] : statyczne funkcje członkowskie](https://devblogs.microsoft.com/cppblog/ccx-part-4-of-n-static-member-functions/)| Wstępna seria blogów w języku C++/CX. |
