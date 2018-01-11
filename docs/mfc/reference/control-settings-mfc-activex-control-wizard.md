---
title: "Sterowanie ustawieniami, Kreator formantów MFC ActiveX | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.appwiz.mfc.ctl.settings
dev_langs: C++
helpviewer_keywords: MFC ActiveX Control Wizard, control settings
ms.assetid: 2ccaa4fc-0d52-413e-afa3-ecd474c3f6f0
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 60828b7f40009a5fd88c7f0a7f820ede3de4aa93
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2018
---
# <a name="control-settings-mfc-activex-control-wizard"></a>Ustawienia kontrolki, kreator kontrolek ActiveX MFC
Ta strona kreatora można określić sposób formantu ma zachowywać się. Można na przykład podstawowa formantu na standardowe typy formantów systemu Windows, zoptymalizować jego działanie i wygląd lub wskazują, że formant może działać jako kontener dla innych formantów.  
  
 Aby uzyskać więcej informacji na temat wybierania opcji na tej stronie, aby zmaksymalizować wydajność formantu, zobacz [kontrolki ActiveX MFC: Optymalizacja](../../mfc/mfc-activex-controls-optimization.md).  
  
## <a name="uielement-list"></a>Lista elementów UI  
 **Tworzenie formantu na podstawie**  
 Na tej liście można wybrać rodzaj formantu, z którego powinny dziedziczyć formantu. Lista jest podzbiorem klasy formantów, które są dostępne dla `CreateWindowEx` i dodatkowe formanty standardowe, które są określone w commctrl.h. Wybór określa styl formantu w `PreCreateWindow` działać w *nazwa_projektu.nazwa_modułu.nazwa_procedury*Ctrl.cpp pliku. Aby uzyskać więcej informacji, zobacz [kontrolki ActiveX MFC: Tworzenie podklasy kontrolki okna](../../mfc/mfc-activex-controls-subclassing-a-windows-control.md).  
  
|Formant|Opis|  
|-------------|-----------------|  
|**PRZYCISK**|Kontrolkę przycisku systemu Windows|  
|**POLA KOMBI COMBOBOX**|Kontrolka pola kombi systemu Windows|  
|**EDYTUJ**|Pole edycji systemu Windows|  
|**POLA LISTY**|Pole listy systemu Windows|  
|**PASEK PRZEWIJANIA**|Pasek przewijania systemu Windows|  
|**STATYCZNE**|Kontrolki statycznej systemu Windows|  
|**msctls_hotkey32**|Formantu wspólnego klawisza dostępu|  
|**msctls_progress32**|Pasek formantu wspólnego postępu|  
|**msctls_statusbar32**|Stan paska formantu wspólnego|  
|**msctls_trackbar32**|Śledź superpaska formantu wspólnego|  
|**msctls_updown32**|Przycisk pokrętła (lub góra dół) formantu wspólnego|  
|**SysAnimate32**|Typowe formantu animacji|  
|**SysHeader32**|Typowe kontrolki nagłówka|  
|**SysListView32**|Typowe kontrolki widoku listy|  
|**SysTabControl32**|Typowe formantu karty|  
|**SysTreeView32**|Typowe kontrolki widoku drzewa|  
  
 **Aktywuje, gdy jest widoczne**  
 Określa, że okna dla formantu, gdy jest on dostępny. Domyślnie **uaktywnia się, gdy widoczny** opcja jest zaznaczona. Aby odłożyć aktywację sterowania, dopóki kontenera wymaga (na przykład gdy użytkownik kliknie przycisk myszy), usuń zaznaczenie tej opcji. Jeśli ta funkcja jest wyłączona, formantu nie pociągnąć za sobą konieczności tworzenia okna dopóki nie jest to wymagane. Aby uzyskać więcej informacji, zobacz [wyłączenie aktywować podczas widoczna opcja](../../mfc/turning-off-the-activate-when-visible-option.md).  
  
 **Niewidoczne w czasie wykonywania**  
 Określa, czy formant nie ma interfejsu użytkownika w czasie wykonywania. Czasomierz jest rodzajem formantu, który ma być niewidoczna.  
  
 **Zawiera informacje — okno dialogowe**  
 Określa, czy formant ma standard Windows **o** okno dialogowe, które wyświetla numer wersji i informacje o prawach autorskich.  
  
> [!NOTE]
>  Jak użytkownik uzyskuje dostęp do pomocy dla formantu zależy od tego, jak zostały zaimplementowane pomocy i określa, czy pomoc w kontroli jest zintegrowana z kontenera pomocy. Aby uzyskać więcej informacji na temat sposobu integracji Pomocy, na [biblioteki MSDN Library](http://go.microsoft.com/fwlink/p/?linkid=150542) witryny sieci Web, wyszukaj "Dodawanie Context-Sensitive pomoc do MFC formantu ActiveX".  
  
 Po wybraniu tej opcji wstawia `AboutBox` kontrolować metody w klasie kontroli projektu (C*nazwa_projektu.nazwa_modułu.nazwa_procedury*Ctrl.cpp) i dodaje AboutBox do mapy wysyłania projektu. Domyślnie ta opcja jest zaznaczona.  
  
 **Kod zoptymalizowany rysowania**  
 Określa, że kontener przywraca oryginalne obiekty GDI automatycznie po wszystkich kontrole kontenerów, które są rysowane w kontekście tego samego urządzenia, zostały wystawione. Aby uzyskać więcej informacji na temat tej funkcji, zobacz [Optymalizacja rysowania formantów](../../mfc/optimizing-control-drawing.md).  
  
 **Aktywacja bez okien**  
 Określa, że kontrolka nie tworzy okno jest uaktywniany. Aktywacji niepowiązanej z oknami umożliwia nieprostokątny lub przezroczyste formantów, a formantem bez okien wymaga wymaga mniejsze obciążenie systemu niż formantu, który ma okna. Formant niepowiązane z oknami nie zezwala na nieobcinanego kontekstu urządzenia lub aktywacji pozbawionej migotania. Kontenery, które zostały utworzone przed 1996 nie obsługują aktywacji niepowiązanej z oknami. Aby uzyskać więcej informacji o tym, jak użyć tej opcji, zobacz [zapewnianie aktywacji niepowiązanej z oknami](../../mfc/providing-windowless-activation.md).  
  
 **Nieobcinanego kontekstu urządzenia**  
 Zastępuje [COleControl::GetControlFlags](../../mfc/reference/colecontrol-class.md#getcontrolflags) w nagłówku formantu (*nazwa_projektu.nazwa_modułu.nazwa_procedury*ctrl.h) można wyłączyć wywołanie `IntersectClipRect` przez `COleControl`. Po wybraniu tej opcji zapewnia korzyści małej szybkości. W przypadku wybrania **aktywacji niepowiązanej z oknami**, ta funkcja jest niedostępna. Aby uzyskać więcej informacji, zobacz [używanie Nieobcinanego kontekstu urządzenia](../../mfc/using-an-unclipped-device-context.md).  
  
 **Aktywacji pozbawionej migotania**  
 Eliminuje operacje rysowania i towarzyszące im migotanie, które występują między Stanami aktywną i nieaktywną formantu. W przypadku wybrania **aktywacji niepowiązanej z oknami**, ta funkcja jest niedostępna. Po ustawieniu tej opcji `noFlickerActivate` flaga jest jedną z flag, które są zwracane przez [COleControl::GetControlFlags](../../mfc/reference/colecontrol-class.md#getcontrolflags). Aby uzyskać więcej informacji, zobacz [zapewnianie aktywacji pozbawionej migotania](../../mfc/providing-flicker-free-activation.md).  
  
 **Dostępne w oknie dialogowym Wstaw obiekt**  
 Określa, czy formant będzie dostępny w **Wstaw obiekt** okno dialogowe włączone kontenerów. Po wybraniu tej opcji, `afxRegInsertable` flaga jest jedną z flag, które są zwracane przez `AfxOleRegisterControlClass`. Za pomocą **Wstaw obiekt** okno dialogowe, użytkownik może wstawiać nowo utworzony lub istniejące obiekty do dokumentu złożonego.  
  
 **Powiadomienia wskaźnika myszy, gdy nieaktywny**  
 Umożliwia formant powiadomienia wskaźnika myszy proces, czy formant jest aktywny, czy nie. Po wybraniu tej opcji, `pointerInactive` flaga jest jedną z flag, które są zwracane przez [COleControl::GetControlFlags](../../mfc/reference/colecontrol-class.md#getcontrolflags). Aby uzyskać więcej informacji o tym, jak użyć tej opcji, zobacz [dostarczanie myszy interakcji podczas nieaktywne](../../mfc/providing-mouse-interaction-while-inactive.md).  
  
 **Działa jako formant ramki proste**  
 Określa, czy formant jest kontenerem dla innych formantów przez ustawienie `OLEMISC_SIMPLEFRAME` bit dla formantu. Aby uzyskać więcej informacji na [biblioteki MSDN Library](http://go.microsoft.com/fwlink/p/?linkid=150542) witryny sieci Web, wyszukaj "Proste zawierania lokacji ramki".  
  
 **Ładuje właściwości w sposób asynchroniczny**  
 Włącza Resetowanie wszelkich wcześniejszych danych asynchronicznych i inicjuje nowego załadowania właściwości asynchronicznej formantu.  
  
## <a name="see-also"></a>Zobacz też  
 [Kreator kontrolek ActiveX MFC](../../mfc/reference/mfc-activex-control-wizard.md)   
 [Ustawienia aplikacji, Kreator kontrolek ActiveX MFC](../../mfc/reference/application-settings-mfc-activex-control-wizard.md)   
 [Nazwy kontrolek, kreator kontrolek ActiveX MFC](../../mfc/reference/control-names-mfc-activex-control-wizard.md)

