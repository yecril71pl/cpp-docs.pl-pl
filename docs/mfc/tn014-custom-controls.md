---
title: 'TN014: Formanty niestandardowe | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 06/28/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.controls
dev_langs:
- C++
helpviewer_keywords:
- TN014
- custom controls [MFC]
ms.assetid: 1917a498-f643-457c-b570-9a0af7dbf7bb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bacba9ea15598e4c722682a081b64b80db34e00b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46430569"
---
# <a name="tn014-custom-controls"></a>TN014: formanty niestandardowe

Ta uwaga opisuje Obsługa MFC dla formantów niestandardowych i własnym rysowania. Ponadto w tym artykule opisano podklasy dynamiczne i opisuje relację między [CWnd](../mfc/reference/cwnd-class.md) obiektów i `HWND`s.

Przykładowa aplikacja MFC CTRLTEST ilustruje sposób użycia wielu formantów niestandardowych. Zobacz kod źródłowy dla próbki MFC-ogólne [CTRLTEST](../visual-cpp-samples.md) i pomocy online.

## <a name="owner-draw-controlsmenus"></a>Formanty rysowane przez właściciela/menu

Windows obsługuje formanty rysowane przez właściciela i menu za pomocą komunikatów Windows. Okno nadrzędne kontrolki lub menu odbiera tych komunikatów i wywołania funkcji w odpowiedzi. Możesz przesłonić te funkcje, aby dostosować wygląd i zachowanie kontrolka rysowana przez właściciela lub menu.

Biblioteka MFC obsługuje bezpośrednio przez właściciela z następujących funkcji:

- [CWnd::OnDrawItem](../mfc/reference/cwnd-class.md#ondrawitem)

- [CWnd::OnMeasureItem](../mfc/reference/cwnd-class.md#onmeasureitem)

- [CWnd::OnCompareItem](../mfc/reference/cwnd-class.md#oncompareitem)

- [CWnd::OnDeleteItem](../mfc/reference/cwnd-class.md#ondeleteitem)

Możesz zastąpić te funkcje w swojej `CWnd` klasy do zaimplementowania niestandardowego rysowania zachowanie.

To podejście nie prowadzi do kodu wielokrotnego użytku. W przypadku dwóch podobnych kontrolek w dwóch różnych `CWnd` klasy, należy zaimplementować to zachowanie kontrolki niestandardowej w dwóch lokalizacjach. Architektura obsługiwana przez MFC własnym rysowania formantu rozwiązuje ten problem.

## <a name="self-draw-controls-and-menus"></a>Menu i własnym rysowania formantów

MFC udostępnia domyślną implementację (w `CWnd` i [CMenu](../mfc/reference/cmenu-class.md) klasy) dla wiadomości standardowa rysowania przez właściciela. Ta domyślna implementacja będzie dekodowania parametry rysowania przez właściciela i delegowanie wiadomości rysowania przez właściciela do kontrolki lub menu. Jest to nazywane własnym Rysowanie ponieważ kod rysowania klasy formantu lub menu, a nie w oknie właściciela.

Przy użyciu własnym rysowania formantów możesz tworzyć klasy kontrolek wielokrotnego użytku, które korzystają bezpośrednio z semantyki rysowania przez właściciela, aby wyświetlić formant. Kod rysowania kontrolki znajduje się w klasie kontrolki nie jego obiektu nadrzędnego. Jest to zorientowane obiektowo podejście do programowania kontrolki niestandardowej. Dodaj poniższą listę funkcji do swoich klas własnym rysowania:

- Rysowanie własnym przycisków:

    ```cpp
    CButton:DrawItem(LPDRAWITEMSTRUCT);
    // insert code to draw this button
    ```

- Rysowanie własnym menu:

    ```cpp
    CMenu:MeasureItem(LPMEASUREITEMSTRUCT);
    // insert code to measure the size of an item in this menu
    CMenu:DrawItem(LPDRAWITEMSTRUCT);
    // insert code to draw an item in this menu
    ```

- Dla pól listy własnym rysowania:

    ```cpp
    CListBox:MeasureItem(LPMEASUREITEMSTRUCT);
    // insert code to measure the size of an item in this list box
    CListBox:DrawItem(LPDRAWITEMSTRUCT);
    // insert code to draw an item in this list box

    CListBox:CompareItem(LPCOMPAREITEMSTRUCT);
    // insert code to compare two items in this list box if LBS_SORT
    CListBox:DeleteItem(LPDELETEITEMSTRUCT);
    // insert code to delete an item from this list box
    ```

- Dla pola kombi własnym rysowania:

    ```cpp
    CComboBox:MeasureItem(LPMEASUREITEMSTRUCT);
    // insert code to measure the size of an item in this combo box
    CComboBox:DrawItem(LPDRAWITEMSTRUCT);
    // insert code to draw an item in this combo box

    CComboBox:CompareItem(LPCOMPAREITEMSTRUCT);
    // insert code to compare two items in this combo box if CBS_SORT
    CComboBox:DeleteItem(LPDELETEITEMSTRUCT);
    // insert code to delete an item from this combo box
    ```

Aby uzyskać szczegółowe informacje na temat struktury rysowania przez właściciela ([DRAWITEMSTRUCT](../mfc/reference/drawitemstruct-structure.md), [MEASUREITEMSTRUCT](../mfc/reference/measureitemstruct-structure.md), [COMPAREITEMSTRUCT](../mfc/reference/compareitemstruct-structure.md), i [DELETEITEMSTRUCT](../mfc/reference/deleteitemstruct-structure.md)) można znaleźć w dokumentacji MFC `CWnd::OnDrawItem`, `CWnd::OnMeasureItem`, `CWnd::OnCompareItem`, i `CWnd::OnDeleteItem` odpowiednio.

## <a name="using-self-draw-controls-and-menus"></a>Przy użyciu własnym rysowania formantów i menu

Rysowanie własnym menu, konieczne jest przesłonięcie zarówno `OnMeasureItem` i `OnDrawItem` metody.

Dla pola własnym Rysowanie listy i pola kombi, konieczne jest przesłonięcie `OnMeasureItem` i `OnDrawItem`. W szablonie okna dialogowego należy określić stylu LBS_OWNERDRAWVARIABLE dla pól listy lub CBS_OWNERDRAWVARIABLE dla pola kombi. Styl OWNERDRAWFIXED nie będzie działać z własnym narysować elementy, ponieważ wysokość elementu stałej jest określana przed własnym rysowania formantów są dołączone do pola listy. (Można użyć metod [CListBox::SetItemHeight](../mfc/reference/clistbox-class.md#setitemheight) i [CComboBox::SetItemHeight](../mfc/reference/ccombobox-class.md#setitemheight) to ograniczenie.)

Przełączanie stylu OWNERDRAWVARIABLE wymusi systemu, aby zastosować styl NOINTEGRALHEIGHT do formantu. Ponieważ formant nie może obliczyć całkowity wysokość przy użyciu zmiennej wielkości elementów, domyślny styl INTEGRALHEIGHT jest ignorowany i kontrolki zawsze NOINTEGRALHEIGHT. Jeśli elementów są stałe wysokość, uniemożliwi częściowe elementów z możliwością rysowania, określając rozmiar formantu, który ma być mnożnik liczby całkowitej w rozmiarze elementu.

Do celów rysowania własnym pola listy i pola kombi w stylu LBS_SORT lub CBS_SORT, konieczne jest przesłonięcie `OnCompareItem` metody.

Samodzielnie rysowania pola listy i pola kombi, `OnDeleteItem` nie jest zazwyczaj zastępowany. Można zastąpić `OnDeleteItem` Aby wykonywać żadnego specjalnego przetwarzania. Jeden przypadek, gdzie jest to stosowane jest, gdy dodatkowej pamięci lub inne zasoby, które są przechowywane z każdym elementem pola listy, jak pole lub pole kombi.

## <a name="examples-of-self-drawing-controls-and-menus"></a>Przykłady samodzielnie rysowania formantów i menu

Próbki MFC-ogólne [CTRLTEST](../visual-cpp-samples.md) zawiera przykłady menu własnym rysowania i pole listy własnym rysowania.

Najbardziej typowym przykładem własnym rysowania przycisk to przycisk mapy bitowej. Przycisk, który zawiera jeden, dwa lub trzy obrazy mapy bitowej w różnych regionach jest przycisk mapy bitowej. Na przykład znajduje się w klasie MFC [CBitmapButton](../mfc/reference/cbitmapbutton-class.md).

## <a name="dynamic-subclassing"></a>Dynamiczne podklasy

Od czasu do czasu można zmienić funkcjonalność obiektu, który już istnieje. Poprzednie przykłady wymaga dostosować formanty, zanim zostały one utworzone. Dynamiczne podklasy umożliwia dostosowywanie formantu, który został już utworzony.

Podklasy to termin Windows w celu zastąpienia <xref:System.Windows.Forms.Control.WndProc%2A> okna z niestandardową `WndProc` i wywoływania starego `WndProc` dla funkcje domyślne.

To nie należy mylić z pochodnym klasy języka C++. Wyjaśniające, warunki C++ *klasy bazowej* i *klasy pochodnej* są analogiczne do *superklasie* i *podklasy* w Windows model obiektu. C++ Tworzenie wartości pochodnych z podklasy MFC i Windows są podobne, z wyjątkiem C++ nie obsługuje podklasy dynamicznych.

`CWnd` Klasy zapewnia połączenie między obiektu języka C++ (pochodną `CWnd`) i obiekt window Windows (znana jako `HWND`).

Istnieją trzy sposoby wspólnego, które odnoszą się one:

- `CWnd` Tworzy `HWND`. Możesz zmodyfikować zachowanie w klasie pochodnej, tworząc klasę pochodną `CWnd`. `HWND` Jest tworzone, gdy Twoja aplikacja wywołuje [CWnd::Create](../mfc/reference/cwnd-class.md#create).

- Dołącza aplikacji `CWnd` do istniejącego `HWND`. Zachowanie istniejące okno nie jest modyfikowany. Jest przypadkiem delegowania, jest możliwe, wywołując [CWnd::Attach](../mfc/reference/cwnd-class.md#attach) alias istniejący `HWND` do `CWnd` obiektu.

- `CWnd` jest dołączony do istniejącego `HWND` i możesz zmodyfikować zachowanie w klasie pochodnej. Jest to nazywane dynamiczne tworzenie podklasy ponieważ Zmieniamy to zachowanie, a zatem klasy do obiektu Windows w czasie wykonywania.

Podklasy dynamicznej można osiągnąć za pomocą metody [CWnd::SubclassWindow](../mfc/reference/cwnd-class.md#subclasswindow) i[CWnd::SubclassDlgItem](../mfc/reference/cwnd-class.md#subclassdlgitem).

Dołącz oba procedury `CWnd` obiektu do istniejącego `HWND`. `SubclassWindow` Trwa `HWND` bezpośrednio. `SubclassDlgItem` jest funkcja pomocnicza, która przyjmuje identyfikator formantu i okno nadrzędne. `SubclassDlgItem` jest przeznaczona dla dołączanie obiektów C++ do formantów okna dialogowego utworzonego na podstawie szablonu okna dialogowego.

Zobacz [CTRLTEST](../visual-cpp-samples.md) przykład kilka przykładów zastosowania `SubclassWindow` i `SubclassDlgItem`.

## <a name="see-also"></a>Zobacz też

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)
