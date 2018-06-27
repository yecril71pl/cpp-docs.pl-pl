---
title: 'TN014: Formanty niestandardowe | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 9625b3eafa75bdafff7d17ea63db8904d9b49529
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2018
ms.locfileid: "36956850"
---
# <a name="tn014-custom-controls"></a>TN014: formanty niestandardowe
Ta uwaga opisuje Obsługa MFC dla formantów niestandardowych i własnym rysowania. On również opisuje podklasy dynamicznej oraz relacji między [CWnd](../mfc/reference/cwnd-class.md) obiektów i `HWND`s.  
  
 MFC Przykładowa aplikacja CTRLTEST ilustruje sposób używania wielu formantów niestandardowych. Zobacz kod źródłowy przykładowej ogólne MFC [CTRLTEST](../visual-cpp-samples.md) i pomocy online.  
  
## <a name="owner-draw-controlsmenus"></a>Formanty/menu rysowania przez właściciela  
 System Windows zapewnia obsługę formantów rysowania przez właściciela i menu za pomocą komunikatów systemu Windows. Okno nadrzędne kontrolki lub menu odbiera tych wiadomości i wywołania funkcji w odpowiedzi. Można zastąpić te funkcje, aby dostosować wygląd i zachowanie kontrolka rysowana przez właściciela lub menu.  
  
 MFC bezpośrednio obsługuje rysowania przez właściciela z następujących funkcji:  
  
- [CWnd::OnDrawItem](../mfc/reference/cwnd-class.md#ondrawitem)  
  
- [CWnd::OnMeasureItem](../mfc/reference/cwnd-class.md#onmeasureitem)  
  
- [CWnd::OnCompareItem](../mfc/reference/cwnd-class.md#oncompareitem)  
  
- [CWnd::OnDeleteItem](../mfc/reference/cwnd-class.md#ondeleteitem)  
  
 Można zastąpić te funkcje w Twojej `CWnd` klasy do zaimplementowania niestandardowego rysowania zachowanie.  
  
 Takie podejście nie prowadzi do kodu do ponownego użycia. Jeśli masz dwóch podobnych formantów w dwóch różnych `CWnd` klas, musisz zaimplementować zachowanie kontrolki niestandardowej w dwóch lokalizacjach. Architektura obsługiwane MFC własnym rysowania formantu rozwiązuje ten problem.  
  
## <a name="self-draw-controls-and-menus"></a>Rysuj własnym menu i formantów  
 MFC udostępnia domyślną implementację (w `CWnd` i [cmenu —](../mfc/reference/cmenu-class.md) klasy) dla wiadomości standardowe rysowania przez właściciela. Ta domyślna implementacja będzie zdekodować parametrów rysowania przez właściciela, a następnie delegatem wiadomości rysowania przez właściciela menu lub formantów. Jest to własnym rysowania ponieważ kod rysowania jest w klasie lub menu nie znajduje się w oknie właściciela.  
  
 Za pomocą formantów własnym rysowania można utworzyć klasy formantów wielokrotnego użytku, które umożliwia wyświetlanie formantu semantyki rysowania przez właściciela. Kod rysowania formantu jest klasy formantu nie jego elementu nadrzędnego. To zorientowane obiektowo podejście do programowania kontrolek niestandardowych. Dodaj poniższą listę funkcji do klas własnym rysowania:  
  
-   W przypadku przycisków, własnym rysowania:  
  
 ```  
    CButton:DrawItem(LPDRAWITEMSTRUCT);
*// insert code to draw this button  
 ```  
  
-   Rysuj własnym menu:  
  
 ```  
    CMenu:MeasureItem(LPMEASUREITEMSTRUCT);
*// insert code to measure the size of an item in this menu  
    CMenu:DrawItem(LPDRAWITEMSTRUCT);
*// insert code to draw an item in this menu  
 ```  
  
-   Dla pola listy z własnym rysowania:  
  
 ```  
    CListBox:MeasureItem(LPMEASUREITEMSTRUCT);
*// insert code to measure the size of an item in this list box  
    CListBox:DrawItem(LPDRAWITEMSTRUCT);
*// insert code to draw an item in this list box  
 
    CListBox:CompareItem(LPCOMPAREITEMSTRUCT);
*// insert code to compare two items in this list box if LBS_SORT  
    CListBox:DeleteItem(LPDELETEITEMSTRUCT);
*// insert code to delete an item from this list box  
 ```  
  
-   Dla pola kombi własnym rysowania:  
  
 ```  
    CComboBox:MeasureItem(LPMEASUREITEMSTRUCT);
*// insert code to measure the size of an item in this combo box  
    CComboBox:DrawItem(LPDRAWITEMSTRUCT);
*// insert code to draw an item in this combo box  
 
    CComboBox:CompareItem(LPCOMPAREITEMSTRUCT);
*// insert code to compare two items in this combo box if CBS_SORT  
    CComboBox:DeleteItem(LPDELETEITEMSTRUCT);
*// insert code to delete an item from this combo box  
 ```  
  
 Szczegółowe informacje na temat struktury rysowania przez właściciela ([DRAWITEMSTRUCT](../mfc/reference/drawitemstruct-structure.md), [MEASUREITEMSTRUCT](../mfc/reference/measureitemstruct-structure.md), [COMPAREITEMSTRUCT](../mfc/reference/compareitemstruct-structure.md), i [DELETEITEMSTRUCT](../mfc/reference/deleteitemstruct-structure.md)) można znaleźć w dokumentacji MFC `CWnd::OnDrawItem`, `CWnd::OnMeasureItem`, `CWnd::OnCompareItem`, i `CWnd::OnDeleteItem` odpowiednio.  
  
## <a name="using-self-draw-controls-and-menus"></a>Za pomocą formantów własnym rysowania i menu  
 Własnym rysowania menu, konieczne jest przesłonięcie zarówno `OnMeasureItem` i `OnDrawItem` metody.  
  
 Pola listy własnym rysowania i pola kombi, konieczne jest przesłonięcie `OnMeasureItem` i `OnDrawItem`. Należy określić lbs_ownerdrawvariable — styl pola listy lub pola kombi cbs_ownerdrawvariable — styl szablonu okna dialogowego. Styl OWNERDRAWFIXED nie będzie działać z własnym narysować elementy stałego elementu wysokość jest ustalana przed własnym narysować kontrolki są dołączone do pola listy. (Można użyć metod [CListBox::SetItemHeight](../mfc/reference/clistbox-class.md#setitemheight) i [CComboBox::SetItemHeight](../mfc/reference/ccombobox-class.md#setitemheight) Aby obejść to ograniczenie.)  
  
 Przełączanie do stylu OWNERDRAWVARIABLE wymusi system, aby stosował styl NOINTEGRALHEIGHT do formantu. Ponieważ kontrolka nie może obliczyć całkowity wysokość o zmiennej wielkości elementów, domyślny styl INTEGRALHEIGHT jest ignorowana, a formant zawsze jest NOINTEGRALHEIGHT. Jeśli elementy są stałą wysokość, uniemożliwia elementów podzielonych na części są rysowane przez określenie rozmiaru formantu jako liczba całkowita mnożnik rozmiarze elementu.  
  
 Na własnym Rysowanie pola listy i pola kombi w stylu lbs_sort — lub cbs_sort —, konieczne jest przesłonięcie `OnCompareItem` metody.  
  
 Na własnym Rysowanie pola listy i pola kombi `OnDeleteItem` zwykle nie jest przeciążona. Można zastąpić `OnDeleteItem` Jeśli chcesz wykonywać żadnych specjalnych przetwarzania. Jeden przypadek, których to dotyczy jest gdy dodatkowej pamięci lub innych zasobów, które są przechowywane z każdego elementu pola listy, jak pola lub kombi.  
  
## <a name="examples-of-self-drawing-controls-and-menus"></a>Przykłady własnym rysowania formantów i menu  
 Ogólne MFC próbki [CTRLTEST](../visual-cpp-samples.md) przedstawiono przykłady menu własnym rysowania i pole listy własnym rysowania.  
  
 Najbardziej typowym przykładem przycisk własnym rysowania znajduje się przycisk mapy bitowej. Przycisk mapy bitowej jest przycisku, który zawiera jedną, dwie lub trzy obrazy mapy bitowej do innych stanów. Na przykład znajduje się w klasie MFC [CBitmapButton](../mfc/reference/cbitmapbutton-class.md).  
  
## <a name="dynamic-subclassing"></a>Podklasy dynamicznej  
 Od czasu do czasu można zmienić funkcje obiektu, który już istnieje. Poprzednich przykładach wymagane do dostosowywania formanty przed ich utworzenia. Podklasy dynamiczne umożliwia dostosowywanie formantu, który został już utworzony.  
  
 Podklasy jest określenie systemu Windows do zastępowania [WndProc](http://msdn.microsoft.com/en-us/94ba8ffa-3c36-46d4-ac74-9bd10b1ffd26) okna z dostosowany `WndProc` i wywoływania stary `WndProc` dla domyślna funkcjonalność.  
  
 To nie należy mylić z pochodnym klasy C++. Wyjaśnienia, warunki C++ *klasa podstawowa* i *klasy* są podobne do *superklasie* i *podklasy* w systemie Windows model obiektu. Tworzenie wartości pochodnych C++ z MFC i Windows podklasy są podobne, z wyjątkiem C++ nie obsługuje dynamicznej podklasy.  
  
 `CWnd` Klasa udostępnia połączenie między obiektem C++ (pochodną `CWnd`) i obiektu okna systemu Windows (znana jako `HWND`).  
  
 Istnieją trzy sposoby wspólne, które odnoszą się one:  
  
- `CWnd` Tworzy `HWND`. Można zmodyfikować zachowanie w klasie pochodnej, tworząc klasę pochodzącą od `CWnd`. `HWND` Jest tworzony, gdy aplikacja wywołuje [CWnd::Create](../mfc/reference/cwnd-class.md#create).  
  
-   Dołącza aplikacji `CWnd` do istniejącej `HWND`. Zachowanie istniejące okno nie jest modyfikowany. To jest delegowanie i jest możliwe przez wywołanie metody [CWnd::Attach](../mfc/reference/cwnd-class.md#attach) alias istniejący `HWND` do `CWnd` obiektu.  
  
- `CWnd` jest dołączony do istniejącego `HWND` i zachowanie w klasie pochodnej można zmienić. Jest to nazywane dynamiczne tworzenie podklas, ponieważ Zmieniamy zachowanie, a w związku z tym klasę obiektu systemu Windows w czasie wykonywania.  
  
 Podklasy dynamicznej można osiągnąć za pomocą metody [CWnd::SubclassWindow](../mfc/reference/cwnd-class.md#subclasswindow) i[CWnd::SubclassDlgItem](../mfc/reference/cwnd-class.md#subclassdlgitem).  
  
 Dołącz zarówno procedury `CWnd` obiektu do istniejącego `HWND`. `SubclassWindow` Trwa `HWND` bezpośrednio. `SubclassDlgItem` jest to funkcja pomocnika pobierającej Identyfikatora formantu i okno nadrzędne. `SubclassDlgItem` jest przeznaczony do dołączania obiektów C++ do formantów okna dialogowego utworzone na podstawie szablonu okna dialogowego.  
  
 Zobacz [CTRLTEST](../visual-cpp-samples.md) przykład przykłady zastosowania `SubclassWindow` i `SubclassDlgItem`.  
  
## <a name="see-also"></a>Zobacz też  
 [Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)   
 [Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)

