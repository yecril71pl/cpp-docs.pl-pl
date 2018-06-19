---
title: Paski sterowania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- command bars [MFC], types of
- toolbars [MFC], control bars
- control bars [MFC]
- MFC, control bars
- control bars [MFC], types of
- CDialogBar class [MFC], control bars
- status bars [MFC], control bars
- CControlBar class [MFC], MFC control bars
- dialog bars [MFC], control bars
- CToolBar class [MFC], control bars
- CStatusBar class [MFC], control bars
ms.assetid: 31831910-3d23-4d70-9e71-03cc02f01ec4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bd25089594d31de21a3a315d997ee01111aff4fd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33347902"
---
# <a name="control-bars"></a>Paski sterowania
"Pasek sterowania" jest nazwą ogólne paski narzędzi, paski stanu i paski dialogowe. Klasy MFC `CToolBar`, `CStatusBar`, `CDialogBar`, `COleResizeBar`, i **crebar —** pochodzi z klasy [ccontrolbar —](../mfc/reference/ccontrolbar-class.md), który implementuje ich typowe funkcje.  
  
 Paski sterowania są windows wyświetlanych wierszy formantów, z których użytkownicy można wybrać opcje, wykonywać polecenia lub uzyskać informacje o programie. Paski sterowania należą paski narzędzi, paski dialogowe i paski stanu.  
  
-   Paski narzędzi w klasie [ctoolbar —](../mfc/reference/ctoolbar-class.md)  
  
-   Paski stanu w klasie [cstatusbar —](../mfc/reference/cstatusbar-class.md)  
  
-   Paski dialogowe w klasie [cdialogbar —](../mfc/reference/cdialogbar-class.md)  
  
-   Pręty zbrojeniowe w klasie [crebar —](../mfc/reference/crebar-class.md)  
  
> [!IMPORTANT]
>  Począwszy od wersji 4.0 MFC pasków narzędzi, pasków stanu i etykietki narzędzi są implementowane za pomocą funkcji systemu zaimplementowana w comctl32.dll zamiast poprzedniej implementacji MFC. W MFC w wersji 6.0 **crebar —**, comctl32.dll funkcję, która opakowuje również został dodany.  
  
 Wykonaj krótkie instrukcje do typów pasek sterowania. Aby uzyskać więcej informacji zobacz poniższe łącza.  
  
## <a name="control-bars"></a>Paski sterowania  
 Paski sterowania znacznie zwiększają użyteczność programu zapewniając szybkie, jednoetapowy akcje polecenia. Klasa `CControlBar` zawiera typowe funkcje pasków narzędzi, pasków stanu i paski dialogowe. `CControlBar` udostępnia funkcje dotyczące pozycjonowania pasek sterowania w jego ramkę okna nadrzędnego. Ponieważ pasek sterowania jest zazwyczaj okna podrzędnego ramki okna nadrzędnego, jest "równorzędnego" do klienta widoku lub funkcji okno ramowe klienta MDI. Obiekt pasek sterowania używa informacji o jej okna nadrzędnego prostokąt klienta do samej pozycji. A następnie zmienia nadrzędnego pozostałych prostokąt okna klienta, tak aby widok klienta lub okno klienckie MDI wypełnia pozostałe okna klienta.  
  
> [!NOTE]
>  Jeśli nie ma przycisku na pasek sterowania **polecenia** lub **UPDATE_COMMAND_UI** obsługi, w ramach automatycznie wyłącza przycisk.  
  
## <a name="toolbars"></a>Paski narzędzi  
 Pasek narzędzi jest pasek sterowania z wiersza poleceń mapy bitowej przycisków. Naciśnięcie przycisku paska narzędzi jest równoważne wybraniu elementu menu; wywołuje program obsługi tego samego zamapowane na element menu, jeśli element menu ma taki sam identyfikator jak przycisku paska narzędzi. Przyciski można skonfigurować i zachowywać się jak przyciski przycisków radiowych i pól wyboru. Pasek narzędzi zwykle jest wyrównywany do początku okno ramowe, ale narzędzi MFC "dokowany" do strony jej okna nadrzędnego lub float w osobnym oknie mini ramki. Pasek narzędzi można również "float" i można zmienić jego rozmiar i przeciągnij go za pomocą myszy. Pasek narzędzi można również wyświetlić etykietki narzędzi, jako użytkownik przesuwa wskaźnik myszy nad przycisków paska narzędzi. Etykietka narzędzia, która jest okna podręcznego niewielki rozmiar, krótki opis przeznaczenia przycisku.  
  
> [!NOTE]
>  Począwszy od wersji 4.0 MFC, klasa [ctoolbar —](../mfc/reference/ctoolbar-class.md) używa kontrolki typowych narzędzi systemu Windows. A `CToolBar` zawiera [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md). Paski narzędzi starsze nadal są obsługiwane, ale. Zapoznaj się z artykułem [paski narzędzi](../mfc/mfc-toolbar-implementation.md).  
  
## <a name="status-bars"></a>Paski stanu  
 Pasek stanu jest pasek sterowania zawierający tekst wyjściowy okienka lub "wskaźników." Okienka dane wyjściowe są często używane jako wiersze komunikat, a wskaźniki stanu. Komunikat wiersza Przykładami wierszy komunikat pomocy polecenia krótko opisano wybranego menu lub poleceń paska narzędzi w okienku po lewej stronie paska stanu domyślnego tworzone przez Kreatora aplikacji MFC. Stan wskaźnika przykładami blokady PRZEWIJANIA, NUM LOCK i kluczy. Paski stanu zwykle są wyrównane do dolnej części okna ramki. Zawiera opis klasy [cstatusbar —](../mfc/reference/cstatusbar-class.md) i klasa [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md).  
  
## <a name="dialog-bars"></a>Paski dialogowe  
 Paska dialogowego jest pasek sterowania, na podstawie w zasobie szablonu okna dialogowego z funkcjami niemodalne okno dialogowe. Paski dialogowe może zawierać systemu Windows, niestandardowych lub formantów ActiveX. W oknie dialogowym użytkownik tab między formantami. Paski dialogowe może być wyrównany do górny, dolny, po lewej lub prawej stronie okno ramowe i mogą być również przestawione w ich własnych ramkę okna. Zawiera opis klasy [cdialogbar —](../mfc/reference/cdialogbar-class.md).  
  
## <a name="rebars"></a>Pręty zbrojeniowe  
 A [paska pomocniczego](../mfc/using-crebarctrl.md) jest pasek sterowania, który zawiera informacje o formantach paska pomocniczego dokowanie, układ, stanu i trwałości. Obiekt paska pomocniczego może zawierać wiele podrzędnych systemu Windows, zazwyczaj inne formanty, w tym pola edycji, paski narzędzi i pola listy. Obiekt paska pomocniczego można wyświetlić jego okno podrzędne za pośrednictwem Podana mapa bitowa. Go można automatycznie lub ręcznie zmienić rozmiar przez kliknięcie lub przeciągnięcie paska uchwytu. Zawiera opis klasy [crebar —](../mfc/reference/crebar-class.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Elementy interfejsu użytkownika](../mfc/user-interface-elements-mfc.md)
