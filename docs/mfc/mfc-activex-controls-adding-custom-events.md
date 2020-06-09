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
ms.openlocfilehash: 70b0e08bc638b5f630d423ec0db8a169a0119175
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619952"
---
# <a name="mfc-activex-controls-adding-custom-events"></a>Formanty MFC ActiveX: dodawanie zdarzeń niestandardowych

Zdarzenia niestandardowe różnią się od zdarzeń podstawowych w tym, że nie są automatycznie uruchamiane przez klasę `COleControl` . Zdarzenie niestandardowe rozpoznaje pewne działania określone przez dewelopera kontroli jako zdarzenie. Wpisy mapy zdarzeń dla zdarzeń niestandardowych są reprezentowane przez makro EVENT_CUSTOM. Poniższa sekcja implementuje niestandardowe zdarzenie dla projektu kontrolki ActiveX, który został utworzony za pomocą Kreatora kontrolki ActiveX.

## <a name="adding-a-custom-event-with-the-add-event-wizard"></a><a name="_core_adding_a_custom_event_with_classwizard"></a>Dodawanie zdarzenia niestandardowego za pomocą Kreatora dodawania zdarzenia

Poniższa procedura umożliwia dodanie określonego zdarzenia niestandardowego. Ta procedura służy do dodawania innych zdarzeń niestandardowych. Zastąp niestandardową nazwę zdarzenia i jej parametry dla nazwy i parametrów zdarzenia kliknij.

#### <a name="to-add-the-clickin-custom-event-using-the-add-event-wizard"></a>Aby dodać zdarzenie niestandardowe kliknięcia przy użyciu Kreatora dodawania zdarzenia

1. Załaduj projekt kontrolki.

1. W **Widok klasy**kliknij prawym przyciskiem myszy klasę kontrolki ActiveX, aby otworzyć menu skrótów.

1. W menu skrótów kliknij pozycję **Dodaj** , a następnie kliknij pozycję **Dodaj zdarzenie**.

   Spowoduje to otwarcie Kreatora dodawania zdarzenia.

1. W polu **Nazwa zdarzenia** najpierw wybierz dowolne istniejące zdarzenie, a następnie kliknij przycisk radiowy **niestandardowy** , a następnie wpisz *polecenie*.

1. W polu **Nazwa wewnętrzna** wpisz nazwę funkcji uruchamiania zdarzenia. Na potrzeby tego przykładu Użyj wartości domyślnej dostarczonej przez Kreatora dodawania zdarzenia ( `FireClickIn` ).

1. Dodaj parametr o nazwie *xCoord* (typ *OLE_XPOS_PIXELS*), używając kontrolek **Nazwa parametru** i **Typ parametru** .

1. Dodaj drugi parametr o nazwie *yCoord* (typ *OLE_YPOS_PIXELS*).

1. Kliknij przycisk **Zakończ** , aby utworzyć zdarzenie.

## <a name="add-event-wizard-changes-for-custom-events"></a><a name="_core_classwizard_changes_for_custom_events"></a>Dodawanie zmian Kreatora zdarzeń dla zdarzeń niestandardowych

Po dodaniu zdarzenia niestandardowego Kreator dodawania zdarzenia wprowadza zmiany do klasy kontrolek. H,. CPP i. Pliki IDL. Poniższe przykłady kodu są specyficzne dla zdarzenia kliknięcia.

Następujące wiersze są dodawane do nagłówka (. H) plik klasy kontrolki:

[!code-cpp[NVC_MFC_AxUI#7](codesnippet/cpp/mfc-activex-controls-adding-custom-events_1.h)]

Ten kod deklaruje wbudowaną funkcję o nazwie `FireClickIn` , która wywołuje [COleControl:: FireEvent](reference/colecontrol-class.md#fireevent) przy użyciu zdarzenia kliknięcia i parametrów zdefiniowanych za pomocą Kreatora dodawania zdarzenia.

Ponadto Poniższy wiersz jest dodawany do mapy zdarzeń kontrolki, która znajduje się w implementacji (. CPP) plik klasy kontrolki:

[!code-cpp[NVC_MFC_AxUI#8](codesnippet/cpp/mfc-activex-controls-adding-custom-events_2.cpp)]

Ten kod mapuje zdarzenie do funkcji inline `FireClickIn` , przekazując parametry zdefiniowane za pomocą Kreatora dodawania zdarzenia.

Na koniec Poniższy wiersz jest dodawany do kontrolki. Plik IDL:

[!code-cpp[NVC_MFC_AxUI#9](codesnippet/cpp/mfc-activex-controls-adding-custom-events_3.idl)]

Ten wiersz służy do przypisywania zdarzenia kliknij określonego numeru IDENTYFIKACYJNego z pozycji zdarzenia na liście zdarzeń Kreatora dodawania zdarzenia. Wpis na liście zdarzeń umożliwia kontenerowi przewidzenie zdarzenia. Może na przykład dostarczyć kod procedury obsługi, który ma zostać wykonany po uruchomieniu zdarzenia.

## <a name="calling-fireclickin"></a><a name="_core_calling_fireclickin"></a>Wywoływanie FireClickIn

Po dodaniu zdarzenia niestandardowego kliknięcia przy użyciu Kreatora dodawania zdarzenia należy określić, kiedy to zdarzenie ma zostać wyzwolone. Można to zrobić przez wywołanie `FireClickIn` , gdy wystąpi odpowiednie działanie. W tej dyskusji formant używa `InCircle` funkcji wewnątrz `WM_LBUTTONDOWN` procedury obsługi komunikatów do uruchamiania zdarzenia kliknięcia, gdy użytkownik kliknie wewnątrz regionu cyklicznego lub eliptycznego. Poniższa procedura dodaje procedurę `WM_LBUTTONDOWN` obsługi.

#### <a name="to-add-a-message-handler-with-the-add-event-wizard"></a>Aby dodać procedurę obsługi komunikatów za pomocą Kreatora dodawania zdarzenia

1. Załaduj projekt kontrolki.

1. W **Widok klasy**wybierz klasę kontrolki ActiveX.

1. W oknie **Właściwości** zostanie wyświetlona lista komunikatów, które mogą być obsługiwane przez kontrolkę ActiveX. Każdy komunikat wyświetlany w pogrubieniu ma już przypisaną funkcję obsługi.

1. Wybierz komunikat, który chcesz obsłużyć. Na potrzeby tego przykładu wybierz opcję `WM_LBUTTONDOWN` .

1. W polu listy rozwijanej po prawej stronie wybierz pozycję ** \<Add> OnLButtonDown**.

1. Kliknij dwukrotnie nową funkcję obsługi w **Widok klasy** , aby przejść do kodu procedury obsługi komunikatów w implementacji (. CPP) pliku kontrolki ActiveX.

Poniższy przykładowy kod wywołuje funkcję za `InCircle` każdym razem, gdy zostanie kliknięty lewy przycisk myszy w oknie sterowania. Ten przykład można znaleźć w `WM_LBUTTONDOWN` funkcji obsługi, `OnLButtonDown` , w streszczeniu [przykładu](../overview/visual-cpp-samples.md) .

[!code-cpp[NVC_MFC_AxUI#10](codesnippet/cpp/mfc-activex-controls-adding-custom-events_4.cpp)]

> [!NOTE]
> Gdy Kreator dodawania zdarzeń tworzy obsługę komunikatów dla akcji przycisków myszy, automatycznie dodawane jest wywołanie tej samej procedury obsługi komunikatów klasy bazowej. Nie usuwaj tego wywołania. Jeśli kontrolka używa dowolnego z komunikatów myszy, należy wywołać procedury obsługi komunikatów w klasie bazowej, aby upewnić się, że funkcja przechwytywania myszy jest prawidłowo obsługiwana.

W poniższym przykładzie zdarzenie jest wyzwalane tylko wtedy, gdy kliknięcie występuje wewnątrz regionu kołowego lub eliptycznego w obrębie formantu. Aby osiągnąć takie zachowanie, można umieścić `InCircle` funkcję w implementacji kontrolki (. CPP):

[!code-cpp[NVC_MFC_AxUI#11](codesnippet/cpp/mfc-activex-controls-adding-custom-events_5.cpp)]

Konieczne będzie również dodanie następującej deklaracji `InCircle` funkcji do nagłówka kontrolki (. H):

[!code-cpp[NVC_MFC_AxUI#12](codesnippet/cpp/mfc-activex-controls-adding-custom-events_6.h)]

## <a name="custom-events-with-stock-names"></a><a name="_core_custom_events_with_stock_names"></a>Zdarzenia niestandardowe z nazwami zasobów

Można utworzyć zdarzenia niestandardowe o takiej samej nazwie jak zdarzenia podstawowe, ale nie można zaimplementować obu w tej samej kontrolce. Na przykład możesz chcieć utworzyć niestandardowe zdarzenie o nazwie kliknij, które nie uruchamia się po kliknięciu zdarzenia giełdowego normalnie. Następnie można uruchomić zdarzenie kliknięcia w dowolnym momencie, wywołując funkcję uruchamiania.

Poniższa procedura umożliwia dodanie niestandardowego zdarzenia kliknięcia.

#### <a name="to-add-a-custom-event-that-uses-a-stock-event-name"></a>Aby dodać niestandardowe zdarzenie używające nazwy zdarzenia giełdowego

1. Załaduj projekt kontrolki.

1. W **Widok klasy**kliknij prawym przyciskiem myszy klasę kontrolki ActiveX, aby otworzyć menu skrótów.

1. W menu skrótów kliknij pozycję **Dodaj** , a następnie kliknij pozycję **Dodaj zdarzenie**.

   Spowoduje to otwarcie Kreatora dodawania zdarzenia.

1. Z listy rozwijanej **Nazwa zdarzenia** wybierz nazwę zdarzenia giełdowego. Na potrzeby tego przykładu wybierz **pozycję kliknij**.

1. W obszarze **Typ zdarzenia**wybierz pozycję **niestandardowy**.

1. Kliknij przycisk **Zakończ** , aby utworzyć zdarzenie.

1. Wywołaj w `FireClick` odpowiednich miejscach w kodzie.

## <a name="see-also"></a>Zobacz też

[Kontrolki ActiveX MFC](mfc-activex-controls.md)<br/>
[Kontrolki ActiveX MFC: metody](mfc-activex-controls-methods.md)<br/>
[Klasa COleControl](reference/colecontrol-class.md)
