---
title: Dokumentacja języka Visual C++ (C + +/ CX) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/15/2017
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: 3f6abf92-4e5e-4ed8-8e11-f9252380d30a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bad7a0a5263d001d9dc77dd8d9e8cf0cf70100b4
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43219642"
---
# <a name="visual-c-language-reference-ccx"></a>Dokumentacja języka Visual C++ (C + +/ CX)

C + +/ CX to zestaw rozszerzeń języka C++, które umożliwiają tworzenie aplikacji Windows i składników środowiska wykonawczego Windows w idiom, który jest możliwie blisko możliwie do nowoczesnego języka C++. Użyj języka C + +/ CX do pisania aplikacji Windows i składników kodu macierzystego, który łatwością wchodzić w interakcje z Visual C#, Visual Basic i języka JavaScript, a inne języki, które obsługują środowiska wykonawczego Windows. W tych rzadkich przypadkach, które wymagają bezpośredniego dostępu do surowego interfejsów COM lub kod bez wyjątków, można użyć [Windows środowiska uruchomieniowego C++ szablon biblioteki (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md).

> [!NOTE]
> C + +/ WinRT jest nowy, standard C ++ 17 języka dla interfejsów API środowiska wykonawczego Windows. Jest ona dostępna w najnowszy zestaw Windows 10 SDK z wersji 1803 wartości. C + +/ WinRT jest zaimplementowana w całości w plikach nagłówkowych i przeznaczone do zapewnia najwyższej jakości dostęp do nowoczesnego interfejsu Windows API.

> Za pomocą C + +/ WinRT, można używać lub Tworzenie interfejsów API środowiska wykonawczego Windows przy użyciu dowolnej zgodnych ze standardami języka C ++ 17 kompilatora. C + +/ WinRT zazwyczaj działa lepiej i generuje mniejsze pliki binarne niż innych opcji języka dla środowiska wykonawczego Windows. Firma Microsoft będzie obsługiwać C + +/ CX i WRL, ale zdecydowanie zalecamy, aby użyć nowych aplikacji C + +/ WinRT. Aby uzyskać więcej informacji, zobacz [C + +/ WinRT](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/index).


Za pomocą C + +/ CX, można utworzyć:

- Aplikacje C++ Universal Windows Platform (UWP), które umożliwiają definiowanie użytkownika XAML interfejs i korzystanie z natywnych stosu. Aby uzyskać więcej informacji, zobacz [Utwórz aplikację "hello world" w języku C++ (UWP)](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp).

- Składniki środowiska uruchomieniowego Windows C++, które mogą być używane przez aplikacje Windows oparte na języku JavaScript. Aby uzyskać więcej informacji, zobacz [Tworzenie składników środowiska wykonawczego Windows w języku C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp).

- Gry Windows DirectX i aplikacji intensywnie korzystających z grafiki. Aby uzyskać więcej informacji, zobacz [Tworzenie prostej grze platformy uniwersalnej systemu Windows przy użyciu technologii DirectX](/windows/uwp/gaming/tutorial--create-your-first-metro-style-directx-game).

## <a name="related-articles"></a>Powiązane artykuły

|||
|-|-|
|[Krótki przewodnik](../cppcx/quick-reference-c-cx.md)|Tabela słów kluczowych i operatory w języku C + +/ CX.|
|[System typów](../cppcx/type-system-c-cx.md)|W tym artykule opisano podstawowe języka C + +/ CX typów i narzędzi programistycznych oraz jak korzystanie z C + +/ CX, używanie i tworzenie typów środowiska wykonawczego Windows.|
|[Tworzenie aplikacji i bibliotek](../cppcx/building-apps-and-libraries-c-cx.md)|W tym artykule omówiono sposób używania środowiska IDE do tworzenia aplikacji i link do bibliotek statycznych aned biblioteki dll.|
|[Współdziałanie z innymi językami](../cppcx/interoperating-with-other-languages-c-cx.md)|W tym artykule omówiono sposób składniki, które są tworzone za pomocą C + +/ CX może być używany ze składnikami, które zostały napisane w języku JavaScript, zarządzane dowolnego języka lub biblioteka szablonów C++ środowiska wykonawczego Windows.|
|[Wątkowość i Marshaling](../cppcx/threading-and-marshaling-c-cx.md)|W tym artykule omówiono sposób określania zachowania wątkowości i organizowania składników, które tworzysz.|
|[Odwołanie do przestrzeni nazw](../cppcx/namespaces-reference-c-cx.md)|Dokumentacja dotycząca domyślny obszar nazw, przestrzeń nazw platformy, Platform::Collections i pokrewne obszary nazw.|
|[Funkcje CRT nie są obsługiwane w aplikacjach platformy uniwersalnej systemu Windows](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)|Wyświetla listę funkcji CRT, które nie są dostępne do użycia w aplikacjach Windows Runtime.|
|[Przewodniki z instrukcjami dla aplikacji systemu Windows 10](https://msdn.microsoft.com/library/windows/apps/xaml/mt244352.aspx)|Zawiera ogólne wskazówki na temat aplikacji systemu Windows 10 i linki do szczegółowych informacji.|
|[C + +/ CX część 0 \[n\]: wprowadzenie](https://blogs.msdn.microsoft.com/vcblog/2012/08/29/ccx-part-0-of-n-an-introduction/)<br /><br />[C + +/ CX, część 1 z \[n\]: prostą klasę](https://blogs.msdn.microsoft.com/vcblog/2012/09/05/ccx-part-1-of-n-a-simple-class/)<br /><br />[C + +/ CX część 2 \[n\]: typy, które systemy Wear](https://blogs.msdn.microsoft.com/vcblog/2012/09/17/ccx-part-2-of-n-types-that-wear-hats/)<br /><br />[C + +/ CX część 3 \[n\]: W trakcie tworzenia](https://blogs.msdn.microsoft.com/vcblog/2012/10/05/ccx-part-3-of-n-under-construction/)<br /><br />[C + +/ CX część 4 \[n\]: statyczne funkcje Członkowskie](https://blogs.msdn.microsoft.com/vcblog/2012/10/19/ccx-part-4-of-n-static-member-functions/)|Wprowadzające cyklu blogów Visual C++ w języku C + +/ CX.|
