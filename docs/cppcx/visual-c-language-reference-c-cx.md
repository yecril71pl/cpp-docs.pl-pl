---
title: Wizualne C++ Language Reference (C++/CX)
ms.date: 09/15/2017
ms.assetid: 3f6abf92-4e5e-4ed8-8e11-f9252380d30a
ms.openlocfilehash: ce0272499b653b9077a891e39e9b29797e7e051d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384949"
---
# <a name="visual-c-language-reference-ccx"></a>Wizualne C++ Language Reference (C++/CX)

C++/CX to zbiór rozszerzenia C++ języka, które umożliwiają tworzenie aplikacji Windows i składników środowiska wykonawczego Windows w idiom, który jest możliwie jak najbardziej zbliżone do nowoczesnego C++. Użyj C++/CX do pisania aplikacji Windows i składników w trybie macierzystym kod, który łatwo interakcji z wizualizacją C#, Visual Basic i języków JavaScript i inne języki, które obsługują środowiska wykonawczego Windows. W tych rzadkich przypadkach, które wymagają bezpośredniego dostępu do surowego interfejsów COM lub kod bez wyjątków, można użyć [Windows środowiska uruchomieniowego C++ szablon biblioteki (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md).

> [!NOTE]
> **[C++/ WinRT](/windows/uwp/cpp-and-winrt-apis/index) jest zalecaną alternatywą C++/CX**. To nowe, standard C ++ 17 języka projekcji Windows Runtime interfejsów API, dostępne w najnowszy zestaw Windows 10 SDK z wersji 1803 wartości. C++/ WinRT jest zaimplementowana w całości w plikach nagłówkowych i przeznaczone do zapewnia najwyższej jakości dostęp do nowoczesnego interfejsu Windows API.
>
> Za pomocą C++/WinRT, można używać lub Tworzenie interfejsów API środowiska wykonawczego Windows przy użyciu dowolnej zgodnych ze standardami języka C ++ 17 kompilatora. C++/ WinRT zazwyczaj działa lepiej, a także generuje mniejsze pliki binarne niż innych opcji języka dla środowiska wykonawczego Windows. Firma Microsoft będzie obsługiwać C++/CX i WRL, ale zdecydowanie zaleca się, że nowe aplikacje używają C++/WinRT. Aby uzyskać więcej informacji, zobacz [ C++/WinRT](/windows/uwp/cpp-and-winrt-apis/index).

Za pomocą C++/CX, można utworzyć:

- Aplikacje C++ Universal Windows Platform (UWP), które umożliwiają definiowanie użytkownika XAML interfejs i korzystanie z natywnych stosu. Aby uzyskać więcej informacji, zobacz [Utwórz aplikację "hello world" w języku C++ (UWP)](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp).

- Składniki środowiska uruchomieniowego Windows C++, które mogą być używane przez aplikacje Windows oparte na języku JavaScript. Aby uzyskać więcej informacji, zobacz [Tworzenie składników środowiska wykonawczego Windows w języku C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp).

- Gry Windows DirectX i aplikacji intensywnie korzystających z grafiki. Aby uzyskać więcej informacji, zobacz [Tworzenie prostej grze platformy uniwersalnej systemu Windows przy użyciu technologii DirectX](/windows/uwp/gaming/tutorial--create-your-first-uwp-directx-game).

## <a name="related-articles"></a>Pokrewne artykuły:

|||
|-|-|
|[Krótki przewodnik](../cppcx/quick-reference-c-cx.md)|Tabela słów kluczowych i operatory C++/CX.|
|[System typów](../cppcx/type-system-c-cx.md)|W tym artykule opisano podstawowe C++/CX typów i narzędzi programistycznych oraz sposób wykorzystywania C++/CX, używanie i tworzenie typów środowiska wykonawczego Windows.|
|[Tworzenie aplikacji i bibliotek](../cppcx/building-apps-and-libraries-c-cx.md)|W tym artykule omówiono sposób używania środowiska IDE Twórz aplikacje i połączyć z bibliotek statycznych i bibliotek DLL.|
|[Współdziałanie z innymi językami](../cppcx/interoperating-with-other-languages-c-cx.md)|W tym artykule omówiono sposób składniki, które są tworzone za pomocą C++/CX mogą być używane ze składnikami, które zostały napisane w języku JavaScript, zarządzane dowolnego języka lub środowiska uruchomieniowego Windows C++ biblioteki szablonów.|
|[Wątkowość i marshaling](../cppcx/threading-and-marshaling-c-cx.md)|W tym artykule omówiono sposób określania zachowania wątkowości i organizowania składników, które tworzysz.|
|[Dokumentacja przestrzeni nazw](../cppcx/namespaces-reference-c-cx.md)|Dokumentacja dotycząca domyślny obszar nazw, przestrzeń nazw platformy, Platform::Collections i pokrewne obszary nazw.|
|[Funkcje CRT nie są obsługiwane w aplikacjach platformy uniwersalnej systemu Windows](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)|Wyświetla listę funkcji CRT, które nie są dostępne do użycia w aplikacjach Windows Runtime.|
|[Przewodniki z instrukcjami dla aplikacji systemu Windows 10](https://msdn.microsoft.com/library/windows/apps/xaml/mt244352.aspx)|Zawiera ogólne wskazówki na temat aplikacji systemu Windows 10 i linki do szczegółowych informacji.|
|[C++/CX część 0 \[n\]: Wprowadzenie](https://blogs.msdn.microsoft.com/vcblog/2012/08/29/ccx-part-0-of-n-an-introduction/)<br /><br />[C++/CX, część 1 z \[n\]: Proste klasy](https://blogs.msdn.microsoft.com/vcblog/2012/09/05/ccx-part-1-of-n-a-simple-class/)<br /><br />[C++/CX część 2 \[n\]: Typy, które systemy Wear](https://blogs.msdn.microsoft.com/vcblog/2012/09/17/ccx-part-2-of-n-types-that-wear-hats/)<br /><br />[C++/CX część 3 \[n\]: W trakcie tworzenia](https://blogs.msdn.microsoft.com/vcblog/2012/10/05/ccx-part-3-of-n-under-construction/)<br /><br />[C++/CX część 4 \[n\]: Statyczne funkcje Członkowskie](https://blogs.msdn.microsoft.com/vcblog/2012/10/19/ccx-part-4-of-n-static-member-functions/)|Wprowadzające Visual C++ serię wpisów w blogu na C++/CX.|
