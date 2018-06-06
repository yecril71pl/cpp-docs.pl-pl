---
title: MFC Program lub źródło kontroli i pliki nagłówkowe | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- file types [C++], MFC source and header
ms.assetid: f61419a8-bf69-4bbb-8f7c-1734be5e6db6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5ab1ed04b9890fbed8de8b59354ab36d7be063e7
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "33340232"
---
# <a name="mfc-program-or-control-source-and-header-files"></a>Program MFC lub źródło kontroli i pliki nagłówkowe
Następujące pliki są tworzone podczas tworzenia projektu MFC w programie Visual Studio, w zależności od opcji wybranej dla projektu, który można utworzyć. Na przykład projekt zawiera *nazwa_projektu.nazwa_modułu.nazwa_procedury*dlg.cpp i *nazwa_projektu.nazwa_modułu.nazwa_procedury*dlg.h pliki tylko w przypadku tworzenia opartych na oknach dialogowych projektu lub klasy.  
  
 Wszystkie te pliki znajdują się w *nazwa_projektu.nazwa_modułu.nazwa_procedury* katalogu i w folderze pliki nagłówków (.h pliki) lub folderu źródłowego (plików .cpp) w Eksploratorze rozwiązań.  
  
|Nazwa pliku|Opis|  
|---------------|-----------------|  
|*Nazwa_projektu.nazwa_modułu.nazwa_procedury*.h|Pliku dołączanego głównym programu lub DLL. Zawiera wszystkie symbole globalne i `#include` dyrektywy inne pliki nagłówków. Dziedziczy `CPrjnameApp` klasę z `CWinApp` i deklaruje `InitInstance` funkcję elementu członkowskiego. W przypadku formantu `CPrjnameApp` jest pochodną klasy `COleControlModule`.|  
|*Nazwa_projektu.nazwa_modułu.nazwa_procedury*.cpp|Plik źródłowy głównego programu. Tworzy jeden obiekt klasy `CPrjnameApp`, która jest pochodną `CWinApp`i zastępuje `InitInstance` funkcję elementu członkowskiego.<br /><br /> Dla plików wykonywalnych `CPrjnameApp::InitInstance` jest kilka rzeczy. Rejestruje szablonów dokumentów, które stanowią połączenie między dokumentów i widoków; Tworzy główne okno ramowe; tworzy pusty dokument (i otwiera dokument, jeśli jest określony jako argument wiersza polecenia do aplikacji).<br /><br /> Biblioteki dll i ActiveX (dawniej OLE) formantów, `CProjNameApp::InitInstance` rejestruje fabrykę obiektów formantu przez wywołanie OLE `COleObjectFactory::RegisterAll` i nawiązuje połączenie `AfxOLEInit`. Ponadto funkcja członkowska `CProjNameApp::ExitInstance` służy do formantu z pamięci z wywołaniem do zwolnienia **AfxOleTerm**.<br /><br /> Ten plik również rejestruje i wyrejestrowuje formantu w bazie danych rejestracji systemu Windows z zastosowaniem `DllRegisterServer` i `DllUnregisterServer` funkcji.|  
|*Nazwa_projektu.nazwa_modułu.nazwa_procedury*ctrl.h, *nazwa_projektu.nazwa_modułu.nazwa_procedury*ctrl.cpp|Deklarowanie i implementować `CProjnameCtrl` klasy. `CProjnameCtrl` jest pochodną `COleControl`, i szkielet implementacji niektórych funkcji członkowskich zdefiniowanych zainicjować, rysowania i serializacji (przy ładowaniu i zapisywaniu) formantu. Można zdefiniować komunikat, zdarzeń i mapy wysyłania.|  
|*Nazwa_projektu.nazwa_modułu.nazwa_procedury*dlg.cpp, *nazwa_projektu.nazwa_modułu.nazwa_procedury*dlg.h|Utworzony po wybraniu aplikacji opartych na oknach dialogowych. Pliki pochodzić i zaimplementować klasę okna dialogowego o nazwie `CProjnameDlg`i zawiera funkcje Członkowskie szkielet zainicjować okno dialogowe i wykonywać wymiana danych okna dialogowego (DDX). Klasy okien dialogowych o również znajduje się w tych plikach, zamiast w *nazwa_projektu.nazwa_modułu.nazwa_procedury*.cpp.|  
|Dlgproxy.cpp, Dlgproxy.h|W opartych na oknach dialogowych programu, wdrażania i nagłówek plik do projektu klasy serwera proxy automatyzacji dla głównego okna dialogowego. To jest używana tylko w przypadku wybrania Obsługa automatyzacji.|  
|*Nazwa_projektu.nazwa_modułu.nazwa_procedury*doc.cpp, *nazwa_projektu.nazwa_modułu.nazwa_procedury*doc.h|Pochodzić i zaimplementować klasę dokumentu o nazwie `CProjnameDoc`i zawiera funkcje Członkowskie szkielet Inicjowanie dokumentu, serializacji (Zapisywanie i ładowanie) dokumentu oraz wdrożenie Debugowanie diagnostyki.|  
|*Nazwa_projektu.nazwa_modułu.nazwa_procedury*set.h/.cpp|Utworzone w przypadku utworzenia program, który obsługuje bazę danych i zawiera klasę zestawu rekordów.|  
|*Nazwa_projektu.nazwa_modułu.nazwa_procedury*view.cpp, *nazwa_projektu.nazwa_modułu.nazwa_procedury*view.h|Pochodzić i zaimplementować klasę widok o nazwie `CProjnameView`, który służy do wyświetlania i drukowania danych dokumentu. `CProjnameView` Klasa pochodzi od jednej z następujących klas MFC:<br /><br /> -   [CEditView](../mfc/reference/ceditview-class.md)<br />-   [CFormView](../mfc/reference/cformview-class.md)<br />-   [CRecordView](../mfc/reference/crecordview-class.md)<br />-   [Coledbrecordview —](../mfc/reference/coledbrecordview-class.md)<br />-   [CTreeView —](../mfc/reference/ctreeview-class.md)<br />-   [Clistview —](../mfc/reference/clistview-class.md)<br />-   [Cricheditview —](../mfc/reference/cricheditview-class.md)<br />-   [CScrollView](../mfc/reference/cscrollview-class.md)<br />-   [Cview —](../mfc/reference/cview-class.md)<br />-   [CHTMLView](../mfc/reference/chtmlview-class.md)<br />-   [CHTMLEditView](../mfc/reference/chtmleditview-class.md)<br /><br /> Klasa widoku projektu zawiera funkcje Członkowskie szkielet widoku i wdrożenie Debugowanie diagnostyki. Jeśli włączono obsługę drukowania, następnie wpisy mapy wiadomości są dodawane do drukowanie, ustawienia drukowania i Drukuj komunikaty poleceń w wersji zapoznawczej. Te wpisy wywołać odpowiednie funkcje Członkowskie w klasie podstawowej widoku.|  
|*Nazwa_projektu.nazwa_modułu.nazwa_procedury*PropPage.h, *nazwa_projektu.nazwa_modułu.nazwa_procedury*PropPage.cpp|Deklarowanie i implementować `CProjnamePropPage` klasy. `CProjnamePropPage` jest pochodną `COlePropertyPage` i funkcją członkowską szkielet `DoDataExchange`, jest dostępne do zaimplementowania wymiany danych i weryfikacji.|  
|IPframe.cpp, IPframe.h|Jeśli wybrano opcję mini serwer lub pełny serwer w Kreatorze aplikacji utworzony **opcje automatyzacji** (krok 3 6). Pliki pochodzić i zaimplementować klasę okna ramowe w miejscu o nazwie **CInPlaceFrame**, używany, gdy serwer działa w miejscu aktywowany przez program kontenera.|  
|Mainfrm.cpp, Mainfrm.h|Pochodzi **cmainframe —** klasy z dowolnej [cframewnd —](../mfc/reference/cframewnd-class.md) (dla aplikacji SDI) lub [cmdiframewnd —](../mfc/reference/cmdiframewnd-class.md) (dla aplikacji MDI). **Cmainframe —** klasa obsługuje tworzenie przycisków paska narzędzi i paska stanu, jeśli nie wybrano odpowiednie opcje w Kreatorze aplikacji **Opcje aplikacji** (krok 4 6). Aby uzyskać informacje na temat używania **cmainframe —**, zobacz [okno ramowe klasy tworzone przez Kreatora aplikacji](../mfc/frame-window-classes-created-by-the-application-wizard.md).|  
|Childfrm.cpp, Childfrm.h|Pochodzi **CChildFrame** klasę z [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md). **CChildFrame** klasa jest używana dla okien ramowych dokumentu MDI. Te pliki są zawsze tworzone, jeśli zostanie wybrana opcja MDI.|  
  
## <a name="see-also"></a>Zobacz też  
 [Typy plików utworzonych dla projektów Visual C++](../ide/file-types-created-for-visual-cpp-projects.md)   
 [ATL Program lub źródło kontroli i pliki nagłówkowe](../ide/atl-program-or-control-source-and-header-files.md)   
 [Projekty CLR](../ide/files-created-for-clr-projects.md)