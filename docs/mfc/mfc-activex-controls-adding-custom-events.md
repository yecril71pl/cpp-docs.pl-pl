---
title: 'Formanty MFC ActiveX: Dodawanie zdarzeń niestandardowych | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], events [MFC]
- EVENT_CUSTOM prefix [MFC]
- custom events [MFC], adding to ActiveX controls
- EVENT_CUSTOM macro [MFC]
- InCircle method [MFC]
- ClickIn event
- FireClickIn event
- COleControl class [MFC], custom events [MFC]
- Click event, custom events [MFC]
- events [MFC], ActiveX controls
- custom events [MFC]
- FireEvent method, adding custom events
ms.assetid: c584d053-1e34-47aa-958e-37d3e9b85892
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5b82232b8f2ad7a5e3bc1ff8fed0e8a38b1a7d66
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33352534"
---
# <a name="mfc-activex-controls-adding-custom-events"></a>Kontrolki ActiveX MFC: dodawanie zdarzeń niestandardowych
Niestandardowe zdarzenia różnią się ze standardowych zdarzeń, nie są one automatycznie uruchamiane przez klasę `COleControl`. Zdarzenie niestandardowe rozpoznaje niektórych działań, określany przez dewelopera kontrolek jako zdarzenie. Wpisy mapy zdarzeń dla zdarzenia niestandardowe są reprezentowane przez `EVENT_CUSTOM` makra. Poniższa sekcja implementuje zdarzenie niestandardowe dla projektu formantu ActiveX, który został utworzony przy użyciu Kreatora formantów ActiveX.  
  
##  <a name="_core_adding_a_custom_event_with_classwizard"></a> Dodawanie niestandardowych zdarzeń z Kreator dodawania zdarzenia  
 Poniższa procedura dodaje określonego zdarzenia niestandardowe clickin —. Ta procedura służy do dodawania innych zdarzeń niestandardowych. Zastąp nazwę zdarzenie niestandardowe, a jego parametrów clickin — zdarzenie nazwy i parametry.  
  
#### <a name="to-add-the-clickin-custom-event-using-the-add-event-wizard"></a>Aby dodać clickin — zdarzenie niestandardowe przy użyciu Kreatora dodawania zdarzenia  
  
1.  Załaduj projekt z kontroli.  
  
2.  W widoku klas kliknij prawym przyciskiem myszy Twojej klasy kontrolki ActiveX, aby otworzyć menu skrótów.  
  
3.  W menu skrótów kliknij **Dodaj** , a następnie kliknij przycisk **Dodawanie zdarzenia**.  
  
     Spowoduje to otwarcie Kreatora dodawania zdarzenia.  
  
4.  W **Nazwa zdarzenia** polu, najpierw wybierz wszystkie istniejące zdarzenia, a następnie kliknij pozycję **niestandardowy** radiowych przycisk, a następnie wpisz `ClickIn`.  
  
5.  W **wewnętrzna nazwa** wpisz nazwę zdarzenia uruchamiania funkcji. Na przykład użyj wartości domyślnej, wyświetlane przez Kreatora dodawania zdarzenia (`FireClickIn`).  
  
6.  Dodawanie parametru o nazwie `xCoord` (typ `OLE_XPOS_PIXELS`), za pomocą narzędzia **Nazwa parametru** i **typ parametru** kontrolki.  
  
7.  Dodaj drugi parametr o nazwie `yCoord` (typ `OLE_YPOS_PIXELS`).  
  
8.  Kliknij przycisk **Zakończ** utworzyć zdarzenia.  
  
##  <a name="_core_classwizard_changes_for_custom_events"></a> Dodawanie zdarzenia zmiany kreatora dla zdarzeń niestandardowych  
 Po dodaniu niestandardowych zdarzeń, Kreator dodawania zdarzenia zmienia klasy formantu. H. CPP, i. IDL, pliki. Poniższe przykłady kodu są specyficzne dla clickin — zdarzenie.  
  
 Następujące wiersze są dodawane do nagłówka (. H) pliku Twojej klasy kontrolki:  
  
 [!code-cpp[NVC_MFC_AxUI#7](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_1.h)]  
  
 Ten kod deklaruje wbudowanej funkcji o nazwie `FireClickIn` wywołującym [COleControl::FireEvent](../mfc/reference/colecontrol-class.md#fireevent) o parametrach i clickin — zdarzenie zdefiniowany za pomocą Kreatora dodawania zdarzenia.  
  
 Ponadto następujące wiersz zostanie dodany do mapy zdarzeń dla formantu, znajduje się w implementacji (. Pliku CPP) Twojej klasy kontrolki:  
  
 [!code-cpp[NVC_MFC_AxUI#8](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_2.cpp)]  
  
 Ten kod mapuje clickin — zdarzenie funkcji wbudowanej `FireClickIn`, przekazywanie parametrów zdefiniowanych, za pomocą Kreatora dodawania zdarzenia.  
  
 Na koniec następujący wiersz jest dodawany do formantu. Plik IDL:  
  
 [!code-cpp[NVC_MFC_AxUI#9](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_3.idl)]  
  
 Ten wiersz przypisuje clickin — zdarzenie określonych numer identyfikacyjny pobranych z pozycji zdarzenia na liście zdarzeń Kreator dodawania zdarzenia. Wpis na liście zdarzeń umożliwia kontenera do przewidzenia zdarzenia. Na przykład może ona kod obsługi do wykonania, gdy zdarzenie jest wywoływane.  
  
##  <a name="_core_calling_fireclickin"></a> Fireclickin — wywołanie  
 Teraz, gdy zostaną dodane za pomocą Kreatora dodawania zdarzenia clickin — zdarzenie niestandardowe, należy zdecydować, gdy to zdarzenie ma być uruchamiane. Można to zrobić przez wywołanie metody `FireClickIn` po wystąpieniu odpowiednią akcję. Dla tej dyskusji używa kontrolki `InCircle` działać wewnątrz `WM_LBUTTONDOWN` obsługi wiadomości uruchomienie clickin — zdarzenie, gdy użytkownik kliknie wewnątrz okrągły lub eliptycznej regionu. Dodaje procedurę `WM_LBUTTONDOWN` obsługi.  
  
#### <a name="to-add-a-message-handler-with-the-add-event-wizard"></a>Aby dodać program obsługi komunikatów przy użyciu Kreatora dodawania zdarzenia  
  
1.  Załaduj projekt z kontroli.  
  
2.  W widoku klas wybierz Twojej klasy kontrolki ActiveX.  
  
3.  Kliknij w oknie właściwości **wiadomości** przycisku.  
  
     Okno właściwości wyświetla listę komunikatów, które są obsługiwane przez formant ActiveX. Dowolny komunikat pogrubione już przypisano funkcję obsługi do niego.  
  
4.  W oknie właściwości wybierz wiadomości, które mają być obsługiwane. Na przykład wybierz `WM_LBUTTONDOWN`.  
  
5.  W polu listy rozwijanej po prawej stronie wybierz  **\<Dodaj > OnLButtonDown**.  
  
6.  Kliknij dwukrotnie ikonę Nowa funkcja obsługi w widoku klas, aby przejść do kod obsługi komunikatów w implementacji (. Pliku CPP) formantu ActiveX.  
  
 Poniższy kod przykładowy wywołania **InCircle** funkcji każdym kliknięciu lewym przyciskiem myszy w oknie kontrolki. W tym przykładzie można znaleźć w `WM_LBUTTONDOWN` funkcji obsługi `OnLButtonDown`w [próbki OK](../visual-cpp-samples.md) abstrakcyjny.  
  
 [!code-cpp[NVC_MFC_AxUI#10](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_4.cpp)]  
  
> [!NOTE]
>  Gdy Kreator dodawania zdarzenia tworzy programy obsługi komunikatów dla przycisku myszy, jest automatycznie dodawany wywołanie tej samej klasy podstawowej program obsługi komunikatów. Nie należy usuwać tego wywołania. Jeśli formantu używa dowolny z komunikatów myszy standardowych, programy obsługi wiadomości w klasie podstawowej musi zostać wywołana aby upewnić się, że przechwytywanie myszy odbywa się poprawnie.  
  
 W poniższym przykładzie zdarzenia generowane, gdy kliknięcie występuje tylko wewnątrz okrągły lub eliptycznej region w formancie. Aby osiągnąć ten problem, możesz umieścić `InCircle` funkcji w implementacji formantu (. Pliku CPP):  
  
 [!code-cpp[NVC_MFC_AxUI#11](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_5.cpp)]  
  
 Należy również dodać następujące deklaracja `InCircle` funkcji do formantu nagłówka (. H) plików:  
  
 [!code-cpp[NVC_MFC_AxUI#12](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_6.h)]  
  
##  <a name="_core_custom_events_with_stock_names"></a> Niestandardowe zdarzenia o standardowych nazwach  
 Niestandardowe zdarzenia można utworzyć z taką samą nazwę jak standardowych zdarzeń, jednak nie można zaimplementować zarówno w tej samej kontrolki. Na przykład można utworzyć niestandardowe zdarzenie o nazwie kliknij przycisk, który nie jest wyzwalana, gdy zdarzenie standardowe kliknij zwykle spowoduje uruchomienie. Następnie można wywołać zdarzenia kliknij w dowolnym momencie przez wywołanie funkcji jego uruchamiania.  
  
 Poniższa procedura dodaje niestandardowych kliknij zdarzenie.  
  
#### <a name="to-add-a-custom-event-that-uses-a-stock-event-name"></a>Aby dodać niestandardowe zdarzenie, które używa nazwy zdarzenie  
  
1.  Załaduj projekt z kontroli.  
  
2.  W widoku klas kliknij prawym przyciskiem myszy Twojej klasy kontrolki ActiveX, aby otworzyć menu skrótów.  
  
3.  W menu skrótów kliknij **Dodaj** , a następnie kliknij przycisk **Dodawanie zdarzenia**.  
  
     Spowoduje to otwarcie Kreatora dodawania zdarzenia.  
  
4.  W **Nazwa zdarzenia** listy rozwijanej wybierz nazwę zdarzenie. Na przykład wybierz **kliknij**.  
  
5.  Dla **typ zdarzenia**, wybierz pozycję **niestandardowy**.  
  
6.  Kliknij przycisk **Zakończ** utworzyć zdarzenia.  
  
7.  Wywołanie `FireClick` w odpowiednich miejscach w kodzie.  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)   
 [Formanty MFC ActiveX: metody](../mfc/mfc-activex-controls-methods.md)   
 [Klasa COleControl](../mfc/reference/colecontrol-class.md)
