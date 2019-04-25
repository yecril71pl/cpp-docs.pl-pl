---
title: Program MFC lub źródło kontroli i pliki nagłówkowe
ms.date: 11/04/2016
helpviewer_keywords:
- file types [C++], MFC source and header
ms.assetid: f61419a8-bf69-4bbb-8f7c-1734be5e6db6
ms.openlocfilehash: a46fedc9f9bbc888e9b59d2ed313eaf7146394ff
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62321322"
---
# <a name="mfc-program-or-control-source-and-header-files"></a>Program MFC lub źródło kontroli i pliki nagłówkowe

Następujące pliki są tworzone podczas tworzenia projektu MFC w programie Visual Studio, w zależności od opcji wybranej dla tworzonego projektu. Na przykład projekt zawiera *Projname*dlg.cpp i *Projname*dlg.h pliki tylko wtedy, gdy tworzysz oparte o okna dialogowe projektu lub klasy.

Wszystkie te pliki znajdują się w *Projname* katalogu, a w folderze pliki nagłówków (.h pliki) lub pliki źródłowe (.cpp pliki) folder w Eksploratorze rozwiązań.

|Nazwa pliku|Opis|
|---------------|-----------------|
|*Projname*.h|Plik dołączania głównego programu lub DLL. Zawiera on wszystkie symbole globalne i `#include` dyrektywy dla innych plików nagłówkowych. Pochodzi `CPrjnameApp` klasy z `CWinApp` i deklaruje `InitInstance` funkcja elementu członkowskiego. W przypadku formantu `CPrjnameApp` klasa pochodzi od `COleControlModule`.|
|*Projname*.cpp|Plik źródłowy głównego programu. Tworzy jeden obiekt klasy `CPrjnameApp`, który pochodzi od `CWinApp`i zastępuje `InitInstance` funkcja elementu członkowskiego.<br /><br /> Dla plików wykonywalnych `CPrjnameApp::InitInstance` wykonuje kilka operacji. Rejestruje szablonów dokumentów, które służą jako połączenie między dokumentami i widokami; Tworzy ramką głównego okna; tworzy pusty dokument (i zostanie otwarty dokument, jeśli mapa została określona jako argument wiersza polecenia do aplikacji).<br /><br /> Biblioteki dll i ActiveX (dawniej OLE) formantów, `CProjNameApp::InitInstance` rejestruje formantu fabryki obiektów OLE poprzez wywołanie `COleObjectFactory::RegisterAll` i sprawia, że wywołanie `AfxOLEInit`. Ponadto funkcja elementu członkowskiego `CProjNameApp::ExitInstance` służy do zwolnienia kontrolki z pamięci z wywołaniem do **AfxOleTerm**.<br /><br /> Ten plik również rejestruje i wyrejestrowuje kontroli w bazie danych rejestracji Windows poprzez implementację `DllRegisterServer` i `DllUnregisterServer` funkcji.|
|*Projname*ctrl.h, *Projname*ctrl.cpp|Deklarowanie i zaimplementować `CProjnameCtrl` klasy. `CProjnameCtrl` jest tworzony na podstawie `COleControl`, szkielet implementacje niektórych funkcji składowych, są one definiowane zainicjować, rysowania i serializacji (ładowania i zapisywania) kontrolki. Komunikat, zdarzeń i mapy wysyłania również są zdefiniowane.|
|*Projname*dlg.cpp, *Projname*dlg.h|Utworzone, jeśli wybrana aplikacja oparta na oknach dialogowych. Pliki pochodzić i implementowanie klasy okien dialogowych, o nazwie `CProjnameDlg`i obejmują funkcje Członkowskie szkielet zainicjować okno dialogowe i wykonywać wymiana danych okna dialogowego (DDX). Klasy okien dialogowych o znajduje się również w tych plikach, a nie w *Projname*.cpp.|
|Dlgproxy.cpp, Dlgproxy.h|W oparta na oknach dialogowych programu, wdrażania i nagłówek pliku do projektu klasy proxy automatyzacji dla głównego okna dialogowego. To jest używana tylko w przypadku wybrania Obsługa automatyzacji.|
|*Projname*doc.cpp, *Projname*doc.h|Pochodzić i implementowanie klasy dokumentu o nazwie `CProjnameDoc`i obejmują funkcje Członkowskie szkielet Inicjowanie dokumentu, serializacji (Zapisywanie i ładowanie) dokumentu i implementacji, debugowanie i Diagnostyka.|
|*Projname*set.h/.cpp|Utworzone, jeśli tworzysz program, który obsługuje bazę danych i zawiera klasę zestawu rekordów.|
|*Projname*view.cpp, *Projname*view.h|Pochodzić i zaimplementować Wyświetl klasę o nazwie `CProjnameView`, używany do wyświetlania i drukowanie danych dokumentu. `CProjnameView` Klasa pochodzi od jednej z następujących klas MFC:<br /><br />- [Elementu CEditView](../../mfc/reference/ceditview-class.md)<br />- [CFormView](../../mfc/reference/cformview-class.md)<br />- [CRecordView](../../mfc/reference/crecordview-class.md)<br />- [COleDBRecordView](../../mfc/reference/coledbrecordview-class.md)<br />- [CTreeView](../../mfc/reference/ctreeview-class.md)<br />- [CListView](../../mfc/reference/clistview-class.md)<br />- [CRichEditView](../../mfc/reference/cricheditview-class.md)<br />- [CScrollView](../../mfc/reference/cscrollview-class.md)<br />- [CView](../../mfc/reference/cview-class.md)<br />- [CHTMLView](../../mfc/reference/chtmlview-class.md)<br />- [CHTMLEditView](../../mfc/reference/chtmleditview-class.md)<br /><br /> Klasa widoku projektu zawiera funkcje Członkowskie szkielet Rysowanie w widoku i implementacji, debugowanie i Diagnostyka. Jeśli włączono obsługę drukowania, następnie wpisy mapy komunikatów są dodawane do drukowania lub wydrukować instalacji i Drukuj komunikaty o polecenia w wersji zapoznawczej. Te wpisy wywołać odpowiednie funkcje elementów członkowskich w klasie widoku podstawowego.|
|*Projname*PropPage.h, *Projname*PropPage.cpp|Deklarowanie i zaimplementować `CProjnamePropPage` klasy. `CProjnamePropPage` jest tworzony na podstawie `COlePropertyPage` i funkcją składową szkielet `DoDataExchange`, jest dostarczany w celu zaimplementowania wymiany danych i sprawdzania poprawności.|
|IPframe.cpp, IPframe.h|Utworzony, jeśli wybrano opcję mini serwer lub pełny serwer w Kreatorze aplikacji **opcje automatyzacji** strony (krok 3 z 6). Pliki pochodzić i implementowanie klasy okien ramowych w miejscu, o nazwie **CInPlaceFrame**, używany, gdy serwer jest w miejscu aktywowany przez program kontenera.|
|Mainfrm.cpp, Mainfrm.h|Pochodzi **cmainframe —** klasy z poziomu [CFrameWnd](../../mfc/reference/cframewnd-class.md) (dla aplikacji interfejsu SDI) lub [CMDIFrameWnd](../../mfc/reference/cmdiframewnd-class.md) (dla aplikacji MDI). **Cmainframe —** klasy obsługuje tworzenie przycisków paska narzędzi i pasek stanu, wybranie odpowiedniej opcji w Kreatorze aplikacji **Opcje aplikacji** strony (krok 4 z 6). Aby uzyskać informacje na temat korzystania z **cmainframe —**, zobacz [okno ramowe klasy tworzone przez Kreatora aplikacji](../../mfc/frame-window-classes-created-by-the-application-wizard.md).|
|Childfrm.cpp, Childfrm.h|Pochodzi **CChildFrame** klasy z [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md). **CChildFrame** klasa jest używana dla okien ramowych dokumentu MDI. Te pliki są zawsze tworzone w przypadku wybrania opcji MDI.|

## <a name="see-also"></a>Zobacz także

[Typy plików utworzonych dla projektów Visual C++](file-types-created-for-visual-cpp-projects.md)<br>
[Program ATL lub źródło kontroli i pliki nagłówkowe](atl-program-or-control-source-and-header-files.md)<br>
[Projekty CLR](files-created-for-clr-projects.md)
