---
title: Kreator dodawania klasy MFC | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.codewiz.class.mfc.simple.overview
dev_langs:
- C++
helpviewer_keywords:
- MFC Add Class Wizard
- wizards [MFC]
ms.assetid: ad3b0989-d307-43b2-9417-3f9a78889024
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b4c65785008c7257fc2f3714d9bf78395f4a8e40
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="mfc-add-class-wizard"></a>Kreator dodawania klasy MFC
Użyj tego kreatora kod, aby dodać klasę do istniejącego projektu MFC lub aby dodać klasę Projekt ATL, który obsługuje MFC. Klasy MFC mogą również dodać do projektów Win32, których obsługa MFC. Funkcje, które określono podczas tworzenia projektu określają opcje dostępne w tym oknie dialogowym.  
  
## <a name="names"></a>Nazwy  
 Na tej stronie Określ nazwę klasy, klasy podstawowej i nazwy pliku dla nowej klasy.  
  
 **Nazwa klasy**  
 Określa nazwę nowej klasy i stanowi podstawę domyślne dla nazwy identyfikatorów i plików na tej stronie. Klasy C++ zaczynają się zwykle "C", aby na przykład "CMyClass" staje się "MyClass.h", i tak dalej.  
  
 **Klasa podstawowa**  
 Określa nazwę klasy podstawowej dla nowej klasy. Domyślnie klasa podstawowa jest [CWnd](../../mfc/reference/cwnd-class.md). Klasa podstawowa, którą wybierzesz Określa, czy innych pól na tej stronie są aktywne.  
  
 Typ klasy, którą można ustawić jako klasę podstawową Określa, czy klasa ma identyfikator okna dialogowego lub identyfikator zasobu. Typy ogólne klas są następujące:  
  
-   Klas takich jak [CButton](../../mfc/reference/cbutton-class.md), [CWnd](../../mfc/reference/cwnd-class.md), lub [CDocument](../../mfc/reference/cdocument-class.md), które nie wymagają okno dialogowe Identyfikatora lub identyfikator zasobu. Te klasy nie należy używać okna dialogowego lub zasobu identyfikatora. Po wybraniu jednej z tych klas dla klasy podstawowej, **identyfikator okna dialogowego** pole i **identyfikator zasobu DHTML** pola są niedostępne.  
  
-   Klas takich jak [cdialog —](../../mfc/reference/cdialog-class.md), [CFormView](../../mfc/reference/cformview-class.md), lub [cpropertypage —](../../mfc/reference/cpropertypage-class.md), które wymagają identyfikatora dla okna dialogowego.  
  
-   Klasa [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md), co wymaga identyfikator okna dialogowego, identyfikator zasobu DHTML i nazwa pliku HTML.  
  
 Dla klas wymagające identyfikator okna dialogowego, może być bardziej wydajne, aby użyć [Edytor zasobów](../../windows/resource-editors.md) można utworzyć zasobu okna dialogowego, należy przypisać jej Identyfikatora w [okna właściwości](/visualstudio/ide/reference/properties-window), a następnie utworzyć klasę skojarzone z tym identyfikatorem zasobu. Zobacz [tworzenia nowego okna dialogowego](../../windows/creating-a-new-dialog-box.md) Aby uzyskać więcej informacji na temat tworzenia standardowe okno dialogowe systemu Windows.  
  
> [!NOTE]
>  Jeśli najpierw utwórz zasób okna dialogowego i uzyskania jej nowej klasy z `CDHtmlDialog`, Usuń standard Windows **OK** i **anulować** przycisków wyświetlanych w oknie dialogowym domyślne. Standardowe okno dialogowe systemu Windows obsługuje formularz DHTML, który zawiera własną **OK** i **anulować** przycisków.  
  
 Gdy Twoje okno dialogowe może zawierać zarówno formantów systemu Windows, jak i DHTML — formanty go nie jest zalecane.  
  
 **Identyfikator okna dialogowego**  
 Określa identyfikator okna dialogowego, w przypadku wybrania `CDialog`, `CFormView`, `CPropertyPage`, lub `CDHtmlDialog` jako **klasa podstawowa**.  
  
 **w pliku .h**  
 Ustawia nazwę pliku nagłówka dla klasy nowego obiektu. Domyślnie ta nazwa jest na podstawie nazwy podane **Nazwa klasy**. Kliknij przycisk wielokropka, aby zapisać nazwę pliku w wybranej lokalizacji lub do dołączenia do istniejącego pliku deklaracji klasy. Jeśli wybierzesz istniejący plik, Kreator nie zapisze go w wybranej lokalizacji dopóki kliknij **Zakończ** w kreatorze.  
  
 Kreator nie powoduje zastąpienia pliku. Jeśli po kliknięciu przycisku Wybierz nazwę istniejącego pliku, **Zakończ**, Kreator wyświetli monit, aby wskazać, czy deklaracja klasy powinna zostać dołączona do zawartości pliku. Kliknij przycisk **tak** pliku; kliknij przycisk **nr** aby powrócić do kreatora i podaj inną nazwę pliku.  
  
 **plik .cpp**  
 Ustawia nazwę pliku implementacji dla nowego obiektu klasy. Domyślnie ta nazwa jest na podstawie nazwy podane **Nazwa klasy**. Kliknij przycisk wielokropka, aby zapisać nazwę pliku w wybranej lokalizacji. Plik nie jest zapisywany w wybranej lokalizacji do momentu kliknięcia **Zakończ** w kreatorze.  
  
 Kreator nie powoduje zastąpienia pliku. Jeśli po kliknięciu przycisku Wybierz nazwę istniejącego pliku, **Zakończ**, Kreator wyświetli monit, aby wskazać, czy klasa implementacji powinna zostać dołączona do zawartości pliku. Kliknij przycisk **tak** pliku; kliknij przycisk **nr** aby powrócić do kreatora i podaj inną nazwę pliku.  
  
 **Active accessibility**  
 Umożliwia obsługę MFC Active Accessibility wywołując [EnableActiveAccessibility](../../mfc/reference/cwnd-class.md#enableactiveaccessibility) w konstruktorze. Ta opcja jest dostępna dla klasy wyprowadzone z [CWnd](../../mfc/reference/cwnd-class.md).  
  
 **Identyfikator zasobu DHTML**  
 Dotyczy klasy pochodzące od `CDHtmlDialog` tylko. Określa identyfikator zasobu okna dialogowego DHTML. Identyfikator zasobu pojawia się w sekcji HTML plik .rc projektu, oraz nazwa pliku okno dialogowe HTML. DHTML zasobu, określonego przez ten identyfikator jest hostowana przez okno dialogowe identyfikowane przez **identyfikator okna dialogowego**.  
  
 **. Plik HTML**  
 Dotyczy klasy pochodzące od `CDHtmlDialog` tylko. Ustawia nazwę pliku w formacie HTML w oknie dialogowym DHTML. Domyślnie ta nazwa pliku opiera się na nazwę klasy. Nazwa pliku pojawia się w sekcji HTML plik .rc projektu, wraz z identyfikatorem DHTML okna dialogowego pole zasobu.  
  
 **Automatyzacja**  
 Ustawia poziom klasy obsługi [automatyzacji](../../mfc/automation.md). Automatyzacja na poziomie klasy jest dostępna dla wszystkich klas, które obsługują automatyzacji. Jest również dostępne dla projektów utworzonych za pomocą obsługę automatyzacji. Oznacza to, albo MFC projektu, który [obsługuje ATL](../../atl/reference/mfc-support-in-atl-projects.md), lub dla której wybranego projektu MFC **automatyzacji** pole wyboru w [funkcje zaawansowane](../../mfc/reference/advanced-features-mfc-application-wizard.md) strony MFC Kreator aplikacji.  
  
|Opcja|Opis|  
|------------|-----------------|  
|**Brak**|Wskazuje, że klasa nie obsługuje automatyzacji.|  
|**Automatyzacja**|Wskazuje, że klasa obsługuje automatyzacji. Wybranie tej opcji nowo utworzonej klasy jest dostępna jako obiekt programowalny przez aplikacje klienckie automatyzacji, takich jak Microsoft Visual Basic i Microsoft Excel. Ta opcja nie jest dostępna dla klas podstawowych wymienione pod tą tabelą.|  
|**Możliwość utworzenia przez identyfikator typu**|Wskazuje, że zarówno klasy, jak i projektu obsługuje inne aplikacje, tworzenia obiektów tej klasy przy użyciu automatyzacji. Po wybraniu tej opcji klientów automatyzacji można bezpośrednio utworzyć obiekt automatyzacji. Identyfikator typu w polu tekstowym jest używany przez aplikację klienta, aby określić obiekt ma zostać utworzony; jest ogólnosystemowe i muszą być unikatowe. Ta opcja nie jest dostępna dla klas podstawowych wymienione pod tą tabelą.|  
  
 Obsługa automatyzacji nie jest dostępne dla następujących klas podstawowych:  
  
-   `CAsyncMonitorFile`  
  
-   `CAsyncSocket`  
  
-   `CCachedDataPathProperty`  
  
-   `CConnectionPoint`  
  
-   `CDatabase`  
  
-   `CDataPathProperty`  
  
-   `CHttpFilter`  
  
-   `CHttpServer`  
  
-   `CInternetSession`  
  
-   `CObject`  
  
-   `CSocket`  
  
 **Identyfikator typu**  
 Ustawia identyfikator typu klasy. **Identyfikator typu** pole łączy nazwę projektu i nową nazwę klasy w następujący sposób: *MFCProj.MFCClass*. Ten identyfikator jest włączone tylko wtedy, gdy wybrano **automatyzacji** opcji **Creatable przez identyfikator typu**.  
  
 **Generuj zasoby opcję**  
 Informuje, że dokumenty utworzone przez aplikację zasobów szablonu dokumentu. Aby aktywować tego pola wyboru, projekt musi obsługiwać architektury dokument/widok MFC i musi być klasą bazową dla tej klasy [CFormView](../../mfc/reference/cformview-class.md).  
  
 Zobacz [szablony dokumentów i proces tworzenia dokumentu/widoku](../../mfc/document-templates-and-the-document-view-creation-process.md) uzyskać więcej informacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy MFC](../../mfc/reference/adding-an-mfc-class.md)   
 [Dodawanie klasy](../../ide/adding-a-class-visual-cpp.md)
