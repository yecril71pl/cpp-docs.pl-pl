---
title: "Wygląd, Kreator formantu ATL | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.control.misc
dev_langs:
- C++
helpviewer_keywords:
- ATL Control Wizard, appearance
ms.assetid: cc16d7ff-74d7-4c15-9ebd-4b19201ff457
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8869df577dfbc541b989beb4b4f3117d7d12feea
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="appearance-atl-control-wizard"></a>Wygląd, Kreator formantu ATL
Tutaj należy wstawić "Wyszukiwanie" podsumowania.  
  
 Ta strona kreatora do identyfikowania użytkownika dodatkowe opcje elementu dla formantu. Ta strona jest dostępna dla formantów zidentyfikowane jako **standardowych formantów** w obszarze **kontroli typem** na [opcji, Kreator formantu ATL](../../atl/reference/options-atl-control-wizard.md) strony.  
  
## <a name="uielement-list"></a>Lista elementów UI  
 **Wyświetl stan**  
 Określa wygląd formantu kontenera.  
  
-   **Nieprzezroczysta**: zestawy `VIEWSTATUS_OPAQUE` bitu w [podwójne](http://msdn.microsoft.com/library/windows/desktop/ms687201) wyliczenie i rysuje prostokąt kontroli cały przekazany do [CComControlBase::OnDraw](../../atl/reference/ccomcontrolbase-class.md#ondraw) — metoda. Ten formant jest widoczny całkowicie nieprzezroczyste, a żaden z kontenera pokazuje poza granice formantu.  
  
     To ustawienie pomaga w kontenerze narysować kontrolkę szybciej. Jeśli ta opcja nie jest zaznaczona, formant może zawierać części przezroczysty.  
  
     Tylko nieprzezroczystości formantu może mieć jednolite tło.  
  
-   Ustawia `VIEWSTATUS_SOLIDBKGND` bitu w `VIEWSTATUS` wyliczenia. Pełny kolor z wzorcem nie zostanie wyświetlony tła formantu.  
  
     Ta opcja jest dostępna tylko wtedy, gdy **nieprzezroczyste** wybrano również opcji.  
  
 **Dodaj formant w oparciu**  
 Formant ma być oparta na typu kontrolki systemu Windows, dodając [CContainedWindow](ccontainedwindowt-class.md) element członkowski danych klasy Implementowanie formantu. Dodaje również mapy komunikatów i funkcji programu obsługi wiadomości do obsługi komunikatów systemu Windows dla formantu. Wybierz z listy Typ formantu systemu Windows, który chcesz utworzyć, jeśli istnieje.  

  
-   `Button`  
  
-   `ListBox`  
  
-   `SysAnimate32`  
  
-   `SysListView32`  
  
-   `ComboBox`  
  
-   `RichEdit`  
  
-   `SysDateTimePick32`  
  
-   `SysMonthCal32`  
  
-   `ComboBoxEx32`  
  
-   `ScrollBar`  
  
-   `SysHeader32`  
  
-   `SysTabControl32`  
  
-   `Edit`  
  
-   `Static`  
  
-   `SysIPAddress32`  
  
-   `SysTreeView32`  
  
 **Stan obiektu**  
 Określa dodatkowe opcje wygląd i zachowanie dla formantu.  
  
-   **Niewidoczne w czasie wykonywania**: formant ma być niewidoczna w czasie wykonywania. Niewidoczne formantów służy do wykonywania operacji w tle, takie jak wyzwalania zdarzenia w określonych interwałach.  
  
-   **Zachowuje się jak przycisk**: zestawy `OLEMISC_ACTSLIKEBUTTON` bitu w [OLEMISC](http://msdn.microsoft.com/library/windows/desktop/ms678497) wyliczeniu, aby włączyć kontrolę do działania, takich jak przycisk. Po zaznaczeniu formantu lokacji klienta jako przycisk domyślny kontener wybranie tej opcji umożliwia formantu przycisku do wyświetlenia się jako przycisk domyślny za pomocą rysowania sam grubszy ramki. Zobacz [CComControlBase::GetAmbientDisplayAsDefault](../../atl/reference/ccomcontrolbase-class.md#getambientdisplayasdefault) Aby uzyskać więcej informacji.  
  
-   **Zachowuje się jak etykiety**: zestawy `OLEMISC_ACTSLIKELABEL` bitu w `OLEMISC` wyliczeniu, aby włączyć kontrolę zamiast natywnego etykiety kontenera. Kontener określa czynności do wykonania tej flagi, jeśli wszystko.  
  
 **Inne**  
 Ustawia opcje dodatkowe zachowanie dla formantu.  
  
-   **Znormalizowany DC**: ustawia formant Utwórz znormalizowany kontekst urządzenia, gdy jest wywoływana do rysowania sam. Ta akcja standaryzuje wygląd formantu, ale powoduje Rysowanie w mniej wydajne.  
  
-   **Tylko okno**: Określa, czy formant nie może być bez okien. Jeśli nie zaznaczysz tej opcji, formantu jest automatycznie bez okien w kontenerach obsługujących obiektów bez okien i jest automatycznie okna w kontenerach, które nie obsługuje obiektów bez okien. Ta opcja wymusza formantu za okna, nawet w kontenerach obsługujących obiektów bez okien.  
  
-   **Insertable**: Wybierz tę opcję, aby mieć formantu są wyświetlane w **Wstaw obiekt** okna dialogowego aplikacji, takich jak Word i Excel. Następnie można wstawiać formantu przez dowolną aplikację, która obsługuje osadzonych obiektów za pomocą tego okna dialogowego.  
  
## <a name="see-also"></a>Zobacz też  
 [Kreator formantu ATL](../../atl/reference/atl-control-wizard.md)   
 [SUBEDIT próbki: Nadklas formantu standardowego systemu Windows](http://msdn.microsoft.com/en-us/30e46bdc-ed92-417c-b6b8-359017265a7b)

