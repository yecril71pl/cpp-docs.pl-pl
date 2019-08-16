---
title: Wygląd, Kreator kontrolki ATL
ms.date: 08/31/2018
f1_keywords:
- vc.codewiz.class.atl.control.misc
helpviewer_keywords:
- ATL Control Wizard, appearance
ms.assetid: cc16d7ff-74d7-4c15-9ebd-4b19201ff457
ms.openlocfilehash: e07dc017241848f1a670c17b12c2254de6d1b8e1
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492190"
---
# <a name="appearance-atl-control-wizard"></a>Wygląd, Kreator kontrolki ATL

Ta strona kreatora służy do identyfikowania dodatkowych opcji elementów użytkownika dla kontrolki. Ta strona jest dostępna dla kontrolek zidentyfikowanych jako **standardowe kontrolki** w obszarze **Typ formantu** na stronie [Kreatora sterowania ATL](../../atl/reference/options-atl-control-wizard.md) .

## <a name="uielement-list"></a>Lista elementów UI

- **Wyświetl stan**

   Ustawia wygląd formantu w kontenerze.

   - Nieprzezroczysty: Ustawia bit VIEWSTATUS_OPAQUE w wyliczeniu [podwójne](/windows/win32/api/ocidl/ne-ocidl-viewstatus) i rysuje cały prostokąt kontrolki przekazaną do metody [CComControlBase:: OnDraw](../../atl/reference/ccomcontrolbase-class.md#ondraw) . Formant jest wyświetlany całkowicie nieprzezroczysty, a żaden z nich nie jest widoczny w tle.

      To ustawienie ułatwia kontenerowi szybkie narysowanie formantu. Jeśli ta opcja nie jest zaznaczona, formant może zawierać elementy przezroczyste.

      Tylko formant nieprzezroczysty może mieć pełne tło.

   - **Pełne tło**: Ustawia bit VIEWSTATUS_SOLIDBKGND w wyliczeniu podwójne. Tło formantu pojawia się jako pełny kolor bez wzorca.

      Ta opcja jest dostępna tylko wtedy, gdy wybrano również opcję nieprzezroczystość.

- **Dodaj kontrolkę opartą na**

   Ustawia kontrolkę, która ma być oparta na typie kontrolki systemu Windows przez dodanie elementu członkowskiego danych [CContainedWindow](ccontainedwindowt-class.md) do klasy implementującej formant. Dodaje również mapę komunikatów i funkcje obsługi komunikatów do obsługi komunikatów systemu Windows dla kontrolki. Wybierz z listy Typ formantu systemu Windows, który ma zostać utworzony (jeśli istnieje).

   - **Przycisk**

   - **ListBox**

   - **SysAnimate32**

   - **SysListView32**

   - **ComboBox**

   - **RichEdit**

   - **SysDateTimePick32**

   - **SysMonthCal32**

   - **ComboBoxEx32**

   - **ScrollBar**

   - **SysHeader32**

   - **SysTabControl32**

   - **Edytowanie**

   - **Static**

   - **SysIPAddress32**

   - **SysTreeView32**

- **Różne Stany**

   Ustawia dodatkowe opcje wyglądu i zachowania dla kontrolki.

   - **Niewidoczny w czasie wykonywania**: Ustawia, że formant ma być niewidoczny w czasie wykonywania. Możesz użyć niewidocznych formantów do wykonywania operacji w tle, takich jak Wyzwalanie zdarzeń w interwałach czasowych.

   - **Działa jak przycisk**: Ustawia bit OLEMISC_ACTSLIKEBUTTON w wyliczeniu [OLEMISC](/windows/win32/api/oleidl/ne-oleidl-olemisc) , aby umożliwić kontrolce działanie jako przycisk. Jeśli kontener oznaczył lokację kliencką kontrolki jako przycisk domyślny, wybranie tej opcji umożliwia wyświetlenie kontrolki przycisku jako przycisku domyślnego przez rysowanie z grubszą ramką. Aby uzyskać więcej informacji, zobacz [CComControlBase:: GetAmbientDisplayAsDefault](../../atl/reference/ccomcontrolbase-class.md#getambientdisplayasdefault) .

   - **Działa jak etykieta**: Ustawia bit OLEMISC_ACTSLIKELABEL w wyliczeniu OLEMISC, aby umożliwić kontrolce zamienienie etykiety natywnej kontenera. Kontener określa, co zrobić z tą flagą.

- **Inne**

   Ustawia dodatkowe opcje zachowania dla kontrolki.

   - **Znormalizowany kontroler domeny**: Ustawia formant do tworzenia znormalizowanego kontekstu urządzenia, gdy jest wywoływana w celu narysowania siebie. Ta akcja umożliwia standaryzację wyglądu kontrolki, ale sprawia, że rysowanie jest mniej wydajne.

   - **Tylko okno**: Określa, że kontrolka nie może być bez okien. Jeśli ta opcja nie zostanie wybrana, formant zostanie automatycznie wyłączany w kontenerach, które obsługują obiekty bez okien i są automatycznie oknem w kontenerach, które nie obsługują obiektów bez okien. Wybranie tej opcji wymusza przeokienkowanie formantu, nawet w kontenerach, które obsługują obiekty bez okien.

   - Do **wstawienia**: Zaznacz tę opcję, aby formant pojawił się w oknie dialogowym **Wstawianie obiektu** w aplikacjach, takich jak Word i Excel. Formant może następnie zostać wstawiony przez dowolną aplikację, która obsługuje obiekty osadzone za pomocą tego okna dialogowego.

## <a name="see-also"></a>Zobacz także

[Kreator kontrolki ATL](../../atl/reference/atl-control-wizard.md)<br/>
[Przykład SUBEDIT: Superklasa standardową kontrolkę systemu Windows](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/Controls/SubEdit)
