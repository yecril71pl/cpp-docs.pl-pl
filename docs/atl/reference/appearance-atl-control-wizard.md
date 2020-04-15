---
title: Wygląd, Kreator sterowania ATL
ms.date: 08/31/2018
f1_keywords:
- vc.codewiz.class.atl.control.misc
helpviewer_keywords:
- ATL Control Wizard, appearance
ms.assetid: cc16d7ff-74d7-4c15-9ebd-4b19201ff457
ms.openlocfilehash: 3484fb5d0f919af0dfd18b584e96d4675e2baea8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319396"
---
# <a name="appearance-atl-control-wizard"></a>Wygląd, Kreator sterowania ATL

Ta strona kreatora służy do identyfikowania dodatkowych opcji elementu użytkownika formantu. Ta strona jest dostępna dla formantów zidentyfikowanych jako **formanty standardowe** w obszarze **Typ sterowania** na stronie Kreator [sterowania ATL.](../../atl/reference/options-atl-control-wizard.md)

## <a name="uielement-list"></a>Lista elementów UI

- **Stan widoku**

   Ustawia wygląd formantu w kontenerze.

  - **Nieprzezroczyste**: Ustawia bit VIEWSTATUS_OPAQUE w wyliczeniu [VIEWSTATUS](/windows/win32/api/ocidl/ne-ocidl-viewstatus) i rysuje cały prostokąt formantu przekazany do [CComControlBase::OnDraw](../../atl/reference/ccomcontrolbase-class.md#ondraw) metody. Formant wydaje się całkowicie nieprzezroczyste i żaden z kontenerów pokazuje za granicami formantu.

      To ustawienie pomaga kontenerowi szybciej rysować formant. Jeśli ta opcja nie jest zaznaczona, formant może zawierać części przezroczyste.

      Tylko nieprzezroczyste sterowanie może mieć stałe tło.

  - **Tło bryłowe**: Ustawia bit VIEWSTATUS_SOLIDBKGND w wyliczeniu VIEWSTATUS. Tło formantu jest wyświetlany jako jednolity kolor bez szyku.

      Ta opcja jest dostępna tylko wtedy, gdy wybrano również opcję **Nieprzezroczystą.**

- **Dodawanie formantu na podstawie**

   Ustawia formant, który ma być oparty na typie formantu systemu Windows, dodając element członkowski danych [CContainedWindow](ccontainedwindowt-class.md) do klasy implementującej formant. Dodaje również mapę wiadomości i funkcje obsługi wiadomości do obsługi wiadomości systemu Windows dla formantu. Wybierz z listy typ formantu systemu Windows, który chcesz utworzyć, jeśli istnieje.

  - **Przycisk**

  - **ListBox**

  - **SysAnimate32 (WysAnimate32)**

  - **Widok SysListView32**

  - **ComboBox**

  - **Richedit**

  - **SysDateTimePick32**

  - **Miesiąc SysCal32**

  - **ComboBoxEx32**

  - **ScrollBar**

  - **SysHeader32 (Właz głowy)**

  - **SysTabControl32**

  - **Edytuj**

  - **Statyczne**

  - **SysIPAddress32**

  - **Widok SysTreeView32**

- **Stan różnej**

   Ustawia dodatkowe opcje wyglądu i zachowania dla formantu.

  - **Niewidoczny w czasie wykonywania:** Ustawia formant jako niewidoczny w czasie wykonywania. Niewidoczne formanty służy do wykonywania operacji w tle, takich jak wypalania zdarzeń w odstępach czasu.

  - **Działa jak przycisk:** Ustawia bit OLEMISC_ACTSLIKEBUTTON w wyliczeniu [OLEMISC,](/windows/win32/api/oleidl/ne-oleidl-olemisc) aby umożliwić formant działać jak przycisk. Jeśli kontener oznaczył lokację klienta formantu jako przycisk domyślny, wybranie tej opcji umożliwia kontrolkę przycisku wyświetlanie się jako przycisk domyślny, rysując się za pomocą grubszej ramki. Zobacz [CComControlBase::GetAmbientDisplayAsDefault aby](../../atl/reference/ccomcontrolbase-class.md#getambientdisplayasdefault) uzyskać więcej informacji.

  - **Działa jak etykieta:** Ustawia bit OLEMISC_ACTSLIKELABEL w wyliczeniu OLEMISC, aby włączyć formant, aby zastąpić etykietę macierzystą kontenera. Kontener określa, co zrobić z tej flagi, jeśli w ogóle.

- **Inne**

   Ustawia dodatkowe opcje zachowania dla formantu.

  - **Znormalizowany kontroler domeny:** Ustawia formant, aby utworzyć znormalizowany kontekst urządzenia, gdy jest wywoływana do rysowania się. Ta akcja standaryzuje wygląd formantu, ale sprawia, że rysowanie jest mniej wydajne.

  - **Tylko okno:** Określa, że formant nie może być bez okien. Jeśli ta opcja nie zostanie zaznaczona, formant jest automatycznie bez okien w kontenerach, które obsługują obiekty bez okien i jest automatycznie okna w kontenerach, które nie obsługują obiektów bez okien. Wybranie tej opcji wymusza formant do okna, nawet w kontenerach, które obsługują obiekty bez okien.

  - **Możliwość wstawiania:** Wybierz tę opcję, aby formant był wyświetlany w oknie dialogowym **Wstawianie obiektu** aplikacji takich jak Word i Excel. Formant może być następnie wstawiany przez dowolną aplikację, która obsługuje obiekty osadzone za pośrednictwem tego okna dialogowego.

## <a name="see-also"></a>Zobacz też

[Kreator kontrolki ATL](../../atl/reference/atl-control-wizard.md)<br/>
[Przykład SUBEDIT: Superclasses standard windows control](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/Controls/SubEdit)
