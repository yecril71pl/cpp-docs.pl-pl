---
title: 'TN029: Splitter — Windows'
ms.date: 11/04/2016
f1_keywords:
- vc.windows.splitter
helpviewer_keywords:
- TN029
- splitter windows [MFC], about splitter windows
ms.assetid: 2c57ce99-2a3c-4eff-9cea-baccb13af075
ms.openlocfilehash: 6c2f619d9cd619ca598c66ca657faa1b9dccaaa2
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58781734"
---
# <a name="tn029-splitter-windows"></a>TN029: Splitter — Windows

Ta uwaga opisuje MFC [klasa CSplitterWnd](../mfc/reference/csplitterwnd-class.md), zapewniającą okna dzieli i zarządza rozmiaru inne okna okienka.

## <a name="splitter-styles"></a>Splitter — style

Element `CSplitterWnd` obsługuje dwa różne style podziału systemu windows.

"Rozdzielaczy statyczne" okna rozdzielacza tworzy panele podczas jego tworzenia. Kolejność i liczba okienka nigdy nie ulegną zmianie. Paski podziału służą do zmiany rozmiaru z różnych okienek. Ten styl służy do wyświetlania klasy inny widok w każde okienko. Edytor grafiki Visual C++ i Menedżer plików Windows to przykłady programów, które używają tego stylu rozdzielacza. Ten styl okna rozdzielacza nie korzysta z okna rozdzielacza.

Dodatkowe okienka "rozdzielaczy dynamicznego", są tworzone i niszczone, jako użytkownik dzieli dane i anulować podziałów nowych widoków. Tego podziału rozpoczyna się od pojedynczego widoku i zapewnia okna rozdzielacza użytkownikowi zainicjować dzielenia. Okno rozdzielacza dynamicznie tworzy nowy obiekt widoku, gdy widok jest podzielona na jeden kierunek. Ten nowy obiekt widoku reprezentuje nowe okienko. Jeśli widok jest podzielona w dwóch kierunkach przy użyciu interfejsu klawiatury, okno rozdzielacza tworzy trzy nowe obiekty widoku trzy nowe okienka. Podczas podziału jest aktywna, Windows wyświetla okno rozdzielacza jako paskiem podziału pomiędzy okienka. Windows niszczy obiekty widoku dodatkowe użytkownik usunie podziału, kiedy niszczony jest oryginalny pozostaje widoku aż samo okna rozdzielacza. Program Microsoft Excel i Microsoft Word są przykładami aplikacji, które używają styl dynamiczny rozdzielacz.

Kiedy tworzysz dowolny rodzaj okno rozdzielacza, należy określić maksymalną liczbę wierszy i kolumn, które będą zarządzać rozdzielacza. Spowoduje to utworzenie statyczny rozdzielacz okienka, aby wypełnić wszystkie wiersze i kolumny. Dynamiczny rozdzielacz spowoduje utworzenie pierwszego okienka po `CSplitterWnd` zostanie utworzony.

Maksymalna liczba okienka, które można określić dla statycznych rozdzielaczy wynosi 16 wierszy i 16 kolumn. Dostępne są następujące zalecane konfiguracje:

- 1 wiersz x 2 kolumn: zwykle z różnymi okienkami

- Kolumna 2 wiersze x 1: zwykle z różnymi okienkami

- 2 wiersze x 2 kolumny: zwykle przy użyciu podobnych okienek

Maksymalna liczba okienek, które można określić dla dynamicznych rozdzielaczy wynosi 2 wiersze według 2 kolumny. Dostępne są następujące zalecane konfiguracje:

- 1 wiersz x 2 kolumn: dla danych kolumnowych

- Kolumna 2 wiersze x 1: w przypadku danych tekstowych lub innych

- 2 wiersze x 2 kolumny: siatki lub tabeli zorientowane na dane

## <a name="splitter-examples"></a>Splitter — przykłady

Wiele przykładowych programów MFC użyj okna podziału, bezpośrednio lub pośrednio. Próbki MFC-ogólne [VIEWEX](../overview/visual-cpp-samples.md) ilustruje kilka zastosowań rozdzielaczy statyczne, w tym jak dokonać podziału należy umieścić w rozdzielacz.

ClassWizard służy również do tworzenia nowego wiele dokumentów interfejsu (MDI) podrzędnych ramki okna klasę, która zawiera okno rozdzielacza. Aby uzyskać więcej informacji na temat okna podziału, zobacz [wiele typów dokumentów, widoków i ramek Windows](../mfc/multiple-document-types-views-and-frame-windows.md).

## <a name="terminology-used-by-implementation"></a>Terminologia używana przez implementację

Oto lista warunków, które są specyficzne dla okna podziału:

`CSplitterWnd`: Okno, który zawiera podział okienka kontrolek i paski przewijania, które są wspólne dla wszystkich okienek na wiersz lub kolumnę. Określ wierszy i kolumn z międzynarodowymi numerami identyfikującymi liczony od zera (pierwszy okienko jest wiersz = 0 i kolumna = 0).

Okienko: Okno specyficzne dla aplikacji, `CSplitterWnd` zarządza. Okienko zazwyczaj jest obiektem, który jest tworzony na podstawie [CView Class](../mfc/reference/cview-class.md), ale może być dowolnym [CWnd](../mfc/reference/cwnd-class.md) obiekt, który ma identyfikator podrzędny odpowiednie okna.

Do użycia `CWnd`-pochodnych obiektu, przekazać RUNTIME_CLASS obiektu do `CreateView` funkcji, jak gdyby były używane `CView`-klasy pochodnej. Klasa należy użyć DECLARE_DYNCREATE i IMPLEMENT_DYNCREATE, ponieważ struktura używa dynamiczne tworzenie w środowisku uruchomieniowym. Mimo że istnieje duża ilość kodu w `CSplitterWnd` specyficznego `CView` klasy [CObject::IsKindOf](../mfc/reference/cobject-class.md#iskindof) jest zawsze używana, zanim te akcje są wykonywane.

Pasek podziału: Formant, który jest umieszczany między wierszami i kolumnami okienka. Może służyć aby dopasować rozmiar wierszy lub kolumn okienek.

Okno rozdzielacza: Kontrolki w dynamicznym `CSplitterWnd` służące do tworzenia nowych wierszy lub kolumn okienka. Jest on umieszczony u góry pasków przewijania w pionie lub w lewo poziome paski przewijania.

Przecięcie rozdzielacz: Przecięcie pionowy pasek podziału i poziomy pasek podziału. Można przeciągnąć go do dopasowania rozmiaru wierszy i kolumn okienka jednocześnie.

## <a name="shared-scroll-bars"></a>Udostępnione paski przewijania

`CSplitterWnd` Klasy obsługuje również paski przewijania udostępnionych. Te formanty paska przewijania są elementami podrzędnymi `CSplitterWnd` są współdzielone z różnymi okienkami w rozdzielacza.

Na przykład w oknie kolumna 1 wiersz x 2, można określić WS_VSCROLL podczas tworzenia `CSplitterWnd`. Windows tworzy specjalne pasek przewijania, która jest współużytkowana przez dwa okienka.

```
[      ][      ][^]
[pane00][pane01][|]
[      ][      ][v]
```

Gdy użytkownik przesuwa paska przewijania, WM_VSCROLL komunikaty będą wysyłane do obu widokach. Gdy którymś z widoków Ustawia położenie paska przewijania, pasek przewijania udostępnione zostaną ustawione.

Należy pamiętać o tym, czy paski przewijania udostępnionego są najbardziej przydatne z podobnymi obiektami, widok. Po przemieszaniu widoków różniące się typy w rozdzielacz może być konieczne pisanie kodu specjalne do koordynowania ich pozycji przewijania. Wszelkie `CView`-pochodne klasy, która używa `CWnd` paska przewijania, interfejsy API będzie delegować do paska przewijania udostępnionych, jeśli taki istnieje. `CScrollView` Implementacja jest jednym z przykładów `CView` klasę, która obsługuje udostępnione paski przewijania. Klasy, które nie pochodzą z `CView`, klasy, które polegają na paski przewijania-control lub klasy, które używają standardowe wdrożenia Windows (na przykład `CEditView`) nie będzie działać z funkcją paska przewijania udostępnionego `CSplitterWnd`.

## <a name="minimum-sizes"></a>Minimalny rozmiar

Dla każdego wiersza jest minimalną wysokość wiersza, a dla każdej kolumny jest minimalną szerokość kolumny. To minimum gwarantuje, że okienko nie jest zbyt mały, który będzie wyświetlany szczegółowy.

W oknie statyczny rozdzielacz wstępny wiersz minimalna wysokość i szerokość kolumny to 0. Dynamiczne okno rozdzielacza, aby uzyskać początkowy wiersz minimalna wysokość i szerokość kolumny są ustawiane przez *sizeMin* parametru `CSplitterWnd::Create` funkcji.

Te rozmiary minimalne można zmienić za pomocą [CSplitterWnd::SetRowInfo](../mfc/reference/csplitterwnd-class.md#setrowinfo) i [CSplitterWnd::SetColumnInfo](../mfc/reference/csplitterwnd-class.md#setcolumninfo) funkcji.

## <a name="actual-vs-ideal-sizes"></a>Stan faktyczny a. Idealna rozmiarów

Układ okienka w oknie rozdzielacz zależy od rozmiaru ramki, który je zawiera. Gdy użytkownik zmienia rozmiar ramki zawierającego `CSplitterWnd` powoduje przeniesienie i zmienia rozmiar okienka, tak, aby mieściły się jak to możliwe.

Użytkownik może ręcznie ustawić wiersza rozmiary szerokość wysokość i kolumny lub program można ustawić rozmiar idealny przy użyciu `CSplitterWnd` klasy. Rzeczywisty rozmiar może być mniejszy lub większy od idealnie. Windows dopasuje rzeczywisty rozmiar, jeśli nie jest wystarczająco dużo miejsca, aby wyświetlić rozmiar idealny lub jeśli istnieje zbyt wiele puste miejsce, do prawej lub u dołu okna rozdzielacza.

## <a name="custom-controls"></a>Formanty niestandardowe

Można zastąpić wiele funkcji, aby zapewnić zachowanie niestandardowe i dostosowanego interfejsu. Możesz przesłonić ten pierwszy zestaw zapewnienie alternatywne obrazów dla różnych składników graficzny okna rozdzielacza.

- `virtual void OnDrawSpltter(CDC* pDC, ESplitType nType, const CRect& rect);`

- `virtual void OnInvertTracker(const CRect& rect);`

Możesz wywołać tę funkcję, aby utworzyć współdzieloną kontrolkę paska przewijania. Można zastąpić go, aby utworzyć dodatkowe kontrolki obok paska przewijania.

- `virtual BOOL CreateScrollBarCtrl(DWORD dwStyle, UINT nID);`

Te funkcje zaimplementować logikę dynamiczne okno rozdzielacza. Możesz przesłonić te zapewniają bardziej zaawansowana logika rozdzielacza.

- `virtual void DeleteView(int row, int col);`

- `virtual BOOL SplitRow(int cyBefore);`

- `virtual BOOL SplitColumn(int cxBefore);`

- `virtual void DeleteRow(int rowDelete);`

- `virtual void DeleteColumn(int colDelete);`

## <a name="cview-functionality"></a>Funkcje CView

`CView` Klasy używa następujących poleceń wysokiego poziomu do delegowania `CSplitterWnd` implementacji. Ponieważ te polecenia są wirtualne, standardowe `CView` implementacji nie będzie wymagać całą `CSplitterWnd` implementacji w. W przypadku aplikacji, które używają `CView` , ale nie `CSplitterWnd`, `CSplitterWnd` implementacji nie będzie połączony z aplikacją.

- `virtual BOOL CanActivateNext(BOOL bPrev = FALSE);`

   Sprawdza, czy id_next_pane — lub id_prev_pane — jest to obecnie możliwe.

- `virtual void ActivateNext(BOOL bPrev = FALSE);`

   Wykonuje polecenie "Następne okienko" lub "Poprzednie okienko".

- `virtual BOOL DoKeyboardSplit();`

   Wykonuje polecenie podziału klawiatury, zwykle "podział okna".

## <a name="see-also"></a>Zobacz także

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)
