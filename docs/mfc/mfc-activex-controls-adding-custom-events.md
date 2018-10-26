---
title: 'Kontrolki ActiveX MFC: Dodawanie zdarzeń niestandardowych | Dokumentacja firmy Microsoft'
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
ms.openlocfilehash: 4d5db33dda6abc141c9247c74c16624bef5f0fc8
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50076038"
---
# <a name="mfc-activex-controls-adding-custom-events"></a>Kontrolki ActiveX MFC: dodawanie zdarzeń niestandardowych

Zdarzenia niestandardowe różnią się od standardowych zdarzeń, w tym, że nie są one automatycznie uruchamiane przez klasę `COleControl`. Zdarzenie niestandardowe rozpoznaje określone działanie, określane przez dewelopera kontrolek, jako zdarzenie. Wpisy mapy zdarzeń dla zdarzenia niestandardowe są reprezentowane przez EVENT_CUSTOM — makro. Poniższa sekcja implementuje niestandardowego zdarzenia dla projektu kontrolki ActiveX, który został utworzony przy użyciu Kreatora kontrolek ActiveX.

##  <a name="_core_adding_a_custom_event_with_classwizard"></a> Dodawanie niestandardowego zdarzenia z Kreator dodawania zdarzenia

Poniższa procedura dodaje określone zdarzenie niestandardowe clickin —. Ta procedura służy do dodawania innych zdarzeń niestandardowych. Zastąp nazwę niestandardowego zdarzenia i jego parametrów clickin — zdarzenie nazwy i parametry.

#### <a name="to-add-the-clickin-custom-event-using-the-add-event-wizard"></a>Aby dodać clickin — zdarzenie niestandardowe za pomocą Kreatora dodawania zdarzenia

1. Załaduj projekt formantu.

1. W widoku klas kliknij prawym przyciskiem myszy, aby otworzyć menu skrótów klasy kontrolki ActiveX.

1. W menu skrótów kliknij **Dodaj** a następnie kliknij przycisk **Dodawanie zdarzenia**.

   Spowoduje to otwarcie Kreatora dodawania zdarzenia.

1. W **Nazwa zdarzenia** pole, najpierw wybierz dowolne zdarzenie, istniejące, a następnie kliknij pozycję **niestandardowe** radio przycisk, a następnie wpisz *clickin —*.

1. W **wewnętrzna nazwa** wpisz nazwę funkcji uruchomieniu którego zdarzenie. Na przykład użyj wartości domyślnej, w dostarczonych przez Kreator dodawania zdarzenia (`FireClickIn`).

1. Dodaj parametr o nazwie *xCoord* (typ *OLE_XPOS_PIXELS*) przy użyciu **Nazwa parametru** i **typ parametru** kontrolki.

1. Dodaj drugi parametr o nazwie *yCoord* (typ *OLE_YPOS_PIXELS*).

1. Kliknij przycisk **Zakończ** utworzyć zdarzenia.

##  <a name="_core_classwizard_changes_for_custom_events"></a> Dodaj zmiany w zdarzeniu kreatora dla zdarzeń niestandardowych

Po dodaniu niestandardowego zdarzenia, Kreator dodawania zdarzenia sprawia, że zmiany do klasy formantu. GODZ. CPP, i. IDL, pliki. Poniższe przykłady kodu są specyficzne dla clickin — zdarzenie.

Następujące wiersze są dodawane do nagłówka (. H) plik klasy kontrolki:

[!code-cpp[NVC_MFC_AxUI#7](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_1.h)]

Ten kod deklaruje wbudowanej funkcji o nazwie `FireClickIn` wywołująca [COleControl::FireEvent](../mfc/reference/colecontrol-class.md#fireevent) clickin — zdarzenie i parametry zdefiniowane przy użyciu Kreatora dodawania zdarzenia.

Ponadto następujący wiersz zostanie dodany do mapy zdarzeń dla formantu, który znajduje się w implementacji (. Plik CPP) Twojej klasy kontrolki:

[!code-cpp[NVC_MFC_AxUI#8](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_2.cpp)]

Ten kod mapuje zdarzeń clickin — funkcja śródwierszowa `FireClickIn`, przekazując parametry zdefiniowane przy użyciu Kreatora dodawania zdarzenia.

Na koniec następujący wiersz zostanie dodany do kontroli nad. Plik IDL:

[!code-cpp[NVC_MFC_AxUI#9](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_3.idl)]

Ten wiersz przypisuje clickin — zdarzenie określonych numer identyfikacyjny pobranych z wydarzenia pozycji na liście zdarzeń Kreator dodawania zdarzenia. Wpis na liście zdarzeń umożliwia kontenera przewidywać zdarzenia. Na przykład może ona kod procedury obsługi do wykonania, gdy zdarzenie jest uruchamiane.

##  <a name="_core_calling_fireclickin"></a> Fireclickin — wywołanie

Teraz, że dodano clickin — zdarzenie niestandardowe za pomocą Kreatora dodawania zdarzenia, należy zdecydować, kiedy to zdarzenie jest do uruchomienia. Można to zrobić, wywołując `FireClickIn` po wystąpieniu odpowiednie działania. Na potrzeby tego omówienia kontrolka używa `InCircle` funkcję wewnątrz programu obsługi komunikatów WM_LBUTTONDOWN ognia clickin — zdarzenie po kliknięciu wewnątrz okręgu lub eliptycznego regionu. Poniższa procedura dodaje program obsługi WM_LBUTTONDOWN.

#### <a name="to-add-a-message-handler-with-the-add-event-wizard"></a>Aby dodać program obsługi komunikatów za pomocą Kreatora dodawania zdarzenia

1. Załaduj projekt formantu.

1. W widoku klas Wybierz klasy kontrolki ActiveX.

1. W oknie dialogowym właściwości kliknij **wiadomości** przycisku.

   Okno właściwości wyświetla listę komunikatów, które są obsługiwane przez kontrolkę ActiveX. Każdy komunikat pogrubione już ma funkcję obsługi do niej przypisany.

1. W oknie właściwości wybierz wiadomość, którą chcesz obsługiwać. W tym przykładzie wybierz WM_LBUTTONDOWN.

1. W polu listy rozwijanej po prawej stronie wybierz  **\<Dodaj > onlbuttondown —**.

1. Kliknij dwukrotnie przycisk Nowa funkcja obsługi w widoku klas, aby przejść do kod procedury obsługi komunikatów w implementacji (. Plik CPP) kontrolki ActiveX.

Poniższy kod wywoła przykład `InCircle` funkcja za każdym razem, gdy kliknięto lewego przycisku myszy w oknie Kontrola. W tym przykładzie można znaleźć w funkcji obsługi WM_LBUTTONDOWN `OnLButtonDown`w [przykładowe OK](../visual-cpp-samples.md) abstrakcyjne.

[!code-cpp[NVC_MFC_AxUI#10](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_4.cpp)]

> [!NOTE]
>  Gdy Kreator dodawania zdarzenia tworzy programy obsługi komunikatów dotyczących akcji przycisków myszy, po wywołaniu tej samej program obsługi komunikatów klasy bazowej jest automatycznie dodawany. Nie usuwaj tego wywołania. Jeśli formant wykorzystuje dowolne z komunikaty myszy zapasów, programy obsługi komunikatów w klasie bazowej musi zostać wywołany aby upewnić się, że przechwytywanie myszy odbywa się poprawnie.

W poniższym przykładzie zdarzenia generowane, gdy kliknięcie występuje tylko wewnątrz okręgu lub eliptycznego regionu w kontrolce. Aby uzyskać takie zachowanie, możesz umieścić `InCircle` funkcji w implementacji kontroli nad (. Plik CPP):

[!code-cpp[NVC_MFC_AxUI#11](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_5.cpp)]

Należy również dodać następującą deklarację elementu `InCircle` funkcji do formantu nagłówka (. H) plik:

[!code-cpp[NVC_MFC_AxUI#12](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_6.h)]

##  <a name="_core_custom_events_with_stock_names"></a> Zdarzenia niestandardowe z nazwami podstawowe

Można utworzyć zdarzenia niestandardowe z taką samą nazwę jak zdarzeń standardowych, jednak nie można zaimplementować w tej samej kontrolki. Na przykład można utworzyć niestandardowe zdarzenie o nazwie kliknij przycisk, który nie jest wyzwalana, gdy zdarzenie standardowe kliknij zwykle będzie wyzwalać. Przez wywołanie funkcji jego uruchomieniu którego można następnie wywołać zdarzenia kliknij w dowolnym momencie.

Poniższa procedura dodaje niestandardowy kliknij zdarzenie.

#### <a name="to-add-a-custom-event-that-uses-a-stock-event-name"></a>Aby dodać niestandardowe zdarzenie, które używa nazwy zdarzenie

1. Załaduj projekt formantu.

1. W widoku klas kliknij prawym przyciskiem myszy, aby otworzyć menu skrótów klasy kontrolki ActiveX.

1. W menu skrótów kliknij **Dodaj** a następnie kliknij przycisk **Dodawanie zdarzenia**.

   Spowoduje to otwarcie Kreatora dodawania zdarzenia.

1. W **Nazwa zdarzenia** listę rozwijaną, wybierz nazwę zdarzenie na liście. W tym przykładzie wybierz **kliknij**.

1. Aby uzyskać **typ zdarzenia**, wybierz opcję **niestandardowe**.

1. Kliknij przycisk **Zakończ** utworzyć zdarzenia.

1. Wywołaj `FireClick` w odpowiednich miejscach w kodzie.

## <a name="see-also"></a>Zobacz też

[Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)<br/>
[Kontrolki ActiveX MFC: metody](../mfc/mfc-activex-controls-methods.md)<br/>
[Klasa COleControl](../mfc/reference/colecontrol-class.md)
