---
title: Struktura (MFC) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 09be7a5efbf3f78aa3cbc1862b811fff3d487c75
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="framework-mfc"></a>Struktura (MFC)
Swoją pracę dzięki framework biblioteki Microsoft Foundation Class (MFC) jest przede wszystkim na podstawie kilku główne kategorie i kilka narzędzi Visual C++. Niektóre klasy hermetyzować duża część interfejsu programowania aplikacji (API) Win32. Inne klasy hermetyzować pojęcia dotyczące aplikacji, takich jak dokumenty, widoki i aplikacji. Nadal innym hermetyzować OLE funkcje i możliwości dostępu do danych ODBC i DAO.  
  
 Na przykład koncepcji Win32 dla okna jest hermetyzowany przez klasę MFC `CWnd`. Oznacza to, o nazwie klasy C++ `CWnd` hermetyzuje lub "opakowuje" `HWND` uchwytu, który reprezentuje okna systemu Windows. Podobnie, klasa `CDialog` hermetyzuje Win32 okien dialogowych.  
  
 Hermetyzacja oznacza, że klasa C++ `CWnd`, na przykład zawiera zmienną członkowską typu `HWND`, i funkcje elementów członkowskich klasy Hermetyzowanie wywołania funkcji Win32, które przyjmują `HWND` jako parametr. Funkcje Członkowskie klasy zwykle mają taką samą nazwę jak funkcja Win32, które hermetyzują one.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Używanie klas do pisania aplikacji dla systemu Windows](../mfc/using-the-classes-to-write-applications-for-windows.md)
