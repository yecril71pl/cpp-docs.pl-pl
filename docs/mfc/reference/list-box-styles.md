---
title: Style pola listy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- LBS_STANDARD
- LBS_NODATA
- LBS_OWNERDRAWVARIABLE
- LBS_EXTENDEDSEL
- LBS_USETABSTOPS
- LBS_WANTKEYBOARDINPUT
- LBS_NOTIFY
- LBS_DISABLENOSCROLL
- LBS_HASSTRINGS
- LBS_NOREDRAW
- LBS_NOSEL
- LBS_NOINTEGRALHEIGHT
- LBS_MULTICOLUMN
- LBS_SORT
- LBS_MULTIPLESEL
- LBS_OWNERDRAWFIXED
dev_langs:
- C++
helpviewer_keywords:
- LBS_NOSEL constant [MFC]
- LBS_NOREDRAW constant [MFC]
- LBS_HASSTRINGS constant [MFC]
- LBS_OWNERDRAWFIXED constant [MFC]
- LBS_WANTKEYBOARDINPUT constant [MFC]
- LBS_STANDARD constant [MFC]
- LBS_MULTIPLESEL constant [MFC]
- LBS_OWNERDRAWVARIABLE constant [MFC]
- LBS_DISABLENOSCROLL constant [MFC]
- LBS_NODATA constant [MFC]
- list boxes [MFC], styles
- LBS_EXTENDEDSEL constant [MFC]
- LBS_MULTICOLUMN constant [MFC]
- LBS_NOTIFY constant [MFC]
- LBS_USETABSTOPS constant [MFC]
- LBS_NOINTEGRALHEIGHT constant [MFC]
- LBS_SORT constant
ms.assetid: 3f357b8d-9118-4f41-9e28-02ed92d1e88f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 90441984aa8212212c3a9d4ea99cfb5b36127a03
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="list-box-styles"></a>Style pola listy
-   **Lbs_disablenoscroll —** pole listy zawiera wyłączenia pionowy pasek przewijania podczas pole listy zawiera za mało elementów przewijanie. Bez tego stylu pasek przewijania jest ukryty, gdy pole listy zawiera za mało elementów.  
  
-   **Lbs_extendedsel —** użytkownik może wybrać wiele elementów przy użyciu klawisza SHIFT i myszy lub specjalne kombinacje klawiszy.  
  
-   **Lbs_hasstrings —** Określa pole listy rysowania przez właściciela, który zawiera elementy składające się z ciągów. Pole listy zachowuje pamięci i wskaźniki ciągi, tak aby korzystać z aplikacji `GetText` funkcji członkowskiej pobrać tekstu dla danego elementu.  
  
-   **Lbs_multicolumn —** określa wielokolumnowe pole listy, które jest przewijane w poziomie. `SetColumnWidth` Funkcji członkowskiej Ustawia szerokość kolumn.  
  
-   **Lbs_multiplesel —** wybór ciągu jest przełączane każdym razem, użytkownik kliknie lub kliknie dwukrotnie ciąg. Można wybrać dowolną liczbę ciągów.  
  
-   **Lbs_nodata —** Określa pole listy braku danych. Określ ten styl, gdy liczba elementów w polu listy przekroczy tysiąca. Pole nie danych listy musi mieć również **lbs_ownerdrawfixed —** stylów, ale nie może zawierać **lbs_sort —** lub **lbs_hasstrings —** stylu.  
  
     Pole listy braku danych podobny pole listy rysowane przez właściciela, z tą różnicą, że go nie zawiera string lub bitmap danych dla elementu. Aby dodać, wstawiania lub usuwania elementu zawsze Ignoruj wszystkie podane elementu danych. Niepowodzenie żądania, aby zawsze znaleźć ciąg w polu listy. Wysyła systemu `WM_DRAWITEM` wiadomości do okna nadrzędnego, gdy musi zostać narysowany element. Identyfikator elementu członkiem `DRAWITEMSTRUCT` struktury przekazany z `WM_DRAWITEM` wiadomości określa numer wiersza elementu, który ma być rysowany. Pole nie danych listy nie wysyła `WM_DELETEITEM` wiadomości.  
  
-   **Lbs_nointegralheight —** rozmiar pola listy jest rozmiarem ściśle określonym przez aplikację podczas jej tworzenia listy. Zazwyczaj Windows rozmiary pola listy, aby pole listy nie wyświetla elementów podzielonych na części.  
  
-   **Lbs_noredraw —** wyświetlania pola listy nie jest aktualizowany, gdy zostaną wprowadzone zmiany. Ten styl można zmienić w dowolnym momencie, wysyłając **WM_SETREDRAW** wiadomości.  
  
-   **Lbs_nosel —** Określa, że pole listy zawiera elementy, które mogą być wyświetlane, ale nie jest zaznaczone.  
  
-   **Lbs_notify —** okno nadrzędne odbiera komunikat wejściowy zawsze, gdy użytkownik kliknie lub kliknie dwukrotnie ciąg.  
  
-   **Lbs_ownerdrawfixed —** właściciel pola listy jest odpowiedzialny za rysowania zawartością; elementy w polu listy są tego samego wysokość.  
  
-   **Lbs_ownerdrawvariable —** właściciel pola listy jest odpowiedzialny za rysowania zawartością; elementy w polu listy są zmiennej wysokości.  
  
-   **Lbs_sort —** ciągów w polu listy są sortowane w kolejności alfabetycznej.  
  
-   **Lbs_standard —** ciągów w polu listy są posortowane alfabetycznie i okno nadrzędne otrzyma komunikat wejściowy zawsze, gdy użytkownik kliknie lub kliknie dwukrotnie ciąg. Pole listy zawiera obramowania ze wszystkich stron.  
  
-   **Lbs_usetabstops —** umożliwia okno listy rozpozna i rozszerzy znaki tabulacji podczas rysowania jego ciągów. Domyślne pozycji tabulatorów są 32 jednostki okna dialogowego. (Jednostki okna dialogowego jest odległość pozioma lub pionowa. Jednostki okna dialogowego w poziomie jest równa jednej czwartej bieżąca jednostka podstawowa szerokość okna dialogowego. Jednostki podstawowy okna dialogowego są obliczane na podstawie wysokość i szerokość bieżącej czcionki systemowej. **GetDialogBaseUnits** systemu Windows funkcja zwraca bieżącego okna dialogowego podstawowej jednostki w pikselach.) Ten styl nie powinien być używany z **lbs_ownerdrawfixed —**.  
  
-   **Lbs_wantkeyboardinput —** właściciel pola listy otrzymuje `WM_VKEYTOITEM` lub `WM_CHARTOITEM` komunikatów przy każdym naciśnięciu klawisza, gdy pole listy ma wejściowych fokus. Umożliwia to aplikacji podczas przetwarzania specjalne przy użyciu klawiatury.  
  
## <a name="see-also"></a>Zobacz też  
 [Style używane przez MFC](../../mfc/reference/styles-used-by-mfc.md)   
 [CListBox::Create](../../mfc/reference/clistbox-class.md#create)   
 [Style pola listy](http://msdn.microsoft.com/library/windows/desktop/bb775149)

