---
title: Aplikacje uniwersalne systemu Windows (C++) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 357121cc-d390-4bae-b34a-39614861a9f4
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a293f833de7bc575209089362bcaf146d074684b
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="universal-windows-apps-c"></a>Aplikacje uniwersalne systemu Windows (C++)
Uniwersalnych aplikacji platformy systemu Windows (UWP) opracowane zestaw reguł projektowania, które wyróżnić użytkownika proste interfejsy, które są skupia się wokół zawartości, która automatycznie dopasowane do różnych rozmiarów ekranu na różnych urządzeniach. Możesz utworzyć interfejsu użytkownika w kodzie XAML i kodem w natywnym kodzie C++. Można również utworzyć składników (dll), które mogą być używane przez aplikacje platformy uniwersalnej systemu Windows, które są zapisywane w innych językach. Powierzchnia interfejsu API dla aplikacji platformy uniwersalnej systemu Windows jest środowiska wykonawczego systemu Windows, który jest dobrze factored biblioteki, która zapewnia szerokiej gamy usług systemu operacyjnego.  

> [!TIP]  
> Dla systemu Windows 10 można konwertera aplikacji pulpitu pakietu istniejącej aplikacji klasycznych dla wdrożenia za pomocą Microsoft Store. Aby uzyskać więcej informacji, zobacz [przy użyciu środowiska uruchomieniowego Visual C++ w projekcie Centennial](https://blogs.msdn.microsoft.com/vcblog/2016/07/07/using-visual-c-runtime-in-centennial-project) i [przełączyć aplikację pulpitu do systemu Windows platformy Uniwersalnej z Mostek pulpitu](https://msdn.microsoft.com/en-us/windows/uwp/porting/desktop-to-uwp-root).
  
  
## <a name="uwp-apps-that-use-ccx"></a>Aplikacji platformy uniwersalnej systemu Windows, które używają C + +/ CX  
  
|||  
|-|-|  
|[Dokumentacja języka języka Visual C++ (C + +/ CX)](../cppcx/visual-c-language-reference-c-cx.md)|W tym artykule opisano zestaw rozszerzeń, które upraszczają zużycie C++ interfejsów API środowiska wykonawczego systemu Windows i włączyć obsługi błędów, który jest oparty na wyjątki.|  
|[Tworzenie aplikacji i bibliotek (C++/CX)](../cppcx/building-apps-and-libraries-c-cx.md)|Opisuje sposób tworzenia biblioteki dll i biblioteki statyczne, które są dostępne z C + +/ CX aplikację lub składnik.|  
|[Samouczek: Tworzenie pierwszej aplikacji platformy uniwersalnej systemu Windows w języku C++](https://docs.microsoft.com/en-us/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp)|Przewodnik wprowadzający podstawowych pojęć dotyczących tworzenia aplikacji uniwersalnych systemu Windows w języku C++. (Nie został jeszcze zaktualizowany do tworzenia aplikacji platformy uniwersalnej systemu Windows w systemie Windows 10.)|  
|[Tworzenie składników środowiska wykonawczego systemu Windows w języku C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)|Opisuje sposób tworzenia bibliotek DLL, które mogą korzystać z innych aplikacji platformy uniwersalnej systemu Windows i składników.|  
|[Projektowanie gier](https://docs.microsoft.com/en-us/windows/uwp/gaming/)|Informacje dotyczące używania programu DirectX i C++ do tworzenia gier.|  
  
## <a name="uwp-apps-that-use-the-windows-runtime-c-template-library-wrl"></a>Aplikacji platformy uniwersalnej systemu Windows, które używają Biblioteka szablonów C++ środowiska wykonawczego systemu Windows (WRL) 
 Biblioteka szablonów C++ środowiska wykonawczego systemu Windows udostępnia interfejsy modelu COM niskiego poziomu, według których kod ISO C++ mogą uzyskiwać dostęp do środowiska wykonawczego systemu Windows w środowisku bez wyjątku. W większości przypadków zaleca się, że używasz C + +/ CX zamiast Biblioteka szablonów C++ środowiska wykonawczego systemu Windows, do tworzenia aplikacji platformy uniwersalnej systemu Windows. Aby uzyskać informacje o Biblioteka szablonów C++ środowiska wykonawczego systemu Windows, zobacz [Windows środowiska uruchomieniowego C++ szablonu biblioteki (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Visual C++](../visual-cpp-in-visual-studio.md)

