---
title: Kreator aplikacji MFC | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.appwiz.mfc.exe.overview
dev_langs:
- C++
helpviewer_keywords:
- MFC Application Wizard
- executable files, creating
ms.assetid: 227ac090-921d-4b2f-be0a-66a5f4cab0d4
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9d4997d2d793102119e5021ba1110db2674e1b42
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="mfc-application-wizard"></a>Kreator aplikacji MFC
Kreator aplikacji MFC tworzy aplikację, która po skompilowaniu implementuje podstawowe funkcje aplikacji wykonywalnej systemu Windows (.exe). Aplikacja startowa MFC starter zawiera pliki źródłowe (.cpp) języka C++, pliki zasobów (.rc), pliki nagłówków (.h) i pliki projektu (.vcxproj). Kod generowany w tych plikach startowych jest oparty na bibliotece MFC.  
  
> [!NOTE]
>  Zależnie od wybranych opcji kreator tworzy dodatkowe pliki w projekcie. Na przykład w przypadku wybrania **pomocy kontekstowej** na [funkcje zaawansowane](../../mfc/reference/advanced-features-mfc-application-wizard.md) strony, Kreator tworzy pliki, które są niezbędne do kompilacji pliki pomocy projektu. Aby uzyskać więcej informacji o plikach tworzonych przez kreatora, zobacz [pliku typy utworzone dla projektów Visual C++](../../ide/file-types-created-for-visual-cpp-projects.md)i znajduje się w pliku Readme.txt w projekcie.  
  
## <a name="overview"></a>Omówienie  
 Ta strona kreatora zawiera opis bieżących ustawień tworzonej aplikacji MFC. Domyślnie kreator tworzy projekt w następujący sposób:  
  
-   [Typ aplikacji, kreator aplikacji MFC](../../mfc/reference/application-type-mfc-application-wizard.md)  
  
    -   Projekt jest tworzony z obsługą interfejsu kart dla wielu dokumentów (MDI). Aby uzyskać więcej informacji, zobacz [SDI i MDI](../../mfc/sdi-and-mdi.md).  
  
    -   Projekt korzysta z [architektury dokument/widok](../../mfc/document-view-architecture.md).  
  
    -   Projekt używa bibliotek Unicode.  
  
    -   Projekt jest tworzony przy użyciu stylu projektu programu Visual Studio i umożliwia przełączanie stylu wizualnego.  
  
    -   Projekt używa biblioteki MFC w udostępnionym pliku DLL. Aby uzyskać więcej informacji, zobacz [biblioteki dll w programie Visual C++](../../build/dlls-in-visual-cpp.md).  
  
-   [Obsługa dokumentów złożonych, kreator aplikacji MFC](../../mfc/reference/compound-document-support-mfc-application-wizard.md)  
  
    -   Projekt nie obsługuje dokumentów złożonych.  
  
-   [Ciągi szablonu dokumentu, kreator aplikacji MFC](../../mfc/reference/document-template-strings-mfc-application-wizard.md)  
  
    -   Nazwa projektu jest używana dla ciągów tekstowych domyślnego szablonu dokumentów.  
  
-   [Obsługa bazy danych, kreator aplikacji MFC](../../mfc/reference/database-support-mfc-application-wizard.md)  
  
    -   Projekt nie obsługuje baz danych.  
  
-   [Funkcje interfejsu użytkownika, kreator aplikacji MFC](../../mfc/reference/user-interface-features-mfc-application-wizard.md)  
  
    -   Projekt implementuje standardowe systemu Windows, interfejs użytkownika funkcji, takich jak system menu, paska stanu, zmaksymalizować oraz zminimalizować pola, **o** okno, paska menu standardowego i Dokowanie paska narzędzi i ramek podrzędnych.  
  
-   [Funkcje zaawansowane, kreator aplikacji MFC](../../mfc/reference/advanced-features-mfc-application-wizard.md)  
  
    -   Projekt obsługuje drukowanie i podgląd wydruku.  
  
    -   Projekt obsługuje kontrolki ActiveX. Aby uzyskać więcej informacji, zobacz [sekwencji operacji tworzenia formantów ActiveX](../../mfc/sequence-of-operations-for-creating-activex-controls.md).  
  
    -   Projekt nie zapewnia obsługi dla [automatyzacji](../../mfc/automation.md), [MAPI](../../mfc/mapi-support-in-mfc.md), [Windows Sockets](../../mfc/windows-sockets-in-mfc.md), lub Active Accessibility.  
  
    -   Projekt obsługuje **Explorer** okienko dokujące **dane wyjściowe** okienko dokujące i **właściwości** okienko dokujące.  
  
-   [Klasy generowane, kreator aplikacji MFC](../../mfc/reference/generated-classes-mfc-application-wizard.md)  
  
    -   Klasa widoku projektu jest pochodną [cview — klasa](../../mfc/reference/cview-class.md).  
  
    -   Projekt aplikacji klasa pochodzi od [CWinAppEx klasy](../../mfc/reference/cwinappex-class.md).  
  
    -   Klasa dokumentu typu projektu jest pochodną [cdocument — klasa](../../mfc/reference/cdocument-class.md).  
  
    -   Jest pochodną klasy głównym ramki projektu [CMDIFrameWndEx klasy](../../mfc/reference/cmdiframewndex-class.md).  
  
    -   Projektu podrzędnego ramki klasa pochodzi od [CMDIChildWndEx klasy](../../mfc/reference/cmdichildwndex-class.md).  
  
 Aby zmienić te domyślne ustawienia, należy kliknąć odpowiedni tytuł karty w lewej kolumnie kreatora i wprowadź zmiany na wyświetlonej stronie.  
  
 Po utworzeniu projektu aplikacji MFC do projektu przy użyciu języka Visual C++ można dodać obiektów lub kontrolki [kreatorów kodu](../../ide/adding-functionality-with-code-wizards-cpp.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie aplikacji MFC](../../mfc/reference/creating-an-mfc-application.md)   
 [Aplikacje dla pulpitu MFC](../../mfc/mfc-desktop-applications.md)   
 [Używanie klas do pisania aplikacji dla systemu Windows](../../mfc/using-the-classes-to-write-applications-for-windows.md)
