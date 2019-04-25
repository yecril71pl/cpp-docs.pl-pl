---
title: Wygląd, Kreator kontrolki ATL
ms.date: 08/31/2018
f1_keywords:
- vc.codewiz.class.atl.control.misc
helpviewer_keywords:
- ATL Control Wizard, appearance
ms.assetid: cc16d7ff-74d7-4c15-9ebd-4b19201ff457
ms.openlocfilehash: 4d3b0519951636fad4175dc35261ba35b3694ffa
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62248956"
---
# <a name="appearance-atl-control-wizard"></a>Wygląd, Kreator kontrolki ATL

Ta strona kreatora umożliwia zidentyfikowanie dodatkowego użytkownika elementu Opcje dla formantu. Ta strona jest dostępna dla kontrolki zidentyfikowane jako **standardowych kontrolek** w obszarze **kontrolowanie typu** na [opcji, Kreator kontrolki ATL](../../atl/reference/options-atl-control-wizard.md) strony.

## <a name="uielement-list"></a>Lista elementów UI

- **Wyświetl stan**

   Ustawia wyglądu formantu w kontenerze.

   - **Nieprzezroczysty**: Ustawia VIEWSTATUS_OPAQUE bit w [stan](/windows/desktop/api/ocidl/ne-ocidl-tagviewstatus) wyliczenie i rysuje prostokąt całego kontroli przekazany do [CComControlBase::OnDraw](../../atl/reference/ccomcontrolbase-class.md#ondraw) metody. Ten formant jest widoczny całkowicie nieprzezroczysty, a żaden z kontenera pokazuje poza granice formantu.

      To ustawienie pozwala kontenera narysuj kontrolkę szybciej. Jeśli ta opcja nie jest zaznaczone, formant może zawierać części przezroczysty.

      Tylko kontrolkę nieprzezroczyste może mieć jednolite tło.

   - **Pełne tło**: Ustawia VIEWSTATUS_SOLIDBKGND bit w wyliczeniu stan. Tła formantu pojawia się jako jednolitego koloru nie wzorca.

      Ta opcja jest dostępna tylko wtedy, gdy **nieprzezroczyste** jest również opcja.

- **Dodaj kontrolkę na podstawie**

   Formant opierać się na typ kontrolki Windows, dodając [CContainedWindow](ccontainedwindowt-class.md) element członkowski danych do klasy Implementowanie formantu. Dodaje także mapy komunikatów i funkcji obsługi komunikatów do obsługi komunikatów Windows dla formantu. Wybierz z listy Typ kontrolki Windows, który chcesz utworzyć, jeśli istnieje.

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

- **Stan różne**

   Określa dodatkowe opcje wygląd i zachowanie dla formantu.

   - **Niewidoczne w czasie wykonywania**: Ustawienie kontroli ma być niewidoczna w czasie wykonywania. Niewidoczne formantów służy do wykonywania operacji w tle, takie jak wyzwalanie zdarzeń w określonych interwałach.

   - **Zachowuje się jak przycisk**: Ustawia OLEMISC_ACTSLIKEBUTTON bit w [OLEMISC](/windows/desktop/api/oleidl/ne-oleidl-tagolemisc) wyliczeniu, aby włączyć kontrolę do działania, takie jak przycisk. Jeśli kontener został oznaczony formantu lokacji klienta jako przycisk domyślny, wybranie tej opcji umożliwia kontrolki przycisku do wyświetlenia sama jako przycisk domyślny za pomocą rysowania sam grubszy ramki. Zobacz [CComControlBase::GetAmbientDisplayAsDefault](../../atl/reference/ccomcontrolbase-class.md#getambientdisplayasdefault) Aby uzyskać więcej informacji.

   - **Zachowuje się jak etykiety**: Ustawia OLEMISC_ACTSLIKELABEL bit w wyliczeniu OLEMISC, aby włączyć kontrolę zamiast kontenera natywne etykiety. Kontener Określa, co należy zrobić z tą flagą Jeśli niczego.

- **Inne**

   Ustawia zachowanie dodatkowe opcje dla formantu.

   - **Znormalizowane DC**: Ustawienie dla formantu do utworzenia znormalizowany kontekst urządzenia, gdy jest wywoływana, aby narysować sam. Ta akcja standaryzuje wygląd formantu, ale to sprawia, że rysowania mniej wydajne rozwiązanie.

   - **Tylko okna**: Określa, że formant nie może być bez okien. Jeśli nie zaznaczysz tej opcji, formant jest automatycznie bez okien w kontenerach, które obsługują obiekty niepowiązanej z oknami, i jest automatycznie okna w kontenerach, które nie obsługują obiektów bez okien. Wybranie tej opcji wymusza kontroli nad się okna, nawet w przypadku kontenerów, które obsługują obiekty bez okien.

   - **Wstawianie**: Wybierz tę opcję, aby mieć formantu są wyświetlane w **Wstawianie obiektu** okna dialogowego aplikacji, takich jak Word i Excel. Następnie można wstawiać formantu przez dowolną aplikację, który obsługuje obiekty osadzone, za pomocą tego okna dialogowego.

## <a name="see-also"></a>Zobacz także

[Kreator kontrolki ATL](../../atl/reference/atl-control-wizard.md)<br/>
[SUBEDIT próbki: Superklas kontrolki Windows Standard](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/Controls/SubEdit)
