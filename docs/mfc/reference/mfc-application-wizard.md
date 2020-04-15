---
title: Kreator aplikacji MFC
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfc.exe.overview
helpviewer_keywords:
- MFC Application Wizard
- executable files, creating
ms.assetid: 227ac090-921d-4b2f-be0a-66a5f4cab0d4
ms.openlocfilehash: 6949f136890e8274f225a49496b2eb1b8f78b6fc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81351833"
---
# <a name="mfc-application-wizard"></a>Kreator aplikacji MFC

Kreator aplikacji MFC tworzy aplikację, która po skompilowaniu implementuje podstawowe funkcje aplikacji wykonywalnej systemu Windows (.exe). Aplikacja startowa MFC starter zawiera pliki źródłowe (.cpp) języka C++, pliki zasobów (.rc), pliki nagłówków (.h) i pliki projektu (.vcxproj). Kod generowany w tych plikach startowych jest oparty na bibliotece MFC.

> [!NOTE]
> Zależnie od wybranych opcji kreator tworzy dodatkowe pliki w projekcie. Na przykład jeśli **wybierzesz pomoc kontekstową** na stronie [Funkcje zaawansowane,](../../mfc/reference/advanced-features-mfc-application-wizard.md) kreator utworzy pliki, które są niezbędne do skompilowania plików Pomocy projektu. Aby uzyskać więcej informacji na temat plików tworzonych przez kreatora, zobacz [Typy plików utworzone dla projektów programu Visual Studio C++](../../build/reference/file-types-created-for-visual-cpp-projects.md)i zobacz plik Readme.txt w projekcie.

## <a name="overview"></a>Omówienie

Ta strona kreatora zawiera opis bieżących ustawień tworzonej aplikacji MFC. Domyślnie kreator tworzy projekt w następujący sposób:

- [Typ aplikacji, kreator aplikacji MFC](../../mfc/reference/application-type-mfc-application-wizard.md)

  - Projekt jest tworzony z obsługą interfejsu kart dla wielu dokumentów (MDI). Aby uzyskać więcej informacji, zobacz [SDI i MDI](../../mfc/sdi-and-mdi.md).

  - W projekcie użyto [architektury dokumentu/widoku](../../mfc/document-view-architecture.md).

  - Projekt używa bibliotek Unicode.

  - Projekt jest tworzony przy użyciu stylu projektu programu Visual Studio i umożliwia przełączanie stylu wizualnego.

  - Projekt używa biblioteki MFC w udostępnionym pliku DLL. Aby uzyskać więcej informacji, zobacz [Tworzenie bibliotek DLL języka C/C++ w programie Visual Studio](../../build/dlls-in-visual-cpp.md).

- [Obsługa dokumentów złożonych, kreator aplikacji MFC](../../mfc/reference/compound-document-support-mfc-application-wizard.md)

  - Projekt nie obsługuje dokumentów złożonych.

- [Ciągi szablonu dokumentu, kreator aplikacji MFC](../../mfc/reference/document-template-strings-mfc-application-wizard.md)

  - Nazwa projektu jest używana dla ciągów tekstowych domyślnego szablonu dokumentów.

- [Obsługa bazy danych, kreator aplikacji MFC](../../mfc/reference/database-support-mfc-application-wizard.md)

  - Projekt nie obsługuje baz danych.

- [Funkcje interfejsu użytkownika, kreator aplikacji MFC](../../mfc/reference/user-interface-features-mfc-application-wizard.md)

  - Projekt implementuje standardowe funkcje interfejsu użytkownika systemu Windows, takie jak menu systemowe, pasek stanu, maksymalizacja i minimalizowanie pól, pole **Informacje,** standardowy pasek menu i pasek narzędzi dokowania oraz ramki podrzędne.

- [Funkcje zaawansowane, kreator aplikacji MFC](../../mfc/reference/advanced-features-mfc-application-wizard.md)

  - Projekt obsługuje drukowanie i podgląd wydruku.

  - Projekt obsługuje kontrolki ActiveX. Aby uzyskać więcej informacji, zobacz [Sekwencja operacji tworzenia formantów ActiveX](../../mfc/sequence-of-operations-for-creating-activex-controls.md).

  - Projekt nie zapewnia obsługi [automatyzacji,](../../mfc/automation.md) [MAPI,](../../mfc/mapi-support-in-mfc.md) [gniazd systemu Windows](../../mfc/windows-sockets-in-mfc.md)ani aktywnej ułatwień dostępu.

  - Projekt obsługuje okienko dokowania **Eksploratora,** okienko dokowania **wyjściowego** i okienko dokowania **Właściwości.**

- [Klasy generowane, kreator aplikacji MFC](../../mfc/reference/generated-classes-mfc-application-wizard.md)

  - Klasa widoku projektu jest pochodną [klasy CView](../../mfc/reference/cview-class.md).

  - Klasa aplikacji projektu jest pochodną [klasy CWinAppEx](../../mfc/reference/cwinappex-class.md).

  - Klasa dokumentu projektu pochodzi od [klasy CDocument](../../mfc/reference/cdocument-class.md).

  - Klasa ramki głównej projektu pochodzi od [klasy CMDIFrameWndEx](../../mfc/reference/cmdiframewndex-class.md).

  - Klasa ramki podrzędnej projektu jest pochodną [klasy CMDIChildWndEx](../../mfc/reference/cmdichildwndex-class.md).

Aby zmienić te domyślne ustawienia, należy kliknąć odpowiedni tytuł karty w lewej kolumnie kreatora i wprowadź zmiany na wyświetlonej stronie.

Po utworzeniu projektu aplikacji MFC można dodawać obiekty lub formanty do projektu za pomocą [kreatorów kodu](../../ide/adding-functionality-with-code-wizards-cpp.md)Visual C++.

## <a name="see-also"></a>Zobacz też

[Tworzenie aplikacji MFC](../../mfc/reference/creating-an-mfc-application.md)<br/>
[Aplikacje klasyczne MFC](../../mfc/mfc-desktop-applications.md)<br/>
[Używanie klas do pisania aplikacji dla systemu Windows](../../mfc/using-the-classes-to-write-applications-for-windows.md)
