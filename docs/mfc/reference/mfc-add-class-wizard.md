---
title: Kreator dodawania klasy MFC
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.mfc.simple.overview
helpviewer_keywords:
- MFC Add Class Wizard
- wizards [MFC]
ms.assetid: ad3b0989-d307-43b2-9417-3f9a78889024
ms.openlocfilehash: fa9b947ae6fc0e48aaecde61e35a5f4152c85f27
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57304096"
---
# <a name="mfc-add-class-wizard"></a>Kreator dodawania klasy MFC

Użyj tego kreatora kodu, aby dodać klasę do istniejącego projektu MFC lub aby dodać klasę do projektu ATL, który obsługuje MFC. Klasy MFC można również dodać do projekty Win32, które obsługują MFC. Funkcje, które określono podczas tworzenia projektu określają opcje dostępne w tym oknie dialogowym.

## <a name="names"></a>Nazwy

Na tej stronie Określ nazwę klasy, klasy bazowej i nazwy plików dla nowej klasy.

- **Nazwa klasy**

  Określa nazwę nowej klasy i stanowi podstawę domyślne dla nazwy identyfikatorów i pliki na tej stronie. Klasy C++ zaczynają się zwykle "C", dlatego na przykład "CMyClass" staje się "MyClass.h", i tak dalej.

- **Klasa bazowa**

  Określa nazwę klasy bazowej dla nowej klasy. Domyślnie klasa bazowa jest [CWnd](../../mfc/reference/cwnd-class.md). Klasa bazowa, którą wybierzesz Określa, czy inne pola na tej stronie są aktywne.

  Typ klasy, gdy ustawiasz jako klasa bazowa Określa, czy klasa ma identyfikator okna dialogowego lub identyfikator zasobu. Typy ogólne klasy są następujące:

  - Klasy, takie jak [CButton](../../mfc/reference/cbutton-class.md), [CWnd](../../mfc/reference/cwnd-class.md), lub [CDocument](../../mfc/reference/cdocument-class.md), które nie wymagają okna dialogowego identyfikator lub identyfikator zasobu. W ramach tych zajęć, nie należy używać okna dialogowego lub zasobów identyfikatora. Po wybraniu jednej z tych klas dla swojej klasy bazowej, **identyfikator okna dialogowego** pole i **identyfikator zasobu DHTML** pola są wygaszone.

  - Klasy, takie jak [CDialog](../../mfc/reference/cdialog-class.md), [CFormView](../../mfc/reference/cformview-class.md), lub [CPropertyPage](../../mfc/reference/cpropertypage-class.md), które wymagają identyfikatora dla okna dialogowego.

  - Klasa [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md), co wymaga identyfikator okna dialogowego, identyfikator zasobu DHTML i nazwy pliku HTML.

  Dla klas wymagające identyfikator okna dialogowego, może okazać się bardziej wydajne, aby użyć [Edytor zasobów](../../windows/resource-editors.md) do utworzenia zasobu okna dialogowego, należy przypisać jej identyfikator w [okno właściwości](/visualstudio/ide/reference/properties-window), a następnie Utwórz klasę skojarzone z tego identyfikatora zasobu. Zobacz [Tworzenie nowego okna dialogowego](../../windows/creating-a-new-dialog-box.md) Aby uzyskać więcej informacji na temat tworzenia standardowe okno dialogowe Windows.

  > [!NOTE]
  > Jeśli tworzenie zasobu okna dialogowego pierwszy i uzyskania jej nowej klasy, z `CDHtmlDialog`, Usuń standardowa Windows **OK** i **anulować** przycisków, które są wyświetlane w oknie dialogowym domyślne. Standardowe okno dialogowe Windows obsługuje formularz DHTML, który zawiera swój własny **OK** i **anulować** przycisków.

  Gdy dialogowym mogą zawierać zarówno Windows kontrolki oraz DHTML, nie jest zalecane.

- **Identyfikator okna dialogowego**

  Określa identyfikator okna dialogowego, w przypadku wybrania `CDialog`, `CFormView`, `CPropertyPage`, lub `CDHtmlDialog` jako **klasy bazowej**.

- **plik .h**

  Określa nazwę pliku nagłówkowego klasy nowego obiektu. Domyślnie ta nazwa jest na podstawie nazwy podane **Nazwa klasy**. Kliknij przycisk wielokropka, aby zapisać nazwę pliku na lokalizację lub dołączyć deklaracji klasy do istniejącego pliku. Jeśli wybierzesz istniejący plik, Kreator nie zapisze go w wybranej lokalizacji do momentu kliknij **Zakończ** w kreatorze.

  Kreator nie powoduje zastąpienia pliku. Jeśli wybierasz nazwę istniejącego pliku, po kliknięciu **Zakończ**, Kreator wyświetli monit o wskazują, czy deklaracja klasy powinna zostać dołączona do zawartości pliku. Kliknij przycisk **tak** można dołączyć pliku kliknij przycisk **nie** aby powrócić do kreatora i podaj inną nazwę pliku.

- **Plik CPP**

  Określa nazwę pliku implementacji dla nowego obiektu klasy. Domyślnie ta nazwa jest na podstawie nazwy podane **Nazwa klasy**. Kliknij przycisk wielokropka, aby zapisać nazwę pliku w wybranej lokalizacji. Plik nie jest zapisywany w wybranej lokalizacji, dopóki nie klikniesz **Zakończ** w kreatorze.

  Kreator nie powoduje zastąpienia pliku. Jeśli wybierasz nazwę istniejącego pliku, po kliknięciu **Zakończ**, Kreator wyświetli monit o wskazują, czy Implementacja klasy powinna zostać dołączona do zawartości pliku. Kliknij przycisk **tak** można dołączyć pliku kliknij przycisk **nie** aby powrócić do kreatora i podaj inną nazwę pliku.

- **Moduł Active accessibility**

  Włączenie obsługi MFC Active Accessibility przez wywołanie metody [EnableActiveAccessibility](../../mfc/reference/cwnd-class.md#enableactiveaccessibility) w konstruktorze. Ta opcja jest dostępna dla klasy pochodne [CWnd](../../mfc/reference/cwnd-class.md).

- **Identyfikator zasobu DHTML**

  Dotyczy klasy pochodne `CDHtmlDialog` tylko. Określa identyfikator zasobu okna dialogowego DHTML. Identyfikator zasobu pojawia się w sekcji HTML w pliku .rc w projekcie, wraz z nazwą pliku okno dialogowe HTML. Zasobu DHTML, określonego przez ten identyfikator jest hostowana przez okno dialogowe identyfikowane przez **identyfikator okna dialogowego**.

- **.HTM file**

  Dotyczy klasy pochodne `CDHtmlDialog` tylko. Określa nazwę pliku HTML dla DHTML, okno dialogowe. Domyślnie ta nazwa pliku opiera się na nazwę klasy. Nazwa pliku pojawia się w sekcji HTML projektu pliku .rc, wraz z identyfikatorem DHTML okna dialogowego pole zasobów.

- **Automatyzacja**

  Ustawia poziom klasy obsługi [automatyzacji](../../mfc/automation.md). Usługa Automation na poziomie klasy jest dostępna dla wszystkich klas, które obsługują automatyzacji. Jest również dostępna w przypadku projektów utworzonych za pomocą obsługę automatyzacji. Oznacza to, albo MFC projekt, który [obsługuje ATL](../../atl/reference/mfc-support-in-atl-projects.md), lub projekcie MFC, dla którego wybrano **automatyzacji** pole wyboru w [funkcje zaawansowane](../../mfc/reference/advanced-features-mfc-application-wizard.md) strony MFC Kreator aplikacji.

  |Opcja|Opis|
  |------------|-----------------|
  |**Brak**|Wskazuje, że klasa ma nie obsługuje automatyzacji.|
  |**Automatyzacja**|Wskazuje, że klasa obsługuje automatyzację. Jeśli wybierzesz tę opcję, nowo utworzone klasy jest dostępna jako obiekt programowalny przez aplikacje klienckie usługi Automation, takich jak Microsoft Visual Basic oraz programu Microsoft Excel. Ta opcja nie jest dostępna dla klas podstawowych wyświetlonego po tej tabeli.|
  |**Mogą stworzyć typu identyfikator**|Wskazuje, że klasy oraz projektu obsługiwać inne aplikacje, w tworzenie obiektów tej klasy przy użyciu automatyzacji. Po wybraniu tej opcji klienci automatyzacji można bezpośrednio utworzyć obiekt automatyzacji. Identyfikator typu, w polu tekstowym jest używany przez aplikację klienta, można określić obiekt, który ma zostać utworzony; jest ogólnosystemowe i muszą być unikatowe. Ta opcja nie jest dostępna dla klas podstawowych wyświetlonego po tej tabeli.|

  Obsługa automatyzacji nie jest dostępna dla następujących klas podstawowych:

  - `CAsyncMonitorFile`

  - `CAsyncSocket`

  - `CCachedDataPathProperty`

  - `CConnectionPoint`

  - `CDatabase`

  - `CDataPathProperty`

  - `CHttpFilter`

  - `CHttpServer`

  - `CInternetSession`

  - `CObject`

  - `CSocket`

- **Identyfikator typu**

  Ustawia identyfikator typu klasy. **Identyfikator typu** pole łączy nazwę projektu i nową nazwę klasy w następujący sposób: *MFCProj.MFCClass*. Ten identyfikator jest zmieniane tylko wtedy, gdy wybrano **automatyzacji** opcji **Creatable według Identyfikatora typu**.

- **Generuj tym zasoby**

  Oznacza, że dokumenty utworzonych przez aplikację ma zasoby szablonu dokumentu. Aby uaktywnić to pole wyboru, projekt musi obsługiwać architektury dokument/widok MFC, a klasa bazowa tej klasy muszą być [CFormView](../../mfc/reference/cformview-class.md).

  Zobacz [szablonów dokumentów i proces tworzenia dokumentu/widoku](../../mfc/document-templates-and-the-document-view-creation-process.md) Aby uzyskać więcej informacji.

## <a name="see-also"></a>Zobacz także

[MFC Class](../../mfc/reference/adding-an-mfc-class.md)<br/>
[Dodawanie klasy](../../ide/adding-a-class-visual-cpp.md)
