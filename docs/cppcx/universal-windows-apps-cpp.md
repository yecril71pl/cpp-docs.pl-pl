---
title: Aplikacje uniwersalne systemu Windows (C++)
ms.date: 03/30/2018
ms.assetid: 357121cc-d390-4bae-b34a-39614861a9f4
ms.topic: overview
ms.openlocfilehash: 45d02a5ab923ee46da97d78a1e5ceb2f4313352a
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88841677"
---
# <a name="universal-windows-apps-c"></a>Aplikacje uniwersalne systemu Windows (C++)

Platforma uniwersalna systemu Windows (platformy UWP) to nowoczesny interfejs programistyczny dla systemu Windows. Za pomocą platformy UWP można napisać aplikację lub składnik raz i wdrożyć ją na dowolnym urządzeniu z systemem Windows 10. Można napisać składnik w języku C++, a aplikacje zapisane w dowolnym innym języku zgodnym z platformy UWP mogą korzystać z niego.

Większość dokumentacji platformy UWP znajduje się w drzewie zawartości systemu Windows w [dokumentacji platforma uniwersalna systemu Windows](/windows/uwp/). Znajdziesz tu samouczki i dokumentację referencyjną.

W przypadku nowych aplikacji i składników platformy UWP zaleca się używanie [języka c++/WinRT](/windows/uwp/cpp-and-winrt-apis/), nowego standardowego języka c++ 17 dla środowisko wykonawcze systemu Windows interfejsów API. C++/WinRT jest dostępna w zestawie SDK systemu Windows 10 w wersji 1803. Język C++/WinRT jest implementowany całkowicie w plikach nagłówkowych i został zaprojektowany w celu zapewnienia pierwszej klasy dostępu do nowoczesnego interfejsu API systemu Windows. W przeciwieństwie do implementacji języka C++/CX, C++/WinRT nie korzysta ze składni niestandardowej ani rozszerzeń języka firmy Microsoft i w pełni wykorzystuje kompilator języka C++ do tworzenia wysoce zoptymalizowanych danych wyjściowych. Aby uzyskać więcej informacji, zobacz [wprowadzenie do C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt).

Możesz użyć konwertera aplikacji mostka programu Desktop do spakowania istniejącej aplikacji klasycznej do wdrożenia za pomocą Microsoft Store. Aby uzyskać więcej informacji, zobacz [Używanie środowiska uruchomieniowego Visual C++ w projekcie Centennial](https://devblogs.microsoft.com/cppblog/using-visual-c-runtime-in-centennial-project/) i [Bridge Desktop](/windows/uwp/porting/desktop-to-uwp-root).

## <a name="uwp-apps-that-use-ccx"></a>PLATFORMY UWP aplikacje korzystające z języka C++/CX

[Dokumentacja języka C++/CX](visual-c-language-reference-c-cx.md)\
Opisuje zestaw rozszerzeń, które upraszczają użycie języka C++ środowisko wykonawcze systemu Windows interfejsów API i umożliwiają obsługę błędów, która jest oparta na wyjątkach.

[Tworzenie aplikacji i bibliotek (C++/CX)](building-apps-and-libraries-c-cx.md)\
Opisuje sposób tworzenia bibliotek DLL i bibliotek statycznych, do których można uzyskać dostęp za pomocą aplikacji lub składnika C++/CX.

[Samouczek: Tworzenie aplikacji platformy UWP "Hello, World" w języku C++/CX](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp)\
Przewodnik przedstawiający podstawowe koncepcje opracowywania aplikacji platformy UWP w języku C++/CX.

[Tworzenie składników środowisko wykonawcze systemu Windows w języku C++/CX](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)\
Opisuje sposób tworzenia bibliotek DLL, które mogą być używane przez inne aplikacje i składniki platformy UWP.

[PLATFORMY UWP Programowanie gier](/windows/uwp/gaming/)\
Opisuje sposób używania programu DirectX i C++/CX do tworzenia gier.

## <a name="uwp-apps-that-use-the-windows-runtime-c-template-library-wrl"></a>PLATFORMY UWP aplikacje korzystające środowisko wykonawcze systemu Windows z biblioteki szablonów języka C++ (WRL)

Środowisko wykonawcze systemu Windows Biblioteka szablonów C++ udostępnia interfejsy COM niskiego poziomu, za pomocą których kod ISO C++ może uzyskać dostęp do środowisko wykonawcze systemu Windows w środowisku bez wyjątków. W większości przypadków zaleca się użycie języka C++/WinRT lub C++/CX zamiast środowisko wykonawcze systemu Windows biblioteki szablonów C++ do tworzenia aplikacji platformy UWP. Aby uzyskać informacje na temat biblioteki szablonów środowisko wykonawcze systemu Windows C++, zobacz [środowisko wykonawcze systemu Windows C++ Template Library (WRL)](wrl/windows-runtime-cpp-template-library-wrl.md).

## <a name="see-also"></a>Zobacz też

[Język C++ w programie Visual Studio](../overview/visual-cpp-in-visual-studio.md)<br/>
[Omówienie programowania w systemie Windows w języku C++](../windows/overview-of-windows-programming-in-cpp.md)<br/>
