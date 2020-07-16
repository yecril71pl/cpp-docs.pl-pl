---
title: Ustawienia kontrolki, kreator kontrolek ActiveX MFC
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfc.ctl.settings
helpviewer_keywords:
- MFC ActiveX Control Wizard, control settings
ms.assetid: 2ccaa4fc-0d52-413e-afa3-ecd474c3f6f0
ms.openlocfilehash: 1578ca7f4134e51e0ba0d3c2b247dcafcb0fbd67
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/15/2020
ms.locfileid: "86405016"
---
# <a name="control-settings-mfc-activex-control-wizard"></a>Ustawienia kontrolki, kreator kontrolek ActiveX MFC

Użyj tej strony kreatora, aby określić, jak ma działać formant. Na przykład można oprzeć formant na standardowych typach formantów systemu Windows, zoptymalizować jego zachowanie i wygląd lub wskazać, że kontrolka może pełnić rolę kontenera dla innych formantów.

Aby uzyskać więcej informacji na temat wybierania opcji na tej stronie w celu zmaksymalizowania wydajności formantu, zobacz [kontrolki ActiveX MFC: Optymalizacja](../../mfc/mfc-activex-controls-optimization.md).

## <a name="uielement-list"></a>Lista elementów UI

- **Utwórz kontrolkę opartą na**

   Na tej liście można wybrać rodzaj kontrolki, z której formant powinien dziedziczyć. Lista jest podzbiorem klas formantów, które są dostępne dla `CreateWindowEx` i dodatkowych wspólnych formantów, które są określone w CommCtrl. h. Wybór określa styl kontrolki w `PreCreateWindow` funkcji w pliku *projy*Ctrl. cpp. Aby uzyskać więcej informacji, zobacz kontrolki [ActiveX MFC: podklasy kontrolki systemu Windows](../../mfc/mfc-activex-controls-subclassing-a-windows-control.md).

   |Kontrola|Opis|
   |-------------|-----------------|
   |**PRZYCISK**|Kontrolka przycisku systemu Windows|
   |**SKŁADNIK**|Kontrolka pola kombi systemu Windows|
   |**EDYTOWANIA**|Kontrolka pola edycji systemu Windows|
   |**LISTBOX**|Kontrolka pola listy systemu Windows|
   |**PASKI**|Kontrolka paska przewijania systemu Windows|
   |**RUCHOM**|Formant statyczny systemu Windows|
   |**msctls_hotkey32**|Wspólna kontrola klawisza skrótu|
   |**msctls_progress32**|Wspólna kontrolka paska postępu|
   |**msctls_statusbar32**|Wspólna kontrola paska stanu|
   |**msctls_trackbar32**|Kontrolka wspólna paska śledzenia|
   |**msctls_updown32**|Wspólna Kontrolka przycisku pokrętła (lub w górę)|
   |**SysAnimate32**|Wspólna kontrolka animacji|
   |**SysHeader32**|Wspólna kontrola nagłówka|
   |**SysListView32**|Kontrolka widoku listy|
   |**SysTabControl32**|Typowa kontrolka tabulacji|
   |**SysTreeView32**|Formant wspólny widoku drzewa|

- **Uaktywnia, gdy jest widoczny**

   Określa, że okno jest tworzone dla formantu, gdy jest dostępny. Domyślnie zaznaczona jest opcja **Aktywuj, gdy jest widoczna** . Jeśli chcesz odroczyć aktywację kontroli do momentu jej wykonania przez kontener (na przykład gdy użytkownik kliknie mysz), usuń zaznaczenie tej opcji. Gdy ta funkcja jest wyłączona, nie będzie ponosić kosztów tworzenia okna, dopóki nie jest to wymagane. Aby uzyskać więcej informacji, zobacz Wyłączanie [opcji Aktywuj, gdy jest widoczny](../../mfc/turning-off-the-activate-when-visible-option.md).

- **Niewidoczne w czasie wykonywania**

   Określa, że kontrolka nie ma interfejsu użytkownika w czasie wykonywania. Czasomierz jest rodzajem formantu, który może być niewidoczny.

- **Ma okno dialogowe informacje**

   Określa, że Kontrolka zawiera standardowe okno **dialogowe system** Windows, w którym jest wyświetlany numer wersji i informacje o prawach autorskich.

   > [!NOTE]
   > Sposób, w jaki użytkownik uzyskuje dostęp do pomocy dla formantu, zależy od tego, w jaki sposób została zaimplementowana pomoc, oraz od tego, czy została zintegrowana pomoc dotycząca tego kontenera.

   Po wybraniu tej opcji wstawia ona `AboutBox` metodę kontrolki w klasie formantów projektu (C*Projname*Ctrl. cpp) i dodaje AboutBox do mapy wysyłania projektu. Ta opcja jest wybrana domyślnie.

- **Zoptymalizowany kod rysowania**

   Określa, że kontener automatycznie przywraca oryginalne obiekty GDI po narysowaniu wszystkich kontrolek kontenera, które są rysowane w tym samym kontekście urządzenia. Aby uzyskać więcej informacji na temat tej funkcji, zobacz [Optymalizacja rysowania formantów](../../mfc/optimizing-control-drawing.md).

- **Aktywacja bez okien**

   Określa, że formant nie tworzy okna, gdy jest aktywowany. Aktywacja bez okien pozwala na kontrolki nieprostokątne lub przezroczyste, a kontrolka bez okien wymaga mniejszego obciążenia systemu niż kontrolka, która wymaga okna. Kontrolka bez okien nie zezwala na przycięty kontekst urządzenia lub aktywację bez migotania. Kontenery utworzone przed 1996 nie obsługują aktywacji bez okien. Aby uzyskać więcej informacji na temat korzystania z tej opcji, zobacz [zapewnianie aktywacji bez okien](../../mfc/providing-windowless-activation.md).

- **Kontekst urządzenia nieprzycinanego**

   Przesłania [COleControl:: GetControlFlags](../../mfc/reference/colecontrol-class.md#getcontrolflags) w nagłówku kontrolki (*Projname*Ctrl. h), aby wyłączyć wywołanie `IntersectClipRect` wykonane przez `COleControl` . Po wybraniu tej opcji zapewnia ona małą korzyść. W przypadku wybrania opcji **Aktywacja bez okien**ta funkcja jest niedostępna. Aby uzyskać więcej informacji, zobacz [Używanie nieprzycinanego kontekstu urządzenia](../../mfc/using-an-unclipped-device-context.md).

- **Aktywacja bez migotania**

   Eliminuje operacje rysowania i towarzyszące Migotanie wizualne występujące między aktywnym i nieaktywnym stanem formantu. W przypadku wybrania opcji **Aktywacja bez okien**ta funkcja jest niedostępna. Po ustawieniu tej opcji `noFlickerActivate` flaga jest jedną z flag, które są zwracane przez [COleControl:: GetControlFlags](../../mfc/reference/colecontrol-class.md#getcontrolflags). Aby uzyskać więcej informacji, zobacz [zapewnianie aktywacji bez migotania](../../mfc/providing-flicker-free-activation.md).

- **Dostępne w oknie dialogowym Wstaw obiekt**

   Określa, że formant będzie dostępny w oknie dialogowym **Wstaw obiekt** dla włączonych kontenerów. Po wybraniu tej opcji `afxRegInsertable` flaga jest jedną z flag, które są zwracane przez `AfxOleRegisterControlClass` . Za pomocą okna dialogowego **Wstawianie obiektu** użytkownik może wstawić nowo utworzone lub istniejące obiekty do dokumentu złożonego.

- **Powiadomienia wskaźnika myszy, gdy nieaktywny**

   Umożliwia formantowi przetwarzanie powiadomień dotyczących wskaźnika myszy, niezależnie od tego, czy formant jest aktywny, czy nie. Po wybraniu tej opcji `pointerInactive` flaga jest jedną z flag, które są zwracane przez [COleControl:: GetControlFlags](../../mfc/reference/colecontrol-class.md#getcontrolflags). Aby uzyskać więcej informacji na temat korzystania z tej opcji, zobacz [zapewnianie interakcji z myszą, gdy jest nieaktywna](../../mfc/providing-mouse-interaction-while-inactive.md).

- **Działa jako prosta kontrolka ramki**

   Określa, że formant jest kontenerem dla innych kontrolek, ustawiając OLEMISC_SIMPLEFRAME bit dla kontrolki. Aby uzyskać więcej informacji, zobacz [prosta lokacja klatek zawiera](/windows/win32/com/simple-frame-site-containment).

- **Ładuje właściwości asynchronicznie**

   Włącza resetowanie wszelkich poprzednich danych asynchronicznych i Inicjuje nowe obciążenie właściwości asynchronicznej kontrolki.

## <a name="see-also"></a>Zobacz też

[Kreator kontrolek ActiveX MFC](../../mfc/reference/mfc-activex-control-wizard.md)<br/>
[Ustawienia aplikacji, kreator kontrolek ActiveX MFC](../../mfc/reference/application-settings-mfc-activex-control-wizard.md)<br/>
[Nazwy kontrolek, kreator kontrolek ActiveX MFC](../../mfc/reference/control-names-mfc-activex-control-wizard.md)
