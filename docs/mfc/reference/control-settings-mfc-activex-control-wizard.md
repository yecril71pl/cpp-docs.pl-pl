---
title: Ustawienia kontrolki, Kreator kontrolek ActiveX MFC | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.appwiz.mfc.ctl.settings
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX Control Wizard, control settings
ms.assetid: 2ccaa4fc-0d52-413e-afa3-ecd474c3f6f0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: db62ce0770199b3a928e3f01c04b7f0600ad2dcd
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/05/2018
ms.locfileid: "37853718"
---
# <a name="control-settings-mfc-activex-control-wizard"></a>Ustawienia kontrolki, kreator kontrolek ActiveX MFC
Aby określić, jak kontrolka zachowuje się, należy użyć tej strony kreatora. Można na przykład podstawowa kontrolki w standardowych typów formantów Windows, optymalizowanie jego zachowania i wyglądu lub wskazują, że formant może działać jako kontener dla innych kontrolek.  
  
 Aby uzyskać więcej informacji o tym, jak wybrać opcje na tej stronie, aby zmaksymalizować wydajność formantu, zobacz [kontrolki ActiveX MFC: Optymalizacja](../../mfc/mfc-activex-controls-optimization.md).  
  
## <a name="uielement-list"></a>Lista elementów UI  
 **Tworzenie kontrolki na podstawie**  
 Na tej liście możesz wybrać rodzaj kontrolki, z którego powinien dziedziczyć formantu. Lista jest podzbiorem klasy kontrolek, które są dostępne dla `CreateWindowEx` i dodatkowe formanty standardowe, które są określone w commctrl.h. Ten wybór decyduje styl formantu w `PreCreateWindow` działa w programach *ProjName*Ctrl.cpp pliku. Aby uzyskać więcej informacji, zobacz [kontrolki ActiveX MFC: Tworzenie podklasy kontrolki Windows](../../mfc/mfc-activex-controls-subclassing-a-windows-control.md).  
  
|Formant|Opis|  
|-------------|-----------------|  
|**PRZYCISK**|Kontrolka przycisku Windows|  
|**POLE KOMBI COMBOBOX**|Kontrolka pola kombi Windows|  
|**EDYTUJ**|Formant pola edycji Windows|  
|**POLE LISTY**|Pole listy Windows|  
|**PASEK PRZEWIJANIA**|Windows pasek przewijania|  
|**STATYCZNE**|Formant statyczny Windows|  
|**msctls_hotkey32**|Formantu wspólnego klawisza dostępu|  
|**msctls_progress32**|Pasek wspólne kontrolki postępu|  
|**msctls_statusbar32**|Stan paska formantu typowego|  
|**msctls_trackbar32**|Śledź paska formantu typowego|  
|**msctls_updown32**|Przycisk pokrętła (lub góra dół) wspólną kontrolą|  
|**SysAnimate32**|Typowe formantu animacji|  
|**SysHeader32**|Typowe kontrolki nagłówka|  
|**SysListView32**|Wspólnego formantu widoku listy|  
|**SysTabControl32**|Typowe formantu karty|  
|**SysTreeView32**|Wspólnego formantu widoku drzewa|  
  
 **Aktywowany, gdy widoczny**  
 Określa, czy okno został utworzony dla kontrolki, gdy jest on dostępny. Domyślnie **aktywowany, gdy widoczny** opcja jest zaznaczona. Jeśli chcesz odłożyć aktywację kontroli, dopóki kontener wymaga (na przykład, gdy użytkownik kliknie przycisk myszy), usuń zaznaczenie tej opcji. Gdy ta funkcja jest wyłączona, formant nie są naliczane pieniędzy na tworzenie okien, dopóki nie jest to wymagane. Aby uzyskać więcej informacji, zobacz [wyłączanie opcji aktywacji w przypadku widoczności](../../mfc/turning-off-the-activate-when-visible-option.md).  
  
 **Niewidoczne w czasie wykonywania**  
 Określa, że kontrolka nie ma interfejsu użytkownika w czasie wykonywania. Czasomierz to rodzaj kontrolki, które prawdopodobnie chcą być niewidoczna.  
  
 **Ma okno dialogowe informacje**  
 Określa, że kontrolka ma Standardowy Windows **o** okno dialogowe, które wyświetla numer wersji i informacje o prawach autorskich.  
  
> [!NOTE]
>  Jak użytkownik uzyskuje dostęp do pomocy dla formantu zależy od tego, jak zostały zaimplementowane pomocy i czy zintegrowano pomoc do kontrolek za pomocą kontenerów. Aby uzyskać więcej informacji na temat sposobu integrowania pomocy, na [biblioteki MSDN Library](http://go.microsoft.com/fwlink/p/?linkid=150542) witryny sieci Web, wyszukiwanie "Dodawanie Context-Sensitive pomoc do kontrolki ActiveX MFC".  
  
 Po wybraniu tej opcji, wstawia `AboutBox` kontrolować metody w klasie kontrolki projektu (C*ProjName*Ctrl.cpp) i dodaje AboutBox do mapy wysyłania projektu. Domyślnie ta opcja jest zaznaczona.  
  
 **Zoptymalizowany kod rysowania**  
 Określa, że kontener przywraca oryginalne obiekty GDI automatycznie po wszystkich kontrole kontenerów, które są rysowane na ten sam kontekst urządzenia, zostały wystawione. Aby uzyskać więcej informacji na temat tej funkcji, zobacz [Optymalizacja rysowania formantów](../../mfc/optimizing-control-drawing.md).  
  
 **Aktywacji niepowiązanej z oknami**  
 Określa, że kontrolka nie generuje okna podczas aktywowania jej. Aktywacji niepowiązanej z oknami umożliwia nieprostokątne lub przezroczyste formantów i kontrolce wymaga wymaga mniejsze obciążenie systemu niż formant z okna. Nieobcinanego kontekstu urządzenia lub aktywacji pozbawionej migotania nie zezwala na kontrolce. Kontenery, które zostały utworzone przed 1996 roku nie obsługują aktywacji niepowiązanej z oknami. Aby uzyskać więcej informacji o tym, jak użyć tej opcji, zobacz [zapewnianie aktywacji niepowiązanej z oknami](../../mfc/providing-windowless-activation.md).  
  
 **Nieobcinanego kontekstu urządzenia**  
 Zastępuje [COleControl::GetControlFlags](../../mfc/reference/colecontrol-class.md#getcontrolflags) w nagłówku kontroli (*projname*ctrl.h) można wyłączyć wywołanie `IntersectClipRect` przez `COleControl`. Po wybraniu tej opcji, zapewnia korzyści małej szybkości. Jeśli wybierzesz **aktywacji niepowiązanej z oknami**, ta funkcja nie jest dostępna. Aby uzyskać więcej informacji, zobacz [używanie Nieobcinanego kontekstu urządzenia](../../mfc/using-an-unclipped-device-context.md).  
  
 **Aktywacji pozbawionej migotania**  
 Eliminuje operacji rysowania i towarzyszący migotania visual, która występuje między Stanami aktywnych i nieaktywnych formantu. Jeśli wybierzesz **aktywacji niepowiązanej z oknami**, ta funkcja nie jest dostępna. Po ustawieniu tej opcji `noFlickerActivate` flaga jest jednym z flagi, które są zwracane przez [COleControl::GetControlFlags](../../mfc/reference/colecontrol-class.md#getcontrolflags). Aby uzyskać więcej informacji, zobacz [zapewnianie aktywacji pozbawionej migotania](../../mfc/providing-flicker-free-activation.md).  
  
 **Dostępne w oknie dialogowym Wstaw obiekt**  
 Określa, że formant będzie dostępny w **Wstawianie obiektu** okno dialogowe włączonych kontenerów. Po wybraniu tej opcji `afxRegInsertable` flaga jest jednym z flagi, które są zwracane przez `AfxOleRegisterControlClass`. Za pomocą **Wstawianie obiektu** okno dialogowe, użytkownik może wstawiać nowo utworzone lub istniejące obiekty w dokumencie złożonym.  
  
 **Powiadomienia wskaźnika myszy, gdy nieaktywna**  
 Umożliwia kontrolowanie, które można przetworzyć powiadomień wskaźnika myszy, czy kontrolka jest aktywny, czy nie. Po wybraniu tej opcji `pointerInactive` flaga jest jednym z flagi, które są zwracane przez [COleControl::GetControlFlags](../../mfc/reference/colecontrol-class.md#getcontrolflags). Aby uzyskać więcej informacji o tym, jak użyć tej opcji, zobacz [dostarczanie myszy interakcji podczas nieaktywne](../../mfc/providing-mouse-interaction-while-inactive.md).  
  
 **Działa jako kontrolka proste ramki**  
 Określa, czy kontrolka jest kontenerem dla innych kontrolek, ustawiając OLEMISC_SIMPLEFRAME bitów formantu. Aby uzyskać więcej informacji na [biblioteki MSDN Library](http://go.microsoft.com/fwlink/p/?linkid=150542) witryny sieci Web, wyszukiwanie "Proste ramki lokacji zawierania".  
  
 **Ładuje właściwości asynchronicznie**  
 Umożliwia zresetowanie wszelkie poprzednie dane asynchronicznego i inicjuje nowe obciążenie asynchronicznego właściwości formantu.  
  
## <a name="see-also"></a>Zobacz też  
 [Kreator kontrolek ActiveX MFC](../../mfc/reference/mfc-activex-control-wizard.md)   
 [Ustawienia aplikacji, Kreator kontrolek ActiveX MFC](../../mfc/reference/application-settings-mfc-activex-control-wizard.md)   
 [Nazwy kontrolek, kreator kontrolek ActiveX MFC](../../mfc/reference/control-names-mfc-activex-control-wizard.md)

