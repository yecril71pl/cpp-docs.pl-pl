---
title: Kreator dodawania klasy MFC
ms.date: 09/06/2019
f1_keywords:
- vc.codewiz.class.mfc.simple.overview
helpviewer_keywords:
- MFC Add Class Wizard
- wizards [MFC]
ms.assetid: ad3b0989-d307-43b2-9417-3f9a78889024
ms.openlocfilehash: 2c82e084de2123c579299ca6490bdfcfdac5d255
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2019
ms.locfileid: "70908033"
---
# <a name="mfc-add-class-wizard"></a>Kreator dodawania klasy MFC

Ten Kreator kodu służy do dodawania klasy do istniejącego projektu MFC lub do dodawania klasy do projektu ATL, który obsługuje MFC. Można również dodawać klasy MFC do projektów Win32 z obsługą MFC. Funkcje określone podczas tworzenia projektu określają opcje dostępne w tym oknie dialogowym. Aby uzyskać dostęp do kreatora, kliknij pozycję **Dodaj klasę** w [Kreatorze klas](mfc-class-wizard.md).

![Kreator dodawania klasy MFC](media/add-mfc-class-wizard.png "Kreator dodawania klasy MFC")

## <a name="names"></a>Nazwy

Na tej stronie Określ nazwę klasy, klasę bazową i nazwy plików dla nowej klasy.

- **Nazwa klasy**

  Określa nazwę nowej klasy i zapewnia domyślną podstawę nazw identyfikatorów i plików na tej stronie. C++klasy zwykle zaczynają się od "C", więc na przykład "CMyClass" przyjmuje wartość "MyClass. h" i tak dalej.

- **Klasa bazowa**

  Określa nazwę klasy bazowej dla nowej klasy. Domyślnie Klasa bazowa to [CWnd](../../mfc/reference/cwnd-class.md). Wybrana Klasa bazowa określa, czy inne pola na tej stronie są aktywne.

  Typ klasy ustawianej jako klasa bazowa określa, czy Klasa ma identyfikator okna dialogowego czy identyfikator zasobu. Ogólne typy klas są następujące:

  - Klasy takie jak [CButton](../../mfc/reference/cbutton-class.md), [CWnd](../../mfc/reference/cwnd-class.md)lub [CDOCUMENT](../../mfc/reference/cdocument-class.md), które nie wymagają identyfikatora okna dialogowego ani identyfikatora zasobu. Te klasy nie używają okna dialogowego ani identyfikatora zasobu. W przypadku wybrania jednej z tych klas dla klasy podstawowej pole **identyfikatora okna dialogowego** i **Identyfikator zasobu DHTML** są wygaszone.

  - Klasy takie jak [CDialog](../../mfc/reference/cdialog-class.md), [CFormView](../../mfc/reference/cformview-class.md)lub [CPropertyPage](../../mfc/reference/cpropertypage-class.md), które wymagają identyfikatora okna dialogowego.

  - Klasa [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md), która wymaga identyfikatora okna dialogowego, identyfikatora zasobu DHTML i nazwy pliku HTML.

  W przypadku klas wymagających identyfikatora okna dialogowego może okazać się bardziej wydajne użycie [edytora zasobów](../../windows/resource-editors.md) do utworzenia zasobu okna dialogowego, przypisanie jego identyfikatora w [Kreatorze klasy](mfc-class-wizard.md), a następnie utworzenie klasy SKOJARZONEj z tym identyfikatorem zasobu. Aby uzyskać więcej informacji na temat tworzenia standardowego okna dialogowego systemu Windows, zobacz [Tworzenie nowego okna dialogowego](../../windows/creating-a-new-dialog-box.md) .

  > [!NOTE]
  > Jeśli najpierw utworzysz zasób okna dialogowego i poprowadzisz jego nową klasę `CDHtmlDialog`z, Usuń standardowe przyciski systemu Windows **OK** i **Anuluj** , które są wyświetlane w domyślnym oknie dialogowym. Standardowe okno dialogowe systemu Windows obsługuje formularz DHTML, który zawiera własne przyciski **OK** i **Anuluj** .

  Chociaż okno dialogowe może zawierać formanty systemu Windows i kontrolki DHTML, nie jest to zalecane.

- **Identyfikator okna dialogowego**

  Określa identyfikator okna dialogowego, w `CDialog`przypadku wybrania, `CFormView`, `CPropertyPage`lub `CDHtmlDialog` jako **klasy bazowej**.

- **plik h**

  Ustawia nazwę pliku nagłówka dla klasy nowego obiektu. Domyślnie ta nazwa jest oparta na nazwie podanym w polu **Nazwa klasy**. Kliknij przycisk wielokropka, aby zapisać nazwę pliku w wybranej lokalizacji, lub dołączyć deklarację klasy do istniejącego pliku. Jeśli wybierzesz istniejący plik, Kreator nie zapisze go w wybranej lokalizacji, dopóki nie klikniesz przycisku **Zakończ** w kreatorze.

  Kreator nie zastępuje pliku. Jeśli wybierzesz nazwę istniejącego pliku, po kliknięciu przycisku **Zakończ**Kreator monituje o wskazanie, czy deklaracja klasy powinna zostać dołączona do zawartości pliku. Kliknij przycisk **tak** , aby dołączyć plik; Kliknij przycisk **nie** , aby powrócić do kreatora i określić inną nazwę pliku.

- **plik. cpp**

  Ustawia nazwę pliku implementacji dla klasy nowego obiektu. Domyślnie ta nazwa jest oparta na nazwie podanym w polu **Nazwa klasy**. Kliknij przycisk wielokropka, aby zapisać nazwę pliku w wybranej lokalizacji. Plik nie jest zapisywany w wybranej lokalizacji, dopóki nie zostanie kliknięty przycisk **Zakończ** w kreatorze.

  Kreator nie zastępuje pliku. W przypadku wybrania nazwy istniejącego pliku po kliknięciu przycisku **Zakończ**Kreator monituje o wskazanie, czy implementacja klasy powinna zostać dołączona do zawartości pliku. Kliknij przycisk **tak** , aby dołączyć plik; Kliknij przycisk **nie** , aby powrócić do kreatora i określić inną nazwę pliku.

- **Aktywne ułatwienia dostępu**

  Włącza obsługę funkcji Active Accessibility przez MFC, wywołując [EnableActiveAccessibility](../../mfc/reference/cwnd-class.md#enableactiveaccessibility) w konstruktorze. Ta opcja jest dostępna dla klas pochodnych [CWnd](../../mfc/reference/cwnd-class.md).

- **Automatyzacja**

  Ustawia poziom obsługi [automatyzacji](../../mfc/automation.md). Automatyzacja na poziomie klasy jest dostępna dla wszystkich klas, które obsługują automatyzację. Jest ona również dostępna dla projektów utworzonych z obsługą automatyzacji. Oznacza to, że jest to projekt MFC [obsługujący ATL](../../atl/reference/mfc-support-in-atl-projects.md)lub projekt MFC, dla którego zaznaczono pole wyboru **Automatyzacja** na stronie [funkcje zaawansowane](../../mfc/reference/advanced-features-mfc-application-wizard.md) Kreatora aplikacji MFC.

   Obsługa automatyzacji nie jest dostępna dla następujących klas bazowych:

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

## <a name="see-also"></a>Zobacz także

[Klasa MFC](../../mfc/reference/adding-an-mfc-class.md)<br/>
[Dodawanie klasy](../../ide/adding-a-class-visual-cpp.md)
