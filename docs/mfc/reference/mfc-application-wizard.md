---
title: Kreator aplikacji MFC
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfc.exe.overview
helpviewer_keywords:
- MFC Application Wizard
- executable files, creating
ms.assetid: 227ac090-921d-4b2f-be0a-66a5f4cab0d4
ms.openlocfilehash: e97c7a29dd56a69fad99e85c206ca2104fa71798
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65708200"
---
# <a name="mfc-application-wizard"></a>Kreator aplikacji MFC

Kreator aplikacji MFC tworzy aplikację, która po skompilowaniu implementuje podstawowe funkcje aplikacji wykonywalnej systemu Windows (.exe). Aplikacja startowa MFC starter zawiera pliki źródłowe (.cpp) języka C++, pliki zasobów (.rc), pliki nagłówków (.h) i pliki projektu (.vcxproj). Kod generowany w tych plikach startowych jest oparty na bibliotece MFC.

> [!NOTE]
>  Zależnie od wybranych opcji kreator tworzy dodatkowe pliki w projekcie. Na przykład w przypadku wybrania **pomocy kontekstowej** na [funkcje zaawansowane](../../mfc/reference/advanced-features-mfc-application-wizard.md) strony, Kreator tworzy pliki, które są niezbędne do skompilowania plików pomocy projektu. Aby uzyskać więcej informacji dotyczących plików tworzonych przez kreatora, zobacz [typy plików utworzonych dla programu Visual Studio C++ projektów](../../build/reference/file-types-created-for-visual-cpp-projects.md)i zobacz plik Readme.txt w projekcie.

## <a name="overview"></a>Omówienie

Ta strona kreatora zawiera opis bieżących ustawień tworzonej aplikacji MFC. Domyślnie kreator tworzy projekt w następujący sposób:

- [Typ aplikacji, kreator aplikacji MFC](../../mfc/reference/application-type-mfc-application-wizard.md)

   - Projekt jest tworzony z obsługą interfejsu kart dla wielu dokumentów (MDI). Aby uzyskać więcej informacji, zobacz [SDI i MDI](../../mfc/sdi-and-mdi.md).

   - Projekt używa [architektury dokument/widok](../../mfc/document-view-architecture.md).

   - Projekt używa bibliotek Unicode.

   - Projekt jest tworzony przy użyciu stylu projektu programu Visual Studio i umożliwia przełączanie stylu wizualnego.

   - Projekt używa biblioteki MFC w udostępnionym pliku DLL. Aby uzyskać więcej informacji, zobacz [Utwórz C /C++ bibliotek DLL w programie Visual Studio](../../build/dlls-in-visual-cpp.md).

- [Obsługa dokumentów złożonych, kreator aplikacji MFC](../../mfc/reference/compound-document-support-mfc-application-wizard.md)

   - Projekt nie obsługuje dokumentów złożonych.

- [Ciągi szablonu dokumentu, kreator aplikacji MFC](../../mfc/reference/document-template-strings-mfc-application-wizard.md)

   - Nazwa projektu jest używana dla ciągów tekstowych domyślnego szablonu dokumentów.

- [Obsługa bazy danych, kreator aplikacji MFC](../../mfc/reference/database-support-mfc-application-wizard.md)

   - Projekt nie obsługuje baz danych.

- [Funkcje interfejsu użytkownika, kreator aplikacji MFC](../../mfc/reference/user-interface-features-mfc-application-wizard.md)

   - Projekt implementuje standardowe Windows funkcje interfejsu użytkownika, takie jak menu systemowe, pasek stanu, maksymalizowania i minimalizowania pól, **o** pole, standardowy pasek menu i pasek narzędzi dokowania oraz ramki podrzędne.

- [Funkcje zaawansowane, kreator aplikacji MFC](../../mfc/reference/advanced-features-mfc-application-wizard.md)

   - Projekt obsługuje drukowanie i podgląd wydruku.

   - Projekt obsługuje kontrolki ActiveX. Aby uzyskać więcej informacji, zobacz [sekwencji operacji tworzenia formantów ActiveX](../../mfc/sequence-of-operations-for-creating-activex-controls.md).

   - Projekt nie obsługuje [automatyzacji](../../mfc/automation.md), [MAPI](../../mfc/mapi-support-in-mfc.md), [Windows Sockets](../../mfc/windows-sockets-in-mfc.md), ani modułu Active Accessibility.

   - Projekt obsługuje **Explorer** okienko dokowania, **dane wyjściowe** okienko dokowania, a **właściwości** okienka dokowania.

- [Klasy generowane, kreator aplikacji MFC](../../mfc/reference/generated-classes-mfc-application-wizard.md)

   - Klasa widoku projektu pochodzi od [CView Class](../../mfc/reference/cview-class.md).

   - Klasa aplikacji projektu pochodzi od [klasa CWinAppEx](../../mfc/reference/cwinappex-class.md).

   - Klasa dokumentów projektu pochodzi od [klasa CDocument](../../mfc/reference/cdocument-class.md).

   - Klasa głównej ramki projektu pochodzi od [klasa CMDIFrameWndEx](../../mfc/reference/cmdiframewndex-class.md).

   - Klasa ramki podrzędnej projektu pochodzi od [klasa CMDIChildWndEx](../../mfc/reference/cmdichildwndex-class.md).

Aby zmienić te domyślne ustawienia, należy kliknąć odpowiedni tytuł karty w lewej kolumnie kreatora i wprowadź zmiany na wyświetlonej stronie.

Po utworzeniu projektu aplikacji MFC, możesz dodać obiekty i kontrolki do projektu przy użyciu języka Visual C++ [kreatorów kodu](../../ide/adding-functionality-with-code-wizards-cpp.md).

## <a name="see-also"></a>Zobacz także

[Tworzenie aplikacji MFC](../../mfc/reference/creating-an-mfc-application.md)<br/>
[Aplikacje klasyczne MFC](../../mfc/mfc-desktop-applications.md)<br/>
[Używanie klas do pisania aplikacji dla systemu Windows](../../mfc/using-the-classes-to-write-applications-for-windows.md)
