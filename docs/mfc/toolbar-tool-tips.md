---
title: Etykietki narzędzi paska narzędzi | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- tool tips [MFC], activating
- CBRS_TOOLTIPS constant [MFC]
- tool tips [MFC], adding text
- updates [MFC]
- CBRS_FLYBY constant [MFC]
- tool tips [MFC]
- updating status bar messages
- updates, status bar messages
- status bars [MFC], tool tips
- flyby status bar updates
ms.assetid: d1696305-b604-4fad-9f09-638878371412
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 90f325df3825b3546616ce145d4477322a1b4eed
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2018
ms.locfileid: "36956297"
---
# <a name="toolbar-tool-tips"></a>Etykietki narzędzi paska narzędzi
Etykietki narzędzi są okna podręczne niewielki rozmiar, udostępniające krótkie opisy celu przycisku paska narzędzi, gdy umieszczenie wskaźnika myszy nad przyciskiem w danym okresie czasu. Po utworzeniu aplikacji przy użyciu Kreatora aplikacji, który ma paska narzędzi Narzędzia Porada jest obsługiwane dla Ciebie. W tym artykule opisano zarówno narzędzia Porada obsługi utworzone przez Kreatora aplikacji oraz sposób dodawania obsługi Porada narzędzia do aplikacji.  
  
 W tym artykule omówiono:  
  
-   [Aktywowanie etykietki narzędzi](#_core_activating_tool_tips)  
  
-   [Aktualizacje paska stanu flyby —](#_core_fly_by_status_bar_updates)  
  
##  <a name="_core_activating_tool_tips"></a> Aktywowanie etykietki narzędzi  
 Aby aktywować etykietki narzędzi w aplikacji, należy wykonać dwie czynności:  
  
-   Dodać cbrs_tooltips — do innych stylów (takie jak ws_child — ws_visible — i innych **CBRS_** style) przekazany jako *dwStyle* parametr [CToolBar::Create](../mfc/reference/ctoolbar-class.md#create) Funkcja lub [SetBarStyle](../mfc/reference/ccontrolbar-class.md#setbarstyle).  
  
-   Zgodnie z opisem w poniższej procedurze, Dołącz tekst porady narzędzi, oddzielone znakiem nowego wiersza ("\n"), do zasobu ciągu zawierającego wiersza polecenia wiersza polecenia narzędzi. Zasób ciągu udostępnia identyfikator przycisku paska narzędzi.  
  
#### <a name="to-add-the-tool-tip-text"></a>Aby dodać tekst wskazówki  
  
1.  Podczas edytowania paska narzędzi w edytorze paska narzędzi, otwórz **właściwości przycisku paska narzędzi** okna dla danego przycisku.  
  
2.  W **monitu** Określ tekst, który ma być wyświetlany w etykietce narzędzia dla przycisku.  
  
> [!NOTE]
>  Ustawienie tekstu zgodnie z właściwością przycisku w edytorze paska narzędzi zastępuje wcześniejsze procedury, w którym można było otworzyć i edytować zasobu ciągu.  
  
 Jeśli pasek sterowania z podpowiedzi włączone ma dla niej formantów podrzędnych, pasek sterowania do wyświetlenia etykietki narzędzia dla każdego formantu podrzędnego na pasek sterowania pod warunkiem, że spełnia on następujące kryteria:  
  
-   Identyfikator formantu jest nie - 1.  
  
-   Wpis tabeli ciągów o tym samym identyfikatorze jako formantu podrzędnego w pliku zasobów ma ciągu etykietki narzędzia.  
  
##  <a name="_core_fly_by_status_bar_updates"></a> Pasek stanu flyby — aktualizacje  
 Funkcja związane z etykietki narzędzi jest pasek aktualizowania stanu "flyby —". Domyślnie komunikat na pasku stanu opisuje tylko przycisku paska narzędzi w szczególności, gdy przycisk jest aktywny. Umieszczając cbrs_flyby — na liście style przekazany do `CToolBar::Create`, może mieć te komunikaty aktualizowane, gdy wskaźnik myszy przesuwa się nad narzędzi bez uaktywniania faktycznie przycisku.  
  
### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o  
  
-   [MFC — implementacja paska narzędzi (omówienie na paskach narzędzi)](../mfc/mfc-toolbar-implementation.md)  
  
-   [Zadokowane i przestawne paski narzędzi](../mfc/docking-and-floating-toolbars.md)  
  
-   [Ctoolbar —](../mfc/reference/ctoolbar-class.md) i [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) klas  
  
-   [Praca z formantem paska narzędzi](../mfc/working-with-the-toolbar-control.md)  
  
-   [Używanie swoich starych pasków narzędzi](../mfc/using-your-old-toolbars.md)  
  
## <a name="see-also"></a>Zobacz też  
 [MFC, implementacja paska narzędzi](../mfc/mfc-toolbar-implementation.md)

