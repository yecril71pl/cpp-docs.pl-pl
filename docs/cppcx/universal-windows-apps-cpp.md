---
title: Aplikacje uniwersalne systemu Windows (C++)
ms.date: 03/30/2018
ms.assetid: 357121cc-d390-4bae-b34a-39614861a9f4
ms.topic: overview
ms.openlocfilehash: 11a32504dfdd380f621c380994f4f53073547a57
ms.sourcegitcommit: 7750e4c291d56221c8893120c56a1fe6c9af60d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274704"
---
# <a name="universal-windows-apps-c"></a>Aplikacje uniwersalne systemu Windows (C++)

Platforma uniwersalna systemu Windows (platformy UWP) to nowoczesny interfejs programistyczny dla systemu Windows. Za pomocą platformy UWP można napisać aplikację lub składnik raz i wdrożyć ją na dowolnym urządzeniu z systemem Windows 10. Można napisać składnik programu C++ i aplikacji napisanych w dowolnym innym języku zgodnym z platformy UWP.

Większość dokumentacji platformy UWP znajduje się w drzewie zawartości systemu Windows w [dokumentacji platforma uniwersalna systemu Windows](/windows/uwp/). Znajdziesz tu samouczki i dokumentację referencyjną. 

W przypadku nowych aplikacji i składników platformy UWP zaleca się użycie [ C++/WinRT](/windows/uwp/cpp-and-winrt-apis/), nowego standardowego języka c++ 17 dla środowisko wykonawcze systemu Windows interfejsów API. C++/WinRT jest dostępny w zestawie SDK systemu Windows 10 w wersji 1803. C++/WinRT jest zaimplementowana całkowicie w plikach nagłówkowych i została zaprojektowana w celu zapewnienia pierwszej klasy dostępu do nowoczesnego interfejsu API systemu Windows. W przeciwieństwie C++do implementacji/CX. C++/WinRT nie korzysta ze składni niestandardowej ani rozszerzeń języka firmy Microsoft i w pełni C++ optymalizuje dane wyjściowe. Aby uzyskać więcej informacji, zobacz [wprowadzenie C++do/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt).

Możesz użyć konwertera aplikacji mostka programu Desktop do spakowania istniejącej aplikacji klasycznej do wdrożenia za pomocą Microsoft Store. Aby uzyskać więcej informacji, zobacz [Używanie C++ środowiska uruchomieniowego Visual w projekcie Centennial](https://blogs.msdn.microsoft.com/vcblog/2016/07/07/using-visual-c-runtime-in-centennial-project) i [mostka Desktop](/windows/uwp/porting/desktop-to-uwp-root).

## <a name="uwp-apps-that-use-ccx"></a>PLATFORMY UWP aplikacje korzystające C++z/CX

|||
|-|-|
|[C++Dokumentacja języka/CX](visual-c-language-reference-c-cx.md)|Opisuje zestaw rozszerzeń, które upraszczają C++ użycie interfejsów API środowisko wykonawcze systemu Windows i włączają obsługę błędów, która jest oparta na wyjątkach.|
|[Tworzenie aplikacji i bibliotek (C++/CX)](building-apps-and-libraries-c-cx.md)|Opisuje sposób tworzenia bibliotek DLL i bibliotek statycznych, do których można uzyskać dostęp C++za pomocą aplikacji lub składnika/CX.|
|[Samouczek: Tworzenie aplikacji platformy UWP "Hello, World" w C++usłudze/CX](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp)|Przewodnik wprowadzający podstawowe koncepcje opracowywania aplikacji platformy UWP w C++/CX. |
|[Tworzenie składników środowisko wykonawcze systemu Windows w C++/CX](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)|Opisuje sposób tworzenia bibliotek DLL, które mogą być używane przez inne aplikacje i składniki platformy UWP.|
|[PLATFORMY UWP Programowanie gier](/windows/uwp/gaming/)|Opisuje sposób używania programu DirectX i C++/CX do tworzenia gier.|

## <a name="uwp-apps-that-use-the-windows-runtime-c-template-library-wrl"></a>PLATFORMY UWP aplikacje korzystające z biblioteki C++ szablonów środowisko wykonawcze systemu Windows (WRL)

Biblioteka szablonów C++ środowisko wykonawcze systemu Windows udostępnia interfejsy com niskiego poziomu, za pomocą których kod C++ ISO może uzyskać dostęp do środowisko wykonawcze systemu Windows w środowisku bez wyjątków. W większości przypadków zalecamy użycie C++/WinRT lub C++/CX zamiast środowisko wykonawcze systemu Windows C++ biblioteki szablonów do tworzenia aplikacji platformy UWP. Aby uzyskać informacje na temat C++ środowisko wykonawcze systemu Windows biblioteki szablonów, [Zobacz C++ szablon środowisko wykonawcze systemu Windows Library (WRL)](wrl/windows-runtime-cpp-template-library-wrl.md).

## <a name="see-also"></a>Zobacz także

[Język C++ w programie Visual Studio](../overview/visual-cpp-in-visual-studio.md)<br/>
[Omówienie programowania w systemie Windows w języku C++](../windows/overview-of-windows-programming-in-cpp.md)<br/>