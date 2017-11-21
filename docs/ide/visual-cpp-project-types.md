---
title: "Typy projektów Visual C++ | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 10/30/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- programs [C++], projects
- project templates [Visual Studio], C++
- TODO comments [C++]
- projects [C++], types
- templates [C++], projects
- applications [C++], projects
- Visual C++ projects, types
ms.assetid: 7337987e-1e7b-4120-9a4b-94f0401f15e7
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 625489b69b3831d78bbe9bc80d92838e1e79b0c8
ms.sourcegitcommit: 69632887f7a85f4841c49b4c1353d3144927a52c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/11/2017
---
# <a name="visual-c-project-types"></a>Typy projektów Visual C++

Szablon projektu umożliwia utworzenie struktura podstawowa programu, menu, paski narzędzi, ikony, odwołania i `#include` instrukcji, które są odpowiednie dla rodzaju projektu, w którym chcesz utworzyć. Visual Studio zawiera kilka rodzajów szablony projektów Visual C++ i zapewnia kreatorów dla wielu z nich można dostosować swoje projekty, jak można je utworzyć. Natychmiast po utworzeniu projektu, należy go skompilować i uruchomić aplikacji; należy dobrze kompilacji sporadycznie podczas opracowywania aplikacji.

Nie trzeba użyć szablonu, aby utworzyć projekt, ale w większości przypadków jest bardziej wydajne, aby to zrobić, ponieważ możliwe jest łatwiejsze do zmodyfikowania plików projektu udostępnionego i struktura niż je tworzyć od podstaw.  
  
> [!NOTE]
> Projekt języka C można utworzyć przy użyciu szablonów projektu C++. W wygenerowanego projektu, Znajdź pliki, których .cpp rozszerzenia nazwy pliku i zmień go na. c. Następnie na **właściwości projektu** dla projektu (a nie dla rozwiązania) rozwiń pozycję **właściwości konfiguracji**, **C/C++** i wybierz **zaawansowane**. Zmień **skompilować jako** ustawienie **skompiluj jako kod języka C (/ TC)**.

## <a name="project-templates"></a>Szablony projektu

Szablony projektów uwzględnione w programie Visual Studio są zależne od wersji produktu i obciążeń, które zostały zainstalowane. Jeśli po zainstalowaniu tworzenia klasycznych aplikacji z obciążenia C++, Visual Studio ma te szablony projektu Visual C++.

### <a name="windows-desktop"></a>System Windows Desktop

|Szablon projektu|Opis|  
|----------------------|-----------------------------| 
|[Aplikacji konsoli systemu Windows](../windows/creating-a-console-application.md)|Projekt do tworzenia aplikacji konsoli systemu Windows.|
|[Aplikacja systemu Windows](../windows/walkthrough-creating-windows-desktop-applications-cpp.md)|Projekt do tworzenia aplikacji systemu Windows desktop (Win32).|
|[Biblioteka DLL](../build/walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)|Projekt do tworzenia biblioteki dołączanej (dynamicznie DLL).|
|[Biblioteka statyczna](../windows/walkthrough-creating-and-using-a-static-library-cpp.md)|Projekt do tworzenia biblioteki statycznej (LIB).|
|Kreator pulpitu systemu Windows|Kreator tworzenia aplikacji klasycznych systemu Windows i bibliotek dodatkowe opcje.|

### <a name="general"></a>Ogólne

|Szablon projektu|Opis|
|----------------------|-----------------------------|
|Pusty projekt|Pusty projekt do tworzenia aplikacji, biblioteki lub biblioteki DLL. Należy dodać kodu ani wymaganych zasobów.|
|[Projektu pliku reguł programu make](../ide/creating-a-makefile-project.md)|Projekt do wykorzystywania zewnętrznego systemu kompilacji.|
|Udostępniane elementy projektu|Projekt używany do udostępniania plików między wiele projektów.|

### <a name="atl"></a>ATL

|Szablon projektu|Opis|
|----------------------|-----------------------------|
|[Projekt ATL](../atl/reference/creating-an-atl-project.md)|Projekt wykorzystujący Active Template Library.|

### <a name="test"></a>Test

|Szablon projektu|Opis|
|----------------------|-----------------------------|
|[Natywny jednostkowy projekt testowy](/visualstudio/test/writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp)|Projekt zawierający testy jednostkowe C++ macierzystego.|

### <a name="mfc"></a>MFC

Jeśli dodasz MFC i ATL obsługę składników do instalacji programu Visual Studio tych szablonów projektu są dodawane do programu Visual Studio.

|Szablon projektu|Opis|
|----------------------|-----------------------------|
|[Aplikacji MFC](../mfc/reference/creating-an-mfc-application.md)|Projekt do tworzenia aplikacji, która korzysta z biblioteki Microsoft Foundation Class (MFC).|
|[Kontrolki ActiveX MFC](../mfc/reference/creating-an-mfc-activex-control.md)|Projekt do tworzenia formantu ActiveX, który korzysta z biblioteki MFC.|
|[BIBLIOTEKI MFC DLL](../mfc/reference/creating-an-mfc-dll-project.md)|Projekt do tworzenia biblioteki dll, która korzysta z biblioteki MFC.|

### <a name="windows-universal-apps"></a>Uniwersalnych aplikacji systemu Windows

Jeśli dodasz składnika narzędzia platformy uniwersalnej systemu Windows C++ do instalacji programu Visual Studio tych szablonów projektu są dodawane do programu Visual Studio.

Omówienie aplikacji uniwersalnych systemu Windows w języku C++, zobacz [uniwersalnych aplikacji systemu Windows (C++)](../windows/universal-windows-apps-cpp.md).

|Szablon projektu|Opis|
|----------------------|-----------------------------|
|Pusta aplikacja|Projekt jednostronicowej aplikacji Windows platformy Uniwersalnej, który nie ma wstępnie zdefiniowanych kontrolek ani układu.|
|Aplikacja DirectX 11|Projekt aplikacji platformy uniwersalnej systemu Windows, który używa programu DirectX 11.|
|Aplikacja DirectX 12|Projekt aplikacji platformy uniwersalnej systemu Windows, który używa programu DirectX 12.|
|Aplikacja DirectX 11 i XAML|Projekt aplikacji platformy uniwersalnej systemu Windows, który używa programu DirectX 11 i języka XAML.|
|Aplikacji testów jednostkowych|Projekt do tworzenia aplikacji testów jednostkowych dla aplikacji uniwersalnych platformy systemu Windows (UWP).|
|DLL|Projekt natywnej biblioteki dołączanej (dynamicznie DLL) używany przez składnik aplikacji lub środowisko uruchomieniowe platformy uniwersalnej systemu Windows.|
|Biblioteka statyczna|Projekt biblioteki natywnego dołączanej statycznie (LIB), które mogą być używane przez składnik aplikacji lub środowisko uruchomieniowe platformy uniwersalnej systemu Windows.|
|Składnik środowiska wykonawczego systemu Windows|Projekt składnika środowiska wykonawczego systemu Windows, które mogą być używane przez uniwersalną aplikację systemu Windows, niezależnie od języka programowania, w którym napisano aplikację.|
|Projekt do tworzenia pakietów aplikacji systemu Windows|Projekt, który tworzy pakiet platformy uniwersalnej systemu Windows, który umożliwia aplikacja ładowana lub rozproszonych za pomocą Microsoft Store.|

## <a name="todo-comments"></a>Komentarze TODO

Wiele plików generowanych przez szablon projektu zawiera komentarze TODO pomoże zidentyfikować, w którym można podać kod źródłowy. Aby uzyskać więcej informacji na temat dodawania kodu, zobacz [Dodawanie funkcji z kreatorami kodów](../ide/adding-functionality-with-code-wizards-cpp.md) i [Praca z plikami zasobów](../windows/working-with-resource-files.md).

## <a name="see-also"></a>Zobacz też

[Tworzenie projektów pulpitu za pomocą kreatorów aplikacji](../ide/creating-desktop-projects-by-using-application-wizards.md)   
