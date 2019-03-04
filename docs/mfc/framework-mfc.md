---
title: Struktura (MFC)
ms.date: 11/04/2016
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
ms.openlocfilehash: 933fcf97c24ed0903395e2c718f8c89d42473494
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57269022"
---
# <a name="framework-mfc"></a>Struktura (MFC)

Swoją pracę za pomocą framework biblioteki Microsoft Foundation Class (MFC) zależy głównie kilka głównych klas i kilka narzędzi Visual C++. Niektóre klasy hermetyzować dużą część interfejsu programowania aplikacji (API) systemu Win32. Inne klasy hermetyzować aplikacji pojęć, takich jak dokumenty, widoki i samej aplikacji. Nadal hermetyzować inne funkcje OLE i ODBC i DAO możliwości dostępu do danych.

Na przykład w Win32 koncepcji okna jest hermetyzowany przez klasę MFC `CWnd`. Oznacza to, o nazwie klasy języka C++ `CWnd` hermetyzuje lub "opakowuje" `HWND` uchwyt, który reprezentuje okno programu Windows. Podobnie, klasy `CDialog` hermetyzuje Win32, okno dialogowe.

Hermetyzacja oznacza, że klasy C++ `CWnd`, na przykład zawiera zmienną składową typu `HWND`, i funkcje składowych klasy hermetyzacji wywołania funkcji Win32, które przyjmują `HWND` jako parametr. Funkcje składowych klasy mają zwykle taką samą nazwę jak funkcję Win32, które one hermetyzacji.

## <a name="in-this-section"></a>W tej sekcji

[SDI i MDI](../mfc/sdi-and-mdi.md)

[Dokumenty, widoki i struktura](../mfc/documents-views-and-the-framework.md)

[Kreatorzy i edytory zasobów](../mfc/wizards-and-the-resource-editors.md)

## <a name="in-related-sections"></a>W sekcje pokrewne

[Opieranie się na strukturze](../mfc/building-on-the-framework.md)

[Jak struktura wywołuje kod](../mfc/how-the-framework-calls-your-code.md)

[CWinApp: Klasa aplikacji](../mfc/cwinapp-the-application-class.md)

[Szablony dokumentów i proces tworzenia dokumentu/widoku](../mfc/document-templates-and-the-document-view-creation-process.md)

[Obsługa i mapowanie komunikatów](../mfc/message-handling-and-mapping.md)

[Obiekty okna](../mfc/window-objects.md)

## <a name="see-also"></a>Zobacz także

[Używanie klas do pisania aplikacji dla systemu Windows](../mfc/using-the-classes-to-write-applications-for-windows.md)
