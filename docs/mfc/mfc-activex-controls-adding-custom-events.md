---
title: 'Formanty MFC ActiveX: dodawanie zdarzeń niestandardowych'
ms.date: 11/04/2016
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
ms.openlocfilehash: 8d464e5d7c9731e158e44d66d569fd1555401e17
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364727"
---
# <a name="mfc-activex-controls-adding-custom-events"></a>Formanty MFC ActiveX: dodawanie zdarzeń niestandardowych

Zdarzenia niestandardowe różnią się od zdarzeń giełdowych `COleControl`tym, że nie są automatycznie uruchamiane według klasy . Zdarzenie niestandardowe rozpoznaje określoną akcję, określoną przez dewelopera formantu, jako zdarzenie. Wpisy mapy zdarzeń dla zdarzeń niestandardowych są reprezentowane przez makro EVENT_CUSTOM. W poniższej sekcji implementuje niestandardowe zdarzenie dla projektu kontroli ActiveX, który został utworzony za pomocą Kreatora sterowania ActiveX.

## <a name="adding-a-custom-event-with-the-add-event-wizard"></a><a name="_core_adding_a_custom_event_with_classwizard"></a>Dodawanie zdarzenia niestandardowego za pomocą Kreatora dodawania zdarzeń

Poniższa procedura dodaje określone zdarzenie niestandardowe, ClickIn. Za pomocą tej procedury można dodać inne zdarzenia niestandardowe. Zastąp niestandardową nazwę zdarzenia i jego parametry nazwą i parametrami zdarzenia ClickIn.

#### <a name="to-add-the-clickin-custom-event-using-the-add-event-wizard"></a>Aby dodać zdarzenie niestandardowe ClickIn za pomocą Kreatora dodawania zdarzeń

1. Załaduj projekt formantu.

1. W **widoku klasy**kliknij prawym przyciskiem myszy klasę sterowania ActiveX, aby otworzyć menu skrótów.

1. W menu skrótów kliknij polecenie **Dodaj,** a następnie kliknij pozycję **Dodaj zdarzenie**.

   Spowoduje to otwarcie Kreatora dodawania zdarzeń.

1. W polu **Nazwa zdarzenia** najpierw wybierz istniejące zdarzenie, a następnie kliknij przycisk **opcji Niestandardowe,** a następnie wpisz *polecenie Kliknij przycisk .*

1. W polu **Nazwa wewnętrzna** wpisz nazwę funkcji wypalania zdarzenia. W tym przykładzie należy użyć wartości domyślnej`FireClickIn`dostarczonej przez Kreatora dodawania zdarzeń ( ).

1. Dodaj parametr o nazwie *xCoord* (typ *OLE_XPOS_PIXELS*), używając kontrolek **Nazwa parametru** i **Typ parametru.**

1. Dodaj drugi parametr o nazwie *yCoord* (typ *OLE_YPOS_PIXELS*).

1. Kliknij **przycisk Zakończ,** aby utworzyć zdarzenie.

## <a name="add-event-wizard-changes-for-custom-events"></a><a name="_core_classwizard_changes_for_custom_events"></a>Dodawanie zmian kreatora zdarzeń dla zdarzeń niestandardowych

Po dodaniu zdarzenia niestandardowego Kreator dodawania zdarzeń wprowadza zmiany w klasie formantu . H. CPP i . idl. Następujące przykłady kodu są specyficzne dla ClickIn zdarzenia.

Następujące wiersze są dodawane do nagłówka (. H) plik twojej klasy kontrolnej:

[!code-cpp[NVC_MFC_AxUI#7](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_1.h)]

Ten kod deklaruje wbudowaną `FireClickIn` funkcję wywołaną wywołaną [przez COleControl::FireEvent](../mfc/reference/colecontrol-class.md#fireevent) ze zdarzeniem ClickIn i parametrami zdefiniowanymi za pomocą Kreatora dodawania zdarzeń.

Ponadto do mapy zdarzeń dla formantu, znajdującego się w implementacji (. CPP) w swojej klasie kontrolnej:

[!code-cpp[NVC_MFC_AxUI#8](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_2.cpp)]

Ten kod mapuje zdarzenie ClickIn `FireClickIn`do funkcji wbudowanej, przekazując zdefiniowane parametry za pomocą Kreatora dodawania zdarzeń.

Na koniec do formantu jest dodawany następujący wiersz . Plik IDL:

[!code-cpp[NVC_MFC_AxUI#9](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_3.idl)]

Ten wiersz przypisuje clickin przypadku określonego numeru identyfikatora, pobrane z pozycji zdarzenia na liście zdarzeń Dodaj Kreatora zdarzeń. Wpis na liście zdarzeń umożliwia kontenerowi przewidywanie zdarzenia. Na przykład może zapewnić kod obsługi do wykonania, gdy zdarzenie jest uruchamiany.

## <a name="calling-fireclickin"></a><a name="_core_calling_fireclickin"></a>Wywołanie FireClickIn

Teraz, gdy dodano ClickIn zdarzenie niestandardowe za pomocą Kreatora dodawania zdarzeń, należy zdecydować, kiedy to zdarzenie ma zostać wystrzelone. Można to zrobić, wywołując, `FireClickIn` gdy wystąpi odpowiednia akcja. W tej dyskusji formant `InCircle` używa funkcji `WM_LBUTTONDOWN` wewnątrz obsługi wiadomości do wypalania ClickIn zdarzenia, gdy użytkownik kliknie wewnątrz regionu okrężnego lub eliptycznego. Poniższa procedura `WM_LBUTTONDOWN` dodaje program obsługi.

#### <a name="to-add-a-message-handler-with-the-add-event-wizard"></a>Aby dodać program obsługi wiadomości za pomocą Kreatora dodawania zdarzeń

1. Załaduj projekt formantu.

1. W **widoku klasy**wybierz klasę kontrolną ActiveX.

1. W oknie **Właściwości** zostanie wyświetlona lista komunikatów, które mogą być obsługiwane przez kontrolkę ActiveX. Każda wiadomość wyświetlana pogrubioną czcionką ma już przypisaną funkcję obsługi.

1. Wybierz wiadomość, którą chcesz obsłużyć. W tym przykładzie wybierz opcję `WM_LBUTTONDOWN`.

1. Z listy rozwijanej po prawej stronie wybierz pozycję ** \<Dodaj> OnLButtonDown**.

1. Kliknij dwukrotnie nową funkcję obsługi w **widoku klasy,** aby przejść do kodu obsługi wiadomości w implementacji (. CPP) formantu ActiveX.

Poniższy przykładowy `InCircle` kod wywołuje funkcję za każdym razem, gdy lewy przycisk myszy jest klikany w oknie sterowania. Ten przykład można znaleźć `WM_LBUTTONDOWN` w `OnLButtonDown`funkcji obsługi, w [Circ przykładu](../overview/visual-cpp-samples.md) abstract.

[!code-cpp[NVC_MFC_AxUI#10](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_4.cpp)]

> [!NOTE]
> Gdy Kreator dodawania zdarzeń tworzy programy obsługi wiadomości dla akcji przycisku myszy, wywołanie tego samego programu obsługi wiadomości klasy podstawowej jest automatycznie dodawane. Nie usuwaj tego połączenia. Jeśli formant używa dowolnego komunikatów myszy stock, programy obsługi komunikatów w klasie podstawowej musi zostać wywołana, aby upewnić się, że przechwytywanie myszy jest obsługiwane poprawnie.

W poniższym przykładzie zdarzenie jest uruchamiane tylko wtedy, gdy kliknięcie występuje wewnątrz okrągłego lub eliptycznego regionu w formancie. Aby osiągnąć to zachowanie, `InCircle` można umieścić funkcję w implementacji formantu (. CPP):

[!code-cpp[NVC_MFC_AxUI#11](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_5.cpp)]

Należy również dodać następującą deklarację `InCircle` funkcji do nagłówka formantu (. H) plik:

[!code-cpp[NVC_MFC_AxUI#12](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_6.h)]

## <a name="custom-events-with-stock-names"></a><a name="_core_custom_events_with_stock_names"></a>Zdarzenia niestandardowe z nazwami giełdowymi

Można utworzyć zdarzenia niestandardowe o tej samej nazwie co zdarzenia giełdowe, jednak nie można zaimplementować zarówno w tym samym formancie. Na przykład można utworzyć zdarzenie niestandardowe o nazwie Kliknij, które nie uruchamia się, gdy zdarzenie akcji Kliknij normalnie uruchamia. Następnie można odpalić Click zdarzenia w dowolnym momencie, wywołując jego funkcji wypalania.

Poniższa procedura dodaje niestandardowe zdarzenie Click.

#### <a name="to-add-a-custom-event-that-uses-a-stock-event-name"></a>Aby dodać zdarzenie niestandardowe, które używa nazwy zdarzenia giełdowego

1. Załaduj projekt formantu.

1. W **widoku klasy**kliknij prawym przyciskiem myszy klasę sterowania ActiveX, aby otworzyć menu skrótów.

1. W menu skrótów kliknij polecenie **Dodaj,** a następnie kliknij pozycję **Dodaj zdarzenie**.

   Spowoduje to otwarcie Kreatora dodawania zdarzeń.

1. Na liście rozwijanej **Nazwa zdarzenia** wybierz nazwę zdarzenia giełdowego. W tym przykładzie wybierz pozycję **Kliknij**.

1. W przypadku **typu zdarzenia**wybierz pozycję **Niestandardowe**.

1. Kliknij **przycisk Zakończ,** aby utworzyć zdarzenie.

1. Zadzwoń `FireClick` w odpowiednich miejscach w kodzie.

## <a name="see-also"></a>Zobacz też

[Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)<br/>
[Kontrolki ActiveX MFC: metody](../mfc/mfc-activex-controls-methods.md)<br/>
[Klasa COleControl](../mfc/reference/colecontrol-class.md)
