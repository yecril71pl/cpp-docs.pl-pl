---
title: Windows Universal Apps (C++) | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 56b6642bb24107da4c09856dbd8daaf70fb7dfd5
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2018
ms.locfileid: "40015010"
---
# <a name="universal-windows-apps-c"></a>Aplikacje uniwersalne systemu Windows (C++)

Uniwersalnych aplikacji dla platformy Windows (UWP) wcielają zestaw zasad projektowania, które podkreślić proste interfejsy użytkownika skoncentrowane wokół zawartości, który automatycznie dostosowuje się do różnych rozmiarów ekranu na różnych urządzeniach. Należy utworzyć UI w znaczników XAML i kodem w natywnym kodzie C++. Można również utworzyć komponenty (dll), które mogą być używane przez aplikacje platformy uniwersalnej systemu Windows, które są zapisywane w innych językach. Powierzchnią API dla aplikacji platformy uniwersalnej systemu Windows jest środowiska wykonawczego Windows, który jest dobrze uwarunkowaną biblioteką, która zapewnia szerokiej gamy usług systemu operacyjnego.

> [!TIP]  
> Dla systemu Windows 10 Desktop Bridge konwerter aplikacji służy również do pakietu istniejącej aplikacji klasycznych dla wdrożenia przez Microsoft Store. Aby uzyskać więcej informacji, zobacz [przy użyciu środowiska uruchomieniowego Visual C++ w projekcie Centennial](https://blogs.msdn.microsoft.com/vcblog/2016/07/07/using-visual-c-runtime-in-centennial-project) i [Desktop Bridge](/windows/uwp/porting/desktop-to-uwp-root).

## <a name="uwp-apps-that-use-cwinrt"></a>Aplikacje platformy uniwersalnej systemu Windows, które używają języka C + +/ WinRT

C + +/ WinRT jest nowy, tylko nagłówek oparty na bibliotece języka C++ język dla środowiska Windows Runtime, która używa całkowicie standardowego języka C++, w odróżnieniu od C + +/ CX implementacji. C + +/ WinRT nie używa niestandardowa składnia lub rozszerzenia języka firmy Microsoft i wykorzystuje ona pełną kompilatora języka C++, aby utworzyć wysoce zoptymalizowane pod kątem danych wyjściowych. Aby uzyskać więcej informacji, zobacz [C + +/ WinRT](/windows/uwp/cpp-and-winrt-apis). Wprowadzenie do języka C + +/ WinRT i kod Przewodnik Szybki Start zobacz [wprowadzenie dla C + +/ WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt).

## <a name="uwp-apps-that-use-ccx"></a>Aplikacje platformy uniwersalnej systemu Windows, które używają języka C + +/ CX

|||
|-|-|
|[Odwołanie językowe Visual C++ (C + +/ CX)](../cppcx/visual-c-language-reference-c-cx.md)|Opisuje zestaw rozszerzeń, które upraszczają zużycia C++ interfejsów API środowiska wykonawczego Windows i Włącz obsługi błędów, która jest oparta na wyjątkach.|
|[Tworzenie aplikacji i bibliotek (C++/CX)](../cppcx/building-apps-and-libraries-c-cx.md)|W tym artykule opisano sposób tworzenia bibliotek DLL i bibliotek statycznych, które mogą być udostępniane z C + +/ CX aplikacji lub składnika.|
|[Samouczek: Tworzenie platformy uniwersalnej systemu Windows aplikacja "Hello, World" w języku C + +/ CX](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp)|Przewodnik, który wprowadza podstawowe pojęcia dotyczące środowiska tworzenia aplikacji uniwersalnych systemu Windows w języku C + +/ CX. |
|[Tworzenie składników środowiska wykonawczego Windows w języku C + +/ CX](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)|W tym artykule opisano sposób tworzenia bibliotek DLL, które inne aplikacje platformy uniwersalnej systemu Windows i składniki mogą zużywać.|
|[Programowanie gier dla platformy uniwersalnej systemu Windows](/windows/uwp/gaming/)|Opisuje sposób używania programu DirectX i C + +/ CX do tworzenia gier.|

## <a name="uwp-apps-that-use-the-windows-runtime-c-template-library-wrl"></a>Aplikacje platformy uniwersalnej systemu Windows, które używają Biblioteka szablonów języka C++ środowiska wykonawczego systemu Windows (WRL)

Biblioteka szablonów C++ środowiska wykonawczego Windows zapewnia niskiego poziomu interfejsy COM, dzięki którym kod ISO C++ mogą uzyskiwać dostęp do środowiska wykonawczego Windows w środowisku wolnym od wyjątku. W większości przypadków zaleca się, że używasz języka C + +/ WinRT lub C + +/ CX zamiast Biblioteka szablonów C++ środowiska wykonawczego Windows, do tworzenia aplikacji platformy uniwersalnej systemu Windows. Aby dowiedzieć się, Biblioteka szablonów C++ środowiska wykonawczego Windows, zobacz [Windows środowiska uruchomieniowego C++ szablon biblioteki (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md).

## <a name="see-also"></a>Zobacz także
 [Visual C++](../visual-cpp-in-visual-studio.md)<br/>