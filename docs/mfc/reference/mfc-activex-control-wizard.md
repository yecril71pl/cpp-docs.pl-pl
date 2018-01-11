---
title: "Kreator formantów MFC ActiveX | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.appwiz.mfc.ctl.overview
dev_langs: C++
helpviewer_keywords:
- ActiveX controls [MFC], MFC
- MFC ActiveX controls [MFC], wizards
- OLE controls [MFC], creating
- MFC ActiveX Control Wizard
- OLE controls [MFC]
ms.assetid: f19d698c-bdc3-4c74-af97-3d6ccb441b75
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 82e562ceb73da2b103360ab9607cecbbe9f1da02
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="mfc-activex-control-wizard"></a>Kreator kontrolek ActiveX MFC
Formant ActiveX jest określonego typu [serwer automatyzacji](../../mfc/automation-servers.md); jest komponentów wielokrotnego użytku. Hosting kontrolki ActiveX aplikacji jest [klienta automatyzacji](../../mfc/automation-clients.md) tego formantu. Jeśli do utworzenia komponentów wielokrotnego użytku, użyj tego kreatora można utworzyć formantu. Zobacz [kontrolki ActiveX MFC](../../mfc/mfc-activex-controls.md) Aby uzyskać więcej informacji.  
  
 Alternatywnie można utworzyć automatyzacji serwera MFC aplikację przy użyciu [Kreator aplikacji MFC](../../mfc/reference/mfc-application-wizard.md).  
  
 Formantu ActiveX utworzona za pomocą tego kreatora można mieć interfejsu użytkownika lub może być niewidoczny. Można określić tę opcję w [ustawienia kontroli](../../mfc/reference/control-settings-mfc-activex-control-wizard.md) strony kreatora. Formant czasomierza jest przykładem formantu ActiveX, który ma być niewidoczna.  
  
 Kontrolki ActiveX ma interfejs użytkownika złożonych. Niektóre kontrolki mogą być takie jak formularze hermetyzowany: jeden formant zawierający wiele pola każdego w osobnym kontrolki systemu Windows. Na przykład obiekt części automatycznie zaimplementowane jako kontrolki MFC ActiveX mogą stanowić interfejs użytkownika przypominającej formularza za pomocą którego użytkownicy mogą odczytywać i edytować numer części, Nazwa części i inne informacje. Zobacz [kontrolki ActiveX MFC](../../mfc/mfc-activex-controls.md) Aby uzyskać więcej informacji.  
  
 Jeśli musisz utworzyć kontener dla obiektów ActiveX, zobacz [Tworzenie kontenera formantu ActiveX](../../mfc/reference/creating-an-mfc-activex-control-container.md).  
  
 MFC starter program zawiera pliki źródłowe (.cpp) C++, pliki zasobów (.rc) i pliku projektu (.vcxproj). Kod wygenerowany w tych plikach starter jest oparta na MFC.  
  
 Na poniższej liście próbki przedstawiono zadania i typy rozszerzeń dla formantu ActiveX:  
  
-   [Optymalizacja formantu ActiveX](../../mfc/mfc-activex-controls-optimization.md)  
  
-   [Dodawanie zdarzeń standardowych do formantu ActiveX](../../mfc/mfc-activex-controls-adding-stock-events-to-an-activex-control.md)  
  
-   [Dodawanie zdarzeń niestandardowych](../../mfc/mfc-activex-controls-adding-custom-events.md)  
  
-   [Dodawanie metod standardowych](../../mfc/mfc-activex-controls-adding-stock-methods.md)  
  
-   [Dodawanie metod niestandardowych](../../mfc/mfc-activex-controls-adding-custom-methods.md)  
  
-   [Dodawanie właściwości standardowych](../../mfc/mfc-activex-controls-adding-stock-properties.md)  
  
-   [Dodawanie właściwości niestandardowych](../../mfc/mfc-activex-controls-adding-custom-properties.md)  
  
-   [Programowanie formantów ActiveX w kontenerze formantów ActiveX](../../mfc/programming-activex-controls-in-a-activex-control-container.md)  
  
## <a name="overview"></a>Omówienie  
 Ta strona kreatora opisano bieżące ustawienia aplikacji dla tworzonego projektu formantu MFC ActiveX. Domyślnie kreator tworzy projekt w następujący sposób:  
  
-   Domyślny projekt generuje żadnych plików licencji lub Pomoc środowiska wykonawczego. Te ustawienia domyślne można zmienić na [ustawienia aplikacji](../../mfc/reference/application-settings-mfc-activex-control-wizard.md) strony. Tylko wybrane elementy na tej stronie Kreator kontrolek ActiveX zostaną odzwierciedlone na **omówienie** strony.  
  
-   Projekt zawiera klasę formantu i klasy strony właściwości, na podstawie nazwy projektu. Można edytować nazwy nazwy projektu i pliku na [nazwy formantów](../../mfc/reference/control-names-mfc-activex-control-wizard.md) strony.  
  
-   Kontrolka jest oparta na nie istniejącego formantu systemu Windows, aktywuje staje się widoczna, interfejs użytkownika, a obejmuje **o** okno dialogowe. Te ustawienia domyślne można zmienić na [ustawienia kontroli](../../mfc/reference/control-settings-mfc-activex-control-wizard.md) strony.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie i zarządzanie projektami Visual C++](../../ide/creating-and-managing-visual-cpp-projects.md)   
 [Typy projektów Visual C++](../../ide/visual-cpp-project-types.md)   
 [Pojęcia](../../atl/active-template-library-atl-concepts.md)

