---
title: Typ aplikacji, Kreator aplikacji MFC | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.appwiz.mfc.exe.apptype
dev_langs:
- C++
helpviewer_keywords:
- static libraries, MFC
ms.assetid: c3f62b0e-3f13-42c5-9859-d3890d0c3e1d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 45253eed40e9a79dbcb372f63cc44aaeb99edbe0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="application-type-mfc-application-wizard"></a>Typ aplikacji, kreator aplikacji MFC
Ta strona [Kreator aplikacji MFC](../../mfc/reference/mfc-application-wizard.md) do projektowania i dodać podstawowe funkcje do nowej aplikacji MFC.  
  
 **Typ aplikacji**  
 Określa typ obsługi dokumentu, który ma zostać utworzony w aplikacji. Typ aplikacji, którą wybierzesz Określa opcje interfejsu użytkownika, które są dostępne dla aplikacji. Zobacz [funkcje interfejsu użytkownika, Kreator aplikacji MFC](../../mfc/reference/user-interface-features-mfc-application-wizard.md) Aby uzyskać więcej informacji.  
  
 Aby uzyskać więcej informacji na temat typów dokumentów Zobacz:  
  
-   [SDI i MDI](../../mfc/sdi-and-mdi.md)  
  
-   [Okna ramowe](../../mfc/frame-windows.md)  
  
-   [Klasy okien ramowych](../../mfc/frame-window-classes.md)  
  
-   [Dokumenty, widoki i struktura](../../mfc/documents-views-and-the-framework.md)  
  
-   [Okna dialogowe](../../mfc/dialog-boxes.md)  
  
|Opcja|Opis|  
|------------|-----------------|  
|**Pojedynczego dokumentu**|Tworzy to architektura interfejsu (SDI) pojedynczego dokumentu dla aplikacji, w którym na podstawie klasy widoku [cview — klasa](../../mfc/reference/cview-class.md). Można zmienić klasę podstawową dla widoku w [klasy generowane, Kreator aplikacji MFC](../../mfc/reference/generated-classes-mfc-application-wizard.md) stronie kreatora. Do tworzenia aplikacji opartej na formularzu, na przykład użyć [klasy CFormView](../../mfc/reference/cformview-class.md) w klasie widoku.<br /><br /> Tego rodzaju aplikacji dokumentu ramkę okna może zawierać tylko jeden dokument.|  
|**Wiele dokumentów**|Tworzy wiele architektury interfejsu (MDI) dokument dla aplikacji, w którym na podstawie klasy widoku `CView`. Można zmienić klasę podstawową dla widoku w **wygenerowane klasy** stronie kreatora. Do tworzenia aplikacji opartej na formularzu, na przykład użyć `CFormView` w klasie widoku.<br /><br /> Tego rodzaju aplikacji dokumentu ramkę okna może zawierać wielu podrzędnych systemu windows.|  
|**Dokumenty z kartami**|Umieszcza każdy dokument na osobnej karcie.|  
|**Okno dialogowe na podstawie**|Tworzy to architektura opartych na oknach dialogowych, gdzie na podstawie klasy okien dialogowych aplikacji `CDialog`. (Aby utworzyć okno dialogowe HTML, zaznacz pole **HTML użyj okna dialogowego**.)|  
|**Okno dialogowe HTML**|Okno dialogowe pola tylko dla aplikacji. Klasy okien dialogowych z pochodzi [klasy CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md) zamiast [cdialog — klasa](../../mfc/reference/cdialog-class.md). Po zaznaczeniu tego pola `CDHtmlDialog` ma na liście **klasa podstawowa** polu [klasy generowane, Kreator aplikacji MFC](../../mfc/reference/generated-classes-mfc-application-wizard.md) stronie kreatora.<br /><br /> A `CDHtmlDialog`— okno dialogowe pochodnej Wyświetla okna dialogowe oparty na języku HTML, wymiany danych za pomocą HTML kontrolki i obsługuje zdarzenia HTML.|  
|**Wiele dokumentów najwyższego poziomu**|Tworzy wiele architektura najwyższego poziomu dla aplikacji, w którym na podstawie klasy widoku `CView`.<br /><br /> Tego rodzaju aplikacji, gdy użytkownik kliknie **nowy** (lub **nowej ramki**) na **pliku** menu, aplikacja tworzy okno, których elementem nadrzędnym jest niejawnie pulpitu. Nowej ramki dokumentu zostanie wyświetlona na pasku zadań i nie jest ograniczona do obszaru klienckiego okna aplikacji.|  
  
 **Wsparcie dla architektury dokument/widok**  
 Określa, czy dołączać architektury dokument/widok w aplikacji przy użyciu [cdocument — klasa](../../mfc/reference/cdocument-class.md) i [cview — klasa](../../mfc/reference/cview-class.md) (ustawienie domyślne). Wyczyść to pole wyboru, jeśli są eksportowanie aplikacji innego typu niż MFC lub jeśli chcesz zmniejszyć rozmiar skompilowanego pliku wykonywalnego. Domyślnie jest pochodną aplikacji bez architektury dokument/widok [cwinapp — klasa](../../mfc/reference/cwinapp-class.md), i nie zawiera obsługę MFC otwarcie dokumentu z pliku na dysku.  
  
 **Język zasobu**  
 Określa język zasobów. Zostanie wyświetlona lista języków dostępnych w systemie, jak instalowane przez program Visual Studio. Jeśli chcesz wybrać języku innym niż język, musi być zainstalowany w folderze szablonów odpowiednie dla tego języka. Aby uzyskać więcej informacji o instalowaniu zasobów językowych inne niż domyślne dostępne w **języka zasobu** listę, zobacz [Obsługa kreatora dla innych języków](../../ide/wizard-support-for-other-languages.md).  
  
 Wybrany język jest widoczny w **zlokalizowane ciągi** opcji [ciągi szablonu dokumentu, Kreator aplikacji MFC](../../mfc/reference/document-template-strings-mfc-application-wizard.md) stronie kreatora.  
  
 **Korzystaj z bibliotek Unicode**  
 Określa, czy jest używana z Unicode lub z systemem innym niż Unicode wersji biblioteki MFC.  
  
 **Styl projektu**  
 Wskazuje, czy aplikacja ma standardowego MFC, Eksploratora plików, Visual Studio lub Architektura pakietu Office i wyświetlania. Aby uzyskać więcej informacji, zobacz [tworzenie aplikacji MFC w stylu Eksploratora plików](../../mfc/reference/creating-a-file-explorer-style-mfc-application.md).  
  
|Opcja|Opis|  
|------------|-----------------|  
|**MFC standard**|Zapewnia to standardowa Architektura aplikacji MFC.|  
|**Eksploratora plików**|Implementuje pliku Explorer przypominającej aplikacji przy użyciu okna podziału, gdzie jest okienka po lewej stronie [CTreeView — klasa](../../mfc/reference/ctreeview-class.md) i w okienku po prawej stronie jest [clistview — klasa](../../mfc/reference/clistview-class.md).|  
|**Visual Studio**|Implementuje Visual Studio przypominającej aplikacji, zawierający cztery okienka dokującego (**widoku pliku**, **widoku klasy**, **właściwości**, i **dane wyjściowe**) pochodny od [klasy CDockablePane](../../mfc/reference/cdockablepane-class.md) i główne okno ramowe pochodzącej z [klasy CMDIFrameWndEx](../../mfc/reference/cmdiframewndex-class.md) (ustawienie domyślne).|  
|**Office**|Implementuje aplikacji pakietu Office przypominającej zawierającej wstążki, która jest pochodną [klasy CMFCRibbonBar](../../mfc/reference/cmfcribbonbar-class.md), pasek programu Outlook, który jest pochodną [CMFCOutlookBar klasy](../../mfc/reference/cmfcoutlookbar-class.md), pasek tytułu, która jest pochodną [Klasy CMFCCaptionBar](../../mfc/reference/cmfccaptionbar-class.md)i ramce głównej, która jest pochodną [CMDIFrameWndEx klasy](../../mfc/reference/cmdiframewndex-class.md).|  
  
 **Styl wizualny i kolory**  
 Określa styl wizualny aplikacji. Dostępne są następujące opcje:  
  
-   **Windows Native lub domyślnego**  
  
-   **Office 2003**  
  
-   **Visual Studio 2005**  
  
-   **Office 2007 (motyw niebieski)**  
  
-   **Office 2007 (motyw czarny)**  
  
-   **Office 2007 (motyw srebrny)**  
  
-   **Office 2007 (motyw Akwamaryna)**  
  
 **Włącz przełączanie stylu wizualnego.**  
 Określa, czy użytkownik może zmienić stylu wizualnego aplikacji w czasie wykonywania, zwykle, wybierając odpowiedni styl wizualny z menu lub wstążki.  
  
 **Korzystanie z MFC**  
 Określa sposób utworzyć link do biblioteki MFC. Domyślnie MFC jest połączony jako Wspólnej bibliotece DLL.  
  
|Opcja|Opis|  
|------------|-----------------|  
|**Użyj MFC w współdzielonej bibliotece DLL**|Łącza do aplikacji jako Wspólnej bibliotece DLL biblioteki MFC. Aplikacja wykonywania wywołań do biblioteki MFC w czasie wykonywania. Tej opcji zmniejsza wymagania dotyczące dysków i pamięci aplikacji, które składają się z wielu plików wykonywalnych, korzystające z biblioteki MFC. Zarówno Win32 i MFC aplikacje mogą wywoływać funkcje w bibliotece DLL (ustawienie domyślne)|  
|**Użyj MFC w bibliotece statycznej**|Łącza aplikacji z biblioteką statyczną MFC w czasie kompilacji.|  
  
## <a name="see-also"></a>Zobacz też  
 [Kreator aplikacji MFC](../../mfc/reference/mfc-application-wizard.md)   
 [Typy plików utworzonych dla projektów Visual C++](../../ide/file-types-created-for-visual-cpp-projects.md)

