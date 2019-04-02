---
title: Aplikacje uniwersalne systemu Windows (C++)
ms.date: 03/30/2018
ms.assetid: 357121cc-d390-4bae-b34a-39614861a9f4
ms.openlocfilehash: fbd5366ee52dfe32baef9458a82c16914666699e
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58786819"
---
# <a name="universal-windows-apps-c"></a>Aplikacje uniwersalne systemu Windows (C++)

Platforma Universal Windows (UWP) jest nowoczesny interfejs programowania dla Windows. Za pomocą platformy uniwersalnej systemu Windows pisania aplikacji lub składnika jeden raz i wdrożyć ją na dowolnym urządzeniu z systemem Windows 10. Można napisać składnik w języku C++ i aplikacji napisanych w dowolnym języku zgodnym z platformy uniwersalnej systemu Windows mogło ich używać.

Większość dokumentacji platformy uniwersalnej systemu Windows znajduje się w drzewie zawartości Windows u [dokumentacji platformy uniwersalnej Windows](/windows/uwp/). Znajdziesz samouczki początku również jako dokumentacji. 

Nowe aplikacje platformy uniwersalnej systemu Windows i składników, zaleca się użycie [C + +/ WinRT](/windows/uwp/cpp-and-winrt-apis/), nowy standard C ++ 17 języka rzutowanie dla interfejsów API środowiska wykonawczego Windows. C + +/ WinRT jest dostępna w Windows 10 SDK z wersji 1803 wartości. C + +/ WinRT jest zaimplementowana w całości w plikach nagłówkowych i jest przeznaczony do zapewnia najwyższej jakości dostęp do nowoczesnego interfejsu Windows API. W przeciwieństwie do języka C + +/ CX implementacji. C + +/ WinRT nie używa niestandardowa składnia lub rozszerzenia języka firmy Microsoft i wykorzystuje ona pełną kompilatora języka C++, aby utworzyć wysoce zoptymalizowane pod kątem danych wyjściowych. Aby uzyskać więcej informacji, zobacz [wprowadzenie dla C + +/ WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt).

Konwerter aplikacji Desktop Bridge umożliwia pakietu istniejącej aplikacji klasycznych dla wdrożenia przez Microsoft Store. Aby uzyskać więcej informacji, zobacz [przy użyciu środowiska uruchomieniowego Visual C++ w projekcie Centennial](https://blogs.msdn.microsoft.com/vcblog/2016/07/07/using-visual-c-runtime-in-centennial-project) i [Desktop Bridge](/windows/uwp/porting/desktop-to-uwp-root).

## <a name="uwp-apps-that-use-ccx"></a>Aplikacje platformy uniwersalnej systemu Windows, które używają języka C + +/ CX

|||
|-|-|
|[Odwołanie językowe Visual C++ (C + +/ CX)](visual-c-language-reference-c-cx.md)|Opisuje zestaw rozszerzeń, które upraszczają zużycia C++ interfejsów API środowiska wykonawczego Windows i Włącz obsługi błędów, która jest oparta na wyjątkach.|
|[Tworzenie aplikacji i bibliotek (C++/CX)](building-apps-and-libraries-c-cx.md)|W tym artykule opisano sposób tworzenia bibliotek DLL i bibliotek statycznych, które mogą być udostępniane z C + +/ CX aplikacji lub składnika.|
|[Samouczek: Tworzenie platformy uniwersalnej systemu Windows aplikacja "Hello, World" w języku C + +/ CX](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp)|Przewodnik, który wprowadza podstawowe pojęcia dotyczące środowiska tworzenia aplikacji uniwersalnych systemu Windows w języku C + +/ CX. |
|[Tworzenie składników środowiska wykonawczego Windows w języku C + +/ CX](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)|W tym artykule opisano sposób tworzenia bibliotek DLL, które inne aplikacje platformy uniwersalnej systemu Windows i składniki mogą zużywać.|
|[Programowanie gier dla platformy uniwersalnej systemu Windows](/windows/uwp/gaming/)|Opisuje sposób używania programu DirectX i C + +/ CX do tworzenia gier.|

## <a name="uwp-apps-that-use-the-windows-runtime-c-template-library-wrl"></a>Aplikacje platformy uniwersalnej systemu Windows, które używają Biblioteka szablonów języka C++ środowiska wykonawczego systemu Windows (WRL)

Biblioteka szablonów C++ środowiska wykonawczego Windows zapewnia niskiego poziomu interfejsy COM, dzięki którym kod ISO C++ mogą uzyskiwać dostęp do środowiska wykonawczego Windows w środowisku wolnym od wyjątku. W większości przypadków zaleca się, że używasz języka C + +/ WinRT lub C + +/ CX zamiast Biblioteka szablonów C++ środowiska wykonawczego Windows, do tworzenia aplikacji platformy uniwersalnej systemu Windows. Aby dowiedzieć się, Biblioteka szablonów C++ środowiska wykonawczego Windows, zobacz [Windows środowiska uruchomieniowego C++ szablon biblioteki (WRL)](wrl/windows-runtime-cpp-template-library-wrl.md).

## <a name="see-also"></a>Zobacz także

[Język C++ w programie Visual Studio](../overview/visual-cpp-in-visual-studio.md)<br/>
[Omówienie programowania w systemie Windows w języku C++](../windows/overview-of-windows-programming-in-cpp.md)<br/>