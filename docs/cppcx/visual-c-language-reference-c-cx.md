---
title: "Dokumentacja języka Visual C++ (C + +/ CX) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 09/15/2017
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3f6abf92-4e5e-4ed8-8e11-f9252380d30a
caps.latest.revision: "27"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3a0e7cba73d85253db28d719932d02cfb3cdecca
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="visual-c-language-reference-ccx"></a>Dokumentacja języka Visual C++ (C + +/ CX)

C + +/ CX to zestaw rozszerzeń dla języka C++, które umożliwiają tworzenie aplikacji systemu Windows i składników środowiska wykonawczego systemu Windows w idiom będący jak, jak to możliwe, aby modern C++. Użyj C + +/ CX do pisania aplikacji systemu Windows i składniki kodu natywnego, które łatwo interakcję z Visual C#, Visual Basic i JavaScript i innych języków, które obsługuje środowisko wykonawcze systemu Windows. W tych rzadkich przypadkach, które wymagają bezpośredniego dostępu do nieprzetworzonej interfejsy modelu COM lub innym kodem kodu, można użyć [Windows środowiska uruchomieniowego C++ szablonu biblioteki (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md).

Nowy model reprezentuje generacji natywnych języka C++ programowania w systemie Windows. Korzystając z niego, można utworzyć:

- C++ Windows platformy Uniwersalnej aplikacji, które umożliwiają definiowanie użytkownika XAML interfejsu i używać natywnego stosu. Aby uzyskać więcej informacji, zobacz [Utwórz aplikację "hello world" w języku C++ (UWP)](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp).

- Składniki C++ środowiska wykonawczego systemu Windows, które mogą być używane przez aplikacje oparte na języku JavaScript systemu Windows. Aby uzyskać więcej informacji, zobacz [tworzenia składników środowiska wykonawczego systemu Windows w języku C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp).

- Windows DirectX gier i aplikacji dużą ilością grafiki. Aby uzyskać więcej informacji, zobacz [Tworzenie prostego gry platformy uniwersalnej systemu Windows z DirectX](/windows/uwp/gaming/tutorial--create-your-first-metro-style-directx-game).

## <a name="related-articles"></a>Pokrewne artykuły

|||
|-|-|
|[Krótki przewodnik](../cppcx/quick-reference-c-cx.md)|Tabela słów kluczowych i operatory C + +/ CX.|
|[System typów](../cppcx/type-system-c-cx.md)|Opisuje podstawowe języka C + +/ CX typy i narzędzi programistycznych i jak korzystanie z C + +/ CX do wykorzystania i tworzenia typów środowiska wykonawczego systemu Windows.|
|[Tworzenie aplikacji i biblioteki](../cppcx/building-apps-and-libraries-c-cx.md)|Opisano sposób tworzenia aplikacji i link do biblioteki statyczne aned biblioteki DLL za pomocą środowiska IDE.|
|[Współdziałanie z innymi językami](../cppcx/interoperating-with-other-languages-c-cx.md)|W tym artykule omówiono sposób składników, które zostały napisane przy użyciu języka C + +/ CX może być używana ze składnikami, które zostały napisane w języku JavaScript, dowolny zarządzany języka, lub [!INCLUDE[cppwrl](../cppcx/includes/cppwrl-md.md)].|
|[Wątkowość i organizowanie](../cppcx/threading-and-marshaling-c-cx.md)|W tym artykule omówiono sposób określania zachowania wątków i organizowania składników, które można utworzyć.|
|[Odwołanie do przestrzeni nazw](../cppcx/namespaces-reference-c-cx.md)|Dokumentacja referencyjna dla domyślnej przestrzeni nazw, przestrzeń nazw platformy, Platform::Collections i pokrewne przestrzeni nazw.|
|[Funkcje CRT nie są obsługiwane w aplikacjach platformy uniwersalnej systemu Windows](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)|Zawiera listę funkcji CRT, które nie są dostępne do użycia w aplikacjach środowiska wykonawczego systemu Windows.|
|[Jak przewodniki dla aplikacji systemu Windows 10](http://msdn.microsoft.com/library/windows/apps/xaml/mt244352.aspx)|Zawiera ogólne wskazówki dotyczące aplikacji systemu Windows 10 i łącza do dodatkowych informacji.|
|[C + +/ CX część 0 \[ n \]: wprowadzenie](https://blogs.msdn.microsoft.com/vcblog/2012/08/29/ccx-part-0-of-n-an-introduction/)<br /><br />[C + +/ CX część 1 z \[ n \]: prostą klasę](https://blogs.msdn.microsoft.com/vcblog/2012/09/05/ccx-part-1-of-n-a-simple-class/)<br /><br />[C + +/ CX część 2 \[ n \]: typy, które nosić Kapelusze](https://blogs.msdn.microsoft.com/vcblog/2012/09/17/ccx-part-2-of-n-types-that-wear-hats/)<br /><br />[C + +/ CX część 3 \[ n \]: konstruowanego](https://blogs.msdn.microsoft.com/vcblog/2012/10/05/ccx-part-3-of-n-under-construction/)<br /><br />[C + +/ CX część 4 \[ n \]: statyczne funkcje Członkowskie](https://blogs.msdn.microsoft.com/vcblog/2012/10/19/ccx-part-4-of-n-static-member-functions/)|Wstępne cyklu blogów Visual C++ w języku C + +/ CX.|
