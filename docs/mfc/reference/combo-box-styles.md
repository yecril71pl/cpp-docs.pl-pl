---
title: Style pola kombi | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CBS_LOWERCASE
- CBS_SORT
- CBS_OWNERDRAWVARIABLE
- CBS_OEMCONVERT
- CBS_AUTOHSCROLL
- CBS_NOINTEGRALHEIGHT
- CBS_SIMPLE
- CBS_DROPDOWNLIST
- CBS_DROPDOWN
- CBS_UPPERCASE
- CBS_HASSTRINGS
- CBS_DISABLENOSCROLL
- CBS_OWNERDRAWFIXED
dev_langs:
- C++
helpviewer_keywords:
- CBS_OWNERDRAWVARIABLE constant [MFC]
- CBS_NOINTEGRALHEIGHT constant [MFC]
- CBS_SIMPLE constant [MFC]
- CBS_AUTOHSCROLL constant [MFC]
- CBS_OEMCONVERT constant [MFC]
- CBS_DISABLENOSCROLL constant [MFC]
- CBS_HASSTRINGS constant [MFC]
- CBS_LOWERCASE constant [MFC]
- CBS_SORT constant [MFC]
- CBS_DROPDOWN constant [MFC]
- CBS_OWNERDRAWFIXED constant [MFC]
- combo boxes [MFC], styles
- CBS_UPPERCASE constant [MFC]
- CBS_DROPDOWNLIST constant
ms.assetid: d21a5023-e6a2-495b-a6bd-010a515cbc63
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9ec15f483d9a613e77ad07b6f7f306e84099bced
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="combo-box-styles"></a>Style pola kombi
Następujące style pola kombi są dostępne w MFC.  
  
-   **Cbs_autohscroll —** automatycznie przewija tekst w formancie edycyjnym z prawej strony, gdy użytkownik wpisze znak na końcu linii. Jeśli ten styl nie jest ustawiona, jest dozwolona tylko tekst, który mieści się w granicy prostokątny.  
  
-   **Cbs_disablenoscroll —** pole listy zawiera wyłączenia pionowy pasek przewijania podczas pole listy zawiera za mało elementów przewijanie. Bez tego stylu pasek przewijania jest ukryty, gdy pole listy zawiera za mało elementów.  
  
-   **Cbs_dropdown —** podobny do **cbs_simple —**, ale nie jest wyświetlane okno listy, chyba że użytkownik wybierze ikonę obok kontrolki edycji.  
  
-   **Cbs_dropdownlist —** podobny do **cbs_dropdown —**, z wyjątkiem tego, że kontrolka edycji zastępuje element static — tekst, który wyświetla bieżące zaznaczenie w polu listy.  
  
-   **Cbs_hasstrings —** rysowania przez właściciela pole kombi zawiera elementy składające się z ciągów. Pola kombi zachowuje pamięci i wskaźniki ciągi, tak aby korzystać z aplikacji `GetText` funkcji członkowskiej pobrać tekstu dla danego elementu.  
  
-   **Cbs_lowercase —** konwertowany na małe litery cały tekst w polu Wybór i listy.  
  
-   **Cbs_nointegralheight —** Określa, że rozmiar pola kombi jest rozmiarem ściśle określonym przez aplikację podczas jej tworzenia pola kombi. Zwykle Windows rozmiar pola kombi tak, aby pola kombi nie wyświetla elementów podzielonych na części.  
  
-   **Cbs_oemconvert —** w tekście wprowadzanym w formancie edycyjnym pola kombi jest konwertowana z zestawu znaków ANSI na zbiór znaków OEM i potem z powrotem do strony kodowej ANSI. Dzięki temu konwersji znaków właściwe przy `AnsiToOem` funkcji systemu Windows można przekonwertować ciągu ANSI w polu kombi znaków OEM. Ten styl jest najbardziej przydatna dla pola kombi, które zawierają nazwy plików i ma zastosowanie tylko do pól kombi utworzone za pomocą **cbs_simple —** lub **cbs_dropdown —** style.  
  
-   **Cbs_ownerdrawfixed —** właściciel pola listy jest odpowiedzialny za rysowania zawartością; elementy w polu listy są tego samego wysokość.  
  
-   **Cbs_ownerdrawvariable —** właściciel pola listy jest odpowiedzialny za rysowania zawartością; elementy w polu listy są zmiennej wysokości.  
  
-   **Cbs_simple —** pola listy jest wyświetlany przez cały czas. Bieżące zaznaczenie w polu listy jest wyświetlany w formancie edycyjnym.  
  
-   **Cbs_sort —** automatycznie sortuje ciągi znaków wprowadzona w polu listy.  
  
-   **Cbs_uppercase —** konwertowany na wielkie litery cały tekst w polu Wybór i listy.  
  
## <a name="see-also"></a>Zobacz też  
 [Style używane przez MFC](../../mfc/reference/styles-used-by-mfc.md)   
 [CComboBox::Create] (class.md ccombobox — #ccombobox__create   



