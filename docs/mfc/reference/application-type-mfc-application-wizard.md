---
title: Typ aplikacji, Kreator aplikacji MFC | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.appwiz.mfc.exe.apptype
dev_langs:
- C++
helpviewer_keywords:
- static libraries, MFC
ms.assetid: c3f62b0e-3f13-42c5-9859-d3890d0c3e1d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f302c797dd1074bcd96385c7ec1552589853f127
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45720697"
---
# <a name="application-type-mfc-application-wizard"></a>Typ aplikacji, kreator aplikacji MFC
Ta strona [Kreator aplikacji MFC](../../mfc/reference/mfc-application-wizard.md) do projektowania i dodawanie podstawowych funkcji do nowej aplikacji MFC.  
  
- **Typ aplikacji**

   Określa typ obsługi dokumentu, który ma zostać utworzona w aplikacji. Typ aplikacji, którą wybierzesz Określa opcje interfejsu użytkownika, które są dostępne dla aplikacji. Zobacz [funkcje interfejsu użytkownika, Kreator aplikacji MFC](../../mfc/reference/user-interface-features-mfc-application-wizard.md) Aby uzyskać więcej informacji.  
  
   Aby uzyskać więcej informacji na temat typów dokumentów, zobacz:  
  
   - [SDI i MDI](../../mfc/sdi-and-mdi.md)  
  
   - [Okna ramowe](../../mfc/frame-windows.md)  
  
   - [Klasy okien ramowych](../../mfc/frame-window-classes.md)  
  
   - [Dokumenty, widoki i struktura](../../mfc/documents-views-and-the-framework.md)  
  
   - [Okna dialogowe](../../mfc/dialog-boxes.md)  
  
   |Opcja|Opis|  
   |------------|-----------------|  
   |**Pojedynczy dokument**|Tworzy architektury interfejsu (SDI) pojedynczego dokumentu w aplikacji, w którym klasa widoku opiera się na [CView Class](../../mfc/reference/cview-class.md). Możesz zmienić klasę bazową dla widoku w [klasy generowane, Kreator aplikacji MFC](../../mfc/reference/generated-classes-mfc-application-wizard.md) strony kreatora. Do utworzenia aplikacji opartej na formularzu, na przykład użyć [klasa CFormView](../../mfc/reference/cformview-class.md) dla klasy widoku.<br /><br /> W tym typie aplikacji okna ramki dokumentu może zawierać tylko jeden dokument.|  
   |**Wiele dokumentów**|Tworzy wiele architektury interfejsu (MDI) dokumentu dla aplikacji, w którym klasa widoku opiera się na `CView`. Możesz zmienić klasę bazową dla widoku w **wygenerowane klasy** strony kreatora. Do utworzenia aplikacji opartej na formularzu, na przykład użyć `CFormView` dla klasy widoku.<br /><br /> W tym typie aplikacji okna ramki dokumentu może zawierać wiele podrzędnych systemu windows.|  
   |**Dokumenty z kartami**|Przełącza każdy dokument na osobnej karcie.|  
   |**Oparte o okna dialogowe**|Tworzy architektura oparta na oknach dialogowych dla swojej aplikacji, w którym na podstawie klasy okien dialogowych `CDialog`. (Aby utworzyć okno dialogowe HTML, zaznacz pole **okna dialogowego HTML użyj**.)|  
   |**Użyj okna dialogowego HTML**|Okno dialogowe pola tylko dla aplikacji. Pochodzi z klasy okien dialogowych z [klasa CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md) zamiast [klasa CDialog](../../mfc/reference/cdialog-class.md). Jeśli zaznaczysz to pole `CDHtmlDialog` znajduje się w **klasy bazowej** pole w [klasy generowane, Kreator aplikacji MFC](../../mfc/reference/generated-classes-mfc-application-wizard.md) strony kreatora.<br /><br /> A `CDHtmlDialog`-pochodnych okno dialogowe wyświetla okna dialogowe oparty na języku HTML, wymiana danych z kodem HTML kontroluje i obsługuje zdarzenia w formacie HTML.|  
   |**Wiele dokumentów najwyższego poziomu**|Tworzy wiele architektura najwyższego poziomu dla aplikacji, w którym klasa widoku opiera się na `CView`.<br /><br /> W tego rodzaju aplikacji, gdy użytkownik kliknie **New** (lub **nowej ramki**) na **pliku** menu, aplikacja tworzy okno, w których nadrzędna jest niejawnie pulpitu. Nowa ramka dokumentu pojawi się na pasku zadań i nie jest ograniczony do obszaru klienckiego okna aplikacji.|  
  
- **Obsługa architektury dokument/widok**

   Określa, czy dołączać architektury dokument/widok w aplikacji przy użyciu [klasa CDocument](../../mfc/reference/cdocument-class.md) i [CView Class](../../mfc/reference/cview-class.md) (ustawienie domyślne). Wyczyść to pole wyboru, jeśli są przenoszenie aplikacji innego typu niż MFC, lub jeśli chcesz zmniejszyć rozmiar skompilowanej plik wykonywalny. Domyślnie aplikacja bez architektury dokument/widok jest tworzony na podstawie [klasa CWinApp](../../mfc/reference/cwinapp-class.md), i nie obejmuje obsługę MFC otwarcie dokumentu z pliku na dysku.  
  
- **Język zasobów**

   Określa język zasobów. Zostanie wyświetlona lista dostępnych języków w systemie, jak zainstalować program Visual Studio. Jeśli chcesz zaznaczeniu innego języka niż język folderu odpowiedni szablon dla tego języka muszą być zainstalowane. Aby uzyskać więcej informacji o instalowaniu zasobów językowych różni się od wartości domyślne dostępne w **język zasobów** listę, zobacz [Obsługa kreatora dla innych języków](../../ide/wizard-support-for-other-languages.md).  
  
   Język, który wybierzesz znajduje odzwierciedlenie w **zlokalizowane ciągi** opcji [ciągi szablonu dokumentu, Kreator aplikacji MFC](../../mfc/reference/document-template-strings-mfc-application-wizard.md) strony kreatora.  
  
- **Używanie bibliotek Unicode**

   Określa, czy jest używana wersja Unicode lub innego niż Unicode biblioteki MFC.  
  
- **Styl projektu**

   Wskazuje, czy aplikacja ma standardowy MFC, Eksploratora plików, programu Visual Studio lub Architektura pakietu Office i wyświetlania. Aby uzyskać więcej informacji, zobacz [tworzenie aplikacji MFC w stylu Eksploratora plików](../../mfc/reference/creating-a-file-explorer-style-mfc-application.md).  
  
   |Opcja|Opis|  
   |------------|-----------------|  
   |**Standardowa MFC**|Zawiera standardowe architekturą aplikacji MFC.|  
   |**Eksplorator plików**|Implementuje pliku podobny Eksploratora aplikacji za pomocą okna rozdzielacza, gdzie jest okienka po lewej stronie [klasa CTreeView](../../mfc/reference/ctreeview-class.md) i w okienku po prawej stronie jest [klasa CListView](../../mfc/reference/clistview-class.md).|  
   |**Visual Studio**|Implementuje Visual aplikacji przypominającej Studio, która zawiera cztery okienek dokowalnych (**widok pliku**, **Widok klas**, **właściwości**, i **dane wyjściowe**) które są uzyskiwane z [klasa CDockablePane](../../mfc/reference/cdockablepane-class.md) i ramką głównego okna, która jest pochodną [klasa CMDIFrameWndEx](../../mfc/reference/cmdiframewndex-class.md) (ustawienie domyślne).|  
   |**Office**|Implementuje aplikacji podobne do pakietu Office, która zawiera wstążki, która jest pochodną [klasa CMFCRibbonBar](../../mfc/reference/cmfcribbonbar-class.md), pasek programu Outlook, która jest pochodną [klasa CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md), pasek podpisu, która jest pochodną [Klasa CMFCCaptionBar](../../mfc/reference/cmfccaptionbar-class.md)i głównej ramki, który jest tworzony na podstawie [klasa CMDIFrameWndEx](../../mfc/reference/cmdiframewndex-class.md).|  
  
- **Styl wizualny i kolory**

   Określa styl wizualny aplikacji. Dostępne są następujące opcje:  
  
   - **Domyślny natywny Windows**  
  
   - **Office 2003**  
  
   - **Visual Studio 2005**  
  
   - **Office 2007 (motyw niebieski)**  
  
   - **Office 2007 (motyw czarny)**  
  
   - **Office 2007 (motyw srebrny)**  
  
   - **Office 2007 (Akwamaryna motywu)**  
  
- **Włącz przełączanie stylu wizualnego**

   Określa, czy użytkownik może zmienić stylu wizualnego w aplikacji w czasie wykonywania, zwykle, wybierając odpowiedni styl wizualny z Wstążki lub menu.  
  
- **Użycie MFC**

   Określa sposób utworzyć łącze do biblioteki MFC. Domyślnie MFC zostanie połączona jako współdzieloną DLL.  
  
   |Opcja|Opis|  
   |------------|-----------------|  
   |**Użyj MFC w współdzielonej bibliotece DLL**|Łączy aplikację jako współdzieloną DLL biblioteki MFC. Aplikacja wykonuje wywołania do biblioteki MFC w czasie wykonywania. Tej opcji zmniejsza wymagania dotyczące dysku i pamięci aplikacji, które składają się z wielu plików wykonywalnych, korzystające z biblioteki MFC. Aplikacje Win32 i MFC można wywołać funkcji w bibliotece DLL (ustawienie domyślne)|  
   |**Użyj MFC w bibliotece statycznej**|Łączy aplikację z biblioteką statyczną MFC w czasie kompilacji.|  
  
## <a name="see-also"></a>Zobacz też  
 [Kreator aplikacji MFC](../../mfc/reference/mfc-application-wizard.md)   
 [Typy plików utworzonych dla projektów Visual C++](../../ide/file-types-created-for-visual-cpp-projects.md)

