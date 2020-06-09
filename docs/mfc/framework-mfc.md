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
ms.openlocfilehash: b02d5a1862a278f46591895f20f58a97367b5ab2
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618796"
---
# <a name="framework-mfc"></a>Struktura (MFC)

Twoja współpraca z platformą Microsoft Foundation Class (MFC) jest oparta na kilku najważniejszych klasach i kilku Visual C++ narzędziach. Niektóre klasy hermetyzowają znaczną część interfejsu programowania aplikacji Win32 (API). Inne klasy hermetyzowają koncepcje aplikacji, takie jak dokumenty, widoki i sama aplikacja. Inne funkcje OLE i ODBC oraz funkcje dostępu do danych DAO są nadal inne.  (Obiekt DAO jest obsługiwany przez pakiet Office 2013. Element DAO 3,6 jest wersją ostateczną i jest uznawany za przestarzały.

Na przykład Win32's koncepcji okna jest hermetyzowane przez klasę MFC `CWnd` . Oznacza to, że Klasa języka C++ nazywa się `CWnd` hermetyzacją lub "zawija" `HWND` uchwyt, który reprezentuje okno systemu Windows. Podobnie Klasa `CDialog` hermetyzuje okna dialogowe Win32.

Hermetyzacja oznacza, że Klasa C++ `CWnd` , na przykład, zawiera zmienną elementu członkowskiego typu `HWND` , i funkcje składowe klasy hermetyzują wywołania do funkcji Win32, które przyjmują `HWND` jako parametr. Funkcje składowe klasy zazwyczaj mają taką samą nazwę jak funkcja Win32, która hermetyzuje.

## <a name="in-this-section"></a>W tej sekcji

[SDI i MDI](sdi-and-mdi.md)

[Dokumenty, widoki i struktura](documents-views-and-the-framework.md)

[Kreatorzy i edytory zasobów](wizards-and-the-resource-editors.md)

## <a name="in-related-sections"></a>W sekcjach pokrewnych

[Opieranie się na strukturze](building-on-the-framework.md)

[Jak struktura wywołuje kod](how-the-framework-calls-your-code.md)

[CWinApp: klasa aplikacji](cwinapp-the-application-class.md)

[Szablony dokumentów i proces tworzenia dokumentu/widoku](document-templates-and-the-document-view-creation-process.md)

[Obsługa i mapowanie komunikatów](message-handling-and-mapping.md)

[Obiekty okien](window-objects.md)

## <a name="see-also"></a>Zobacz też

[Używanie klas do pisania aplikacji dla systemu Windows](using-the-classes-to-write-applications-for-windows.md)
