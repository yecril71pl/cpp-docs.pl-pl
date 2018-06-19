---
title: Aplikacje uniwersalne systemu Windows (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 03/30/2018
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 357121cc-d390-4bae-b34a-39614861a9f4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9914e9ac83efcc43ef120259254b65ef4f1e0ee9
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33891126"
---
# <a name="universal-windows-apps-c"></a>Aplikacje uniwersalne systemu Windows (C++)

Uniwersalnych aplikacji platformy systemu Windows (UWP) opracowane zestaw reguł projektowania, które wyróżnić użytkownika proste interfejsy, które są skupia się wokół zawartości, która automatycznie dopasowane do różnych rozmiarów ekranu na różnych urządzeniach. Możesz utworzyć interfejsu użytkownika w kodzie XAML i kodem w natywnym kodzie C++. Można również utworzyć składników (dll), które mogą być używane przez aplikacje platformy uniwersalnej systemu Windows, które są zapisywane w innych językach. Powierzchnia interfejsu API dla aplikacji platformy uniwersalnej systemu Windows jest środowiska wykonawczego systemu Windows, który jest dobrze factored biblioteki, która zapewnia szerokiej gamy usług systemu operacyjnego.

> [!TIP]  
> Dla systemu Windows 10 konwertera aplikacji Mostek pulpitu służy do istniejącej aplikacji klasycznych dla wdrożenia za pomocą Microsoft Store pakietu. Aby uzyskać więcej informacji, zobacz [przy użyciu środowiska uruchomieniowego Visual C++ w projekcie Centennial](https://blogs.msdn.microsoft.com/vcblog/2016/07/07/using-visual-c-runtime-in-centennial-project) i [Mostek pulpitu](/windows/uwp/porting/desktop-to-uwp-root).

## <a name="uwp-apps-that-use-cwinrt"></a>Aplikacji platformy uniwersalnej systemu Windows, które używają C + +/ WinRT

C + +/ WinRT jest nowy, tylko nagłówek oparty na bibliotece C++ języka dla środowiska uruchomieniowego systemu Windows, który używa całkowicie standard C++, w odróżnieniu od C + +/ CX implementacji. C + +/ WinRT nie używa niestandardowa składnia lub rozszerzenia języka Microsoft i pełne korzysta z kompilatora C++ do tworzenia wysokiej zoptymalizowanych pod kątem danych wyjściowych. Aby uzyskać więcej informacji, zobacz [C + +/ WinRT](/windows/uwp/cpp-and-winrt-apis). Aby obejrzeć wprowadzenie do języka C + +/ WinRT i kodu — Szybki Start zobacz [wprowadzenie do języka C + +/ WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt).

## <a name="uwp-apps-that-use-ccx"></a>Aplikacji platformy uniwersalnej systemu Windows, które używają C + +/ CX

|||
|-|-|
|[Dokumentacja języka języka Visual C++ (C + +/ CX)](../cppcx/visual-c-language-reference-c-cx.md)|W tym artykule opisano zestaw rozszerzeń, które upraszczają zużycie C++ interfejsów API środowiska wykonawczego systemu Windows i włączyć obsługi błędów, który jest oparty na wyjątki.|
|[Tworzenie aplikacji i bibliotek (C++/CX)](../cppcx/building-apps-and-libraries-c-cx.md)|Opisuje sposób tworzenia biblioteki dll i biblioteki statyczne, które są dostępne z C + +/ CX aplikację lub składnik.|
|[Samouczek: Tworzenie platformy uniwersalnej systemu Windows aplikacja "Hello, World" w języku C + +/ CX](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp)|Przewodnik wprowadzający podstawowych pojęć dotyczących tworzenia aplikacji uniwersalnych systemu Windows w języku C + +/ CX. |
|[Tworzenie składników środowiska wykonawczego systemu Windows w języku C + +/ CX](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)|Opisuje sposób tworzenia bibliotek DLL, które mogą korzystać z innych aplikacji platformy uniwersalnej systemu Windows i składników.|
|[Programowanie gier platformy uniwersalnej systemu Windows](/windows/uwp/gaming/)|Informacje dotyczące używania programu DirectX i C + +/ CX do tworzenia gier.|

## <a name="uwp-apps-that-use-the-windows-runtime-c-template-library-wrl"></a>Aplikacji platformy uniwersalnej systemu Windows, które używają Biblioteka szablonów C++ środowiska wykonawczego systemu Windows (WRL)

Biblioteka szablonów C++ środowiska wykonawczego systemu Windows udostępnia interfejsy modelu COM niskiego poziomu, według których kod ISO C++ mogą uzyskiwać dostęp do środowiska wykonawczego systemu Windows w środowisku bez wyjątku. W większości przypadków zaleca się, że używasz C + +/ WinRT lub C + +/ CX zamiast Biblioteka szablonów C++ środowiska wykonawczego systemu Windows, do tworzenia aplikacji platformy uniwersalnej systemu Windows. Aby uzyskać informacje o Biblioteka szablonów C++ środowiska wykonawczego systemu Windows, zobacz [Windows środowiska uruchomieniowego C++ szablonu biblioteki (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md).

## <a name="see-also"></a>Zobacz także

[Visual C++](../visual-cpp-in-visual-studio.md)<br/>
