---
title: Struktura (MFC)
ms.date: 09/17/2019
helpviewer_keywords:
- encapsulation [MFC], Win32 API
- MFC, application framework
- wrapper classes [MFC], explained
- Win32 [MFC], API encapsulation by MFC
- application framework [MFC], about MFC application framework
- APIs [MFC], encapsulation by MFC Win32
- encapsulation [MFC]
- Windows API [MFC], encapsulation by MFC
- encapsulated Win32 API [MFC]
ms.assetid: 3be0fec8-9843-4119-ae42-ece993ef500b
ms.openlocfilehash: d93d2d50bab4b63258a3e0fe4cd2f24c2fcde4f3
ms.sourcegitcommit: 2f96e2fda591d7b1b28842b2ea24e6297bcc3622
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2019
ms.locfileid: "71095792"
---
# <a name="framework-mfc"></a>Struktura (MFC)

Twoja współpraca z platformą Microsoft Foundation Class (MFC) jest oparta na kilku najważniejszych klasach i kilku narzędziach wizualnych C++ . Niektóre klasy hermetyzowają znaczną część interfejsu programowania aplikacji Win32 (API). Inne klasy hermetyzowają koncepcje aplikacji, takie jak dokumenty, widoki i sama aplikacja. Inne funkcje OLE i ODBC oraz funkcje dostępu do danych DAO są nadal inne.  (Obiekt DAO jest obsługiwany przez pakiet Office 2013. Element DAO 3,6 jest wersją ostateczną i jest uznawany za przestarzały.

Na przykład Win32's koncepcji okna jest hermetyzowane przez klasę `CWnd`MFC. Oznacza to, że C++ Klasa nazywa `CWnd` się hermetyzacją lub " `HWND` zawija" uchwyt, który reprezentuje okno systemu Windows. Podobnie Klasa `CDialog` hermetyzuje okna dialogowe Win32.

Hermetyzacja oznacza, że C++ Klasa `CWnd`, na przykład, zawiera zmienną składową typu `HWND`, i funkcje składowe klasy hermetyzują `HWND` wywołania do funkcji Win32, które przyjmują jako parametr. Funkcje składowe klasy zazwyczaj mają taką samą nazwę jak funkcja Win32, która hermetyzuje.

## <a name="in-this-section"></a>W tej sekcji

[SDI i MDI](../mfc/sdi-and-mdi.md)

[Dokumenty, widoki i struktura](../mfc/documents-views-and-the-framework.md)

[Kreatorzy i edytory zasobów](../mfc/wizards-and-the-resource-editors.md)

## <a name="in-related-sections"></a>W sekcjach pokrewnych

[Opieranie się na strukturze](../mfc/building-on-the-framework.md)

[Jak struktura wywołuje kod](../mfc/how-the-framework-calls-your-code.md)

[CWinApp: klasa aplikacji](../mfc/cwinapp-the-application-class.md)

[Szablony dokumentów i proces tworzenia dokumentu/widoku](../mfc/document-templates-and-the-document-view-creation-process.md)

[Obsługa i mapowanie komunikatów](../mfc/message-handling-and-mapping.md)

[Obiekty okna](../mfc/window-objects.md)

## <a name="see-also"></a>Zobacz także

[Używanie klas do pisania aplikacji dla systemu Windows](../mfc/using-the-classes-to-write-applications-for-windows.md)
