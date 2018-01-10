---
title: "TN029: Okna podziału | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.windows.splitter
dev_langs: C++
helpviewer_keywords:
- TN029
- splitter windows [MFC], about splitter windows
ms.assetid: 2c57ce99-2a3c-4eff-9cea-baccb13af075
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 95b7db2678c03b0508a1507567f8bedcf243cd4a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="tn029-splitter-windows"></a>TN029: okna podziału
Ta uwaga opisuje MFC [CSplitterWnd klasy](../mfc/reference/csplitterwnd-class.md), zapewniające okno dzieli i zarządza rozmiaru innych okien okienka.  
  
## <a name="splitter-styles"></a>Style podziału  
 A `CSplitterWnd` obsługuje dwóch różnych stylów podział systemu windows.  
  
 "Rozdzielaczy statyczny" okna podziału tworzy panele po jego utworzeniu. Kolejność i liczba okienka nigdy nie ulegną zmianie. Paski podziału służą do zmiany rozmiaru z różnych okienek. Ten styl służy do wyświetlenia w poszczególnych okienkach klasy inny widok. Edytor grafiki Visual C++ i Menedżera plików systemu Windows są przykłady programów, które używają tego stylu podziału. Ten styl okna podziału nie korzysta z pola podziału.  
  
 Dodatkowe okienka "rozdzielaczy dynamiczny", są tworzone i niszczone jako użytkownik podziałów i podziałów un nowych widoków. Tego podziału rozpoczyna się od jednego widoku i zawiera pola podziału dla użytkownika zainicjować dzielenia. Okna podziału dynamicznie tworzy nowy obiekt widoku, gdy widok jest rozdzielona w jednym kierunku. Ten nowy obiekt widoku reprezentuje nowe okienko. Jeśli widok jest podzielona w dwóch kierunkach przy użyciu interfejsu klawiatury, okna podziału tworzy trzy nowe obiekty widoku trzy nowe okienka. Podczas podziału jest aktywny, systemu Windows wyświetla okno podziału jako pasek podziału między okienka. Windows niszczy dodatkowe wyświetlanie obiektów, gdy użytkownik usuwa podziału, ale oryginalny pozostaje widoku do samej siebie okna podziału zostanie zniszczony. Program Microsoft Excel i Microsoft Word przedstawiono przykładowe aplikacje, które używają stylu dynamiczny rozdzielacz.  
  
 Podczas tworzenia okna podziału dowolnego typu, należy określić maksymalną liczbę wierszy i kolumn, które będą zarządzać rozdzielacza. Statyczny rozdzielacz utworzy okienka, aby wypełnić wszystkie wiersze i kolumny. Dynamiczny rozdzielacz zostanie utworzona tylko pierwszy okienka po `CSplitterWnd` jest tworzony.  
  
 Maksymalna liczba okienka, które można określić dla statycznych rozdzielaczy wynosi 16 wierszy i 16 kolumn. Zalecane konfiguracje są:  
  
-   kolumny 1 wiersz x 2: zwykle z różnych okienek  
  
-   Kolumna 2 wierszy x 1: zwykle z różnych okienek  
  
-   wiersze 2 x 2 kolumny: zwykle z okienka podobne  
  
 Maksymalna liczba okienkami, których można określić dla dynamicznej rozdzielaczy wynosi 2 wierszy i kolumn 2. Zalecane konfiguracje są:  
  
-   kolumny 1 wiersz x 2: kolumnowy danych  
  
-   Kolumna 2 wierszy x 1: w przypadku danych tekstowych lub innych  
  
-   wiersze 2 x 2 kolumny: siatki lub tabeli zorientowane na danych  
  
## <a name="splitter-examples"></a>Przykłady podziału  
 Okna podziału wiele MFC przykładowe programy używać bezpośrednio lub pośrednio. Ogólne MFC próbki [VIEWEX](../visual-cpp-samples.md) przedstawiono kilka zastosowań rozdzielaczy statycznych, łącznie ze sposobem umieścić rozdzielacza w rozdzielacza.  
  
 Aby utworzyć nową wielu dokumentów interfejsu (MDI) podrzędnych ramki okna klasę, która zawiera okna dzielącego umożliwia także ClassWizard. Aby uzyskać więcej informacji na okna podziału, zobacz [wiele typów dokumentów, widoków i okien ramowych](../mfc/multiple-document-types-views-and-frame-windows.md).  
  
## <a name="terminology-used-by-implementation"></a>Terminologia używana przez implementację  
 Oto lista warunków, które są specyficzne dla okna podziału:  
  
 `CSplitterWnd`:  
 Okno, które zawiera podział okienku kontrolek i paski przewijania, które są wspólne dla wszystkich okienka na wiersz lub kolumnę. Określ wiersze i kolumny z numerami od zera (pierwszego okienka jest wiersz = 0, kolumna = 0).  
  
 Okienko:  
 Okno specyficzne dla aplikacji, która `CSplitterWnd` zarządza. Okienko jest zazwyczaj obiekt, który jest pochodną [cview — klasa](../mfc/reference/cview-class.md), ale może być dowolną [CWnd](../mfc/reference/cwnd-class.md) obiekt, który ma identyfikator podrzędnych odpowiednie okna.  
  
 Do używania `CWnd`-pochodnych obiektów należy przekazać `RUNTIME_CLASS` obiektu do `CreateView` działać tak jak w przypadku używania `CView`-pochodnej klasy. Należy użyć klasy `DECLARE_DYNCREATE` i `IMPLEMENT_DYNCREATE` ponieważ platformę używa dynamiczne tworzenie w czasie wykonywania. Mimo że wiele kodu w `CSplitterWnd` jest specyficzne dla `CView` klasy [CObject::IsKindOf](../mfc/reference/cobject-class.md#iskindof) jest zawsze używana, zanim te czynności są wykonywane.  
  
 Pasek podziału:  
 Formant, który znajduje się między wierszy i kolumn okienka. Może służyć do dostosowania rozmiarów wierszy lub kolumn okienka.  
  
 Pole podziału:  
 Formant w dynamicznym `CSplitterWnd` czy służy do tworzenia nowych wierszy lub kolumn okienka. Jest on umieszczony na górze pasków przewijania pionowego lub w lewo paski przewijania w poziomie.  
  
 Część wspólną podziału:  
 Część wspólną pionowy pasek podziału i poziomy pasek podziału. Możesz przeciągnąć, aby dostosować rozmiar wiersza i kolumny okienka jednocześnie.  
  
## <a name="shared-scroll-bars"></a>Udostępniony paski przewijania  
 `CSplitterWnd` Klasa obsługuje również pasków przewijania udostępnionego. Formanty paska te przewijania są elementami podrzędnymi `CSplitterWnd` i są współużytkowane z różnych okienek w rozdzielacza.  
  
 Na przykład w oknie kolumna 1 wiersz x 2, można określić ws_vscroll — podczas tworzenia `CSplitterWnd`. System Windows tworzy specjalne pasek przewijania współużytkowanych przez dwa okienka.  
  
```  
[      ][      ][^]  
[pane00][pane01][|]  
[      ][      ][v]  
```  
  
 Gdy użytkownik przesuwa na pasku przewijania `WM_VSCROLL` wiadomości zostaną wysłane do obu widokach. Gdy widoku albo Ustawia położenie paska przewijania, pasek przewijania udostępniony zostanie ustawiona.  
  
 Należy zauważyć, że paski przewijania udostępnionego najbardziej przydatne z podobnymi obiektami widoku. Jeśli mieszać widoków o różnych typach w rozdzielacza, mogą mieć do pisania kodu specjalne skoordynowania stanowisk przewijania. Wszelkie `CView`-klasy, która używa `CWnd` paska przewijania interfejsów API będzie delegować do paska przewijania udostępnionego, jeśli istnieje. `CScrollView` Implementacja jest jednym z przykładów `CView` klasy, która obsługuje udostępnione paski przewijania. Klasy, które nie pochodzą z `CView`, klasy, które opierają się na paski przewijania-control lub klasy, które użyć standardowego implementacji systemu Windows (na przykład `CEditView`) nie będzie działać z funkcją paska przewijania udostępnionych z `CSplitterWnd`.  
  
## <a name="minimum-sizes"></a>Minimalny rozmiar  
 Dla każdego wiersza jest minimalną wysokość wiersza i dla każdej kolumny jest minimalną szerokość kolumny. Ta minimalna wielkość gwarantuje okienko nie jest za mały, który będzie wyświetlany szczegółowy.  
  
 Okna podziału statycznych początkowej wiersza minimalna wysokość i szerokość kolumny jest 0. Dla dynamiczne okno podziału, początkowej wiersza minimalna wysokość i szerokość kolumny są ustawiane przez `sizeMin` parametr `CSplitterWnd::Create` funkcji.  
  
 Minimalne rozmiary można zmieniać za pomocą [CSplitterWnd::SetRowInfo](../mfc/reference/csplitterwnd-class.md#setrowinfo) i [CSplitterWnd::SetColumnInfo](../mfc/reference/csplitterwnd-class.md#setcolumninfo) funkcji.  
  
## <a name="actual-vs-ideal-sizes"></a>Rzeczywiste vs. Nadaje się doskonale rozmiary  
 Układ okienka w oknie podziału zależy od rozmiaru ramki, który je zawiera. Gdy użytkownik zmienia rozmiar ramki zawierającego `CSplitterWnd` zmienia położenie i zmienia rozmiar okienka, tak aby mieściły oraz możliwości.  
  
 Użytkownik może ręcznie ustawić wiersza rozmiary szerokość wysokości i kolumny lub program można ustawić rozmiar idealny przy użyciu `CSplitterWnd` klasy. Rzeczywisty rozmiar może być mniejsza lub większa od stanu idealnego. Windows dopasuje rzeczywisty rozmiar, jeśli nie jest wystarczająco dużo miejsca, aby wyświetlić rozmiar idealny lub jest zbyt dużej ilości wolnego miejsca do prawej lub dolnej części okna podziału.  
  
## <a name="custom-controls"></a>Formanty niestandardowe  
 Można zastąpić wiele funkcji, aby zapewnić zachowanie dostosowane i dostosowany interfejs. Można zastąpić pierwszego zestawu do zapewnienia alternatywnych obrazów dla różnych składników graficznego okna podziału.  
  
- `virtual void OnDrawSpltter(CDC* pDC, ESplitType nType, const CRect& rect);`  
  
- `virtual void OnInvertTracker(const CRect& rect);`  
  
 Możesz wywoływać tej funkcji, aby utworzyć udostępniony pasek przewijania. Można je zastąpić, aby utworzyć dodatkowe kontrole obok paska przewijania.  
  
- `virtual BOOL CreateScrollBarCtrl(DWORD dwStyle, UINT nID);`  
  
 Te funkcje implementują logikę okna dynamiczny rozdzielacz. Można zastąpić je do zapewnienia bardziej zaawansowanych logiki podziału.  
  
- `virtual void DeleteView(int row, int col);`  
  
- `virtual BOOL SplitRow(int cyBefore);`  
  
- `virtual BOOL SplitColumn(int cxBefore);`  
  
- `virtual void DeleteRow(int rowDelete);`  
  
- `virtual void DeleteColumn(int colDelete);`  
  
## <a name="cview-functionality"></a>Cview — funkcja  
 `CView` Klasy używa następujących poleceń wysokiego poziomu do delegowania `CSplitterWnd` implementacji. Ponieważ te polecenia są wirtualny, standardowe `CView` implementacji nie będzie wymagać całą `CSplitterWnd` wdrożenia mają być łączone w. Dla aplikacji używających `CView` , ale nie `CSplitterWnd`, `CSplitterWnd` wdrożenia nie zostaną połączone z aplikacją.  
  
 `virtual BOOL CanActivateNext(BOOL bPrev = FALSE);`  
 Sprawdza, czy id_next_pane — lub id_prev_pane — jest obecnie możliwe.  
  
 `virtual void ActivateNext(BOOL bPrev = FALSE);`  
 Wykonuje polecenie "Następne okienko" lub "Poprzednie okienko".  
  
 `virtual BOOL DoKeyboardSplit();`  
 Wykonuje polecenie podziału klawiatury, zwykle "podział okna".  
  
## <a name="see-also"></a>Zobacz też  
 [Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)   
 [Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)

