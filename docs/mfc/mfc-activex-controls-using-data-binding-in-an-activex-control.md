---
title: 'Kontrolki ActiveX MFC: używanie powiązania danych w kontrolce ActiveX'
ms.date: 11/19/2018
f1_keywords:
- bindable
- requestedit
- defaultbind
- displaybind
- dispid
helpviewer_keywords:
- MFC ActiveX controls [MFC], data binding
- data binding [MFC], MFC ActiveX controls
- data-bound controls [MFC], MFC ActiveX controls
- controls [MFC], data binding
- bound controls [MFC], MFC ActiveX
ms.assetid: 476b590a-bf2a-498a-81b7-dd476bd346f1
ms.openlocfilehash: b32dbd8e1777f11998085a90e8851b25e4298e1a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224997"
---
# <a name="mfc-activex-controls-using-data-binding-in-an-activex-control"></a>Kontrolki ActiveX MFC: używanie powiązania danych w kontrolce ActiveX

Jednym z bardziej zaawansowanych sposobów użycia formantów ActiveX jest powiązanie danych, co pozwala na powiązanie z określonym polem w bazie danych właściwości formantu. Gdy użytkownik modyfikuje dane w tej powiązanej właściwości, formant powiadamia bazę danych i żąda aktualizacji pola rekordu. Następnie baza danych powiadamia kontrolę nad sukcesem lub niepowodzeniem żądania.

>[!IMPORTANT]
> Kontrolka ActiveX to Starsza technologia, która nie powinna być używana do nowych celów programistycznych. Aby uzyskać więcej informacji na temat nowoczesnych technologii, które zastępują ActiveX, zobacz [kontrolki ActiveX](activex-controls.md).

Ten artykuł dotyczy strony kontrolki zadania. Zaimplementowanie interakcji z powiązaniem danych z bazą danych jest obowiązkiem kontenera kontroli. Zarządzanie interakcjami bazy danych w kontenerze wykracza poza zakres tej dokumentacji. Sposób przygotowania kontroli dla powiązania danych znajduje się w dalszej części tego artykułu.

![Diagram koncepcyjny kontrolki powiązanej&#45;danych](../mfc/media/vc374v1.gif "Diagram koncepcyjny kontrolki powiązanej&#45;danych") <br/>
Diagram koncepcyjny kontrolki powiązanej z danymi

`COleControl`Klasa zawiera dwie funkcje członkowskie, które tworzą powiązanie danych z łatwym procesem implementacji. Pierwsza funkcja, [BoundPropertyRequestEdit](reference/colecontrol-class.md#boundpropertyrequestedit), jest używana do żądania uprawnień do zmiany wartości właściwości. [BoundPropertyChanged](reference/colecontrol-class.md#boundpropertychanged), druga funkcja jest wywoływana po pomyślnym zmianie wartości właściwości.

W tym artykule omówiono następujące tematy:

- [Tworzenie właściwości zasobów możliwej do powiązania](#vchowcreatingbindablestockproperty)

- [Tworzenie metody get/set możliwej do powiązania](#vchowcreatingbindablegetsetmethod)

## <a name="creating-a-bindable-stock-property"></a><a name="vchowcreatingbindablestockproperty"></a>Tworzenie właściwości zasobów możliwej do powiązania

Istnieje możliwość utworzenia właściwości podstawowych powiązanych z danymi, chociaż jest to bardziej prawdopodobne, że należy użyć [metody get/set do powiązania](#vchowcreatingbindablegetsetmethod).

> [!NOTE]
> Właściwości podstawowe mają `bindable` `requestedit` Domyślnie atrybuty i.

#### <a name="to-add-a-bindable-stock-property-using-the-add-property-wizard"></a>Aby dodać właściwość zasobów możliwej do powiązania za pomocą Kreatora dodawania właściwości

1. Rozpocznij projekt przy użyciu [Kreatora kontrolek ActiveX MFC](reference/mfc-activex-control-wizard.md).

1. Kliknij prawym przyciskiem myszy węzeł interfejsu dla kontrolki.

   Spowoduje to otwarcie menu skrótów.

1. W menu skrótów kliknij polecenie **Dodaj** , a następnie kliknij przycisk **Dodaj właściwość**.

1. Wybierz jeden z wpisów z listy rozwijanej **Nazwa właściwości** . Na przykład możesz zaznaczyć **tekst**.

   Ponieważ **tekst** jest właściwością giełdową, atrybuty możliwe do **powiązania** i **requestedit** są już zaznaczone.

1. Zaznacz następujące pola wyboru na karcie **atrybuty IDL** : **displaybind** i **defaultbind** , aby dodać atrybuty do definicji właściwości w projekcie. Plik IDL. Te atrybuty sprawiają, że formant jest widoczny dla użytkownika i ustaw właściwość Stock jako domyślną właściwość, którą można powiązać.

W tym momencie formant może wyświetlać dane ze źródła danych, ale użytkownik nie będzie mógł aktualizować pól danych. Aby formant mógł także aktualizować dane, należy zmienić `OnOcmCommand` funkcję [OnOcmCommand](mfc-activex-controls-subclassing-a-windows-control.md) , aby wyglądać następująco:

[!code-cpp[NVC_MFC_AxData#1](codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_1.cpp)]

Teraz można skompilować projekt, który będzie rejestrował formant. Po wstawieniu kontrolki w oknie dialogowym zostaną dodane **pola danych** i właściwości **źródła danych** , a teraz można wybrać źródło danych i pole do wyświetlenia w formancie.

## <a name="creating-a-bindable-getset-method"></a><a name="vchowcreatingbindablegetsetmethod"></a>Tworzenie metody get/set możliwej do powiązania

Oprócz metody get/set powiązanej z danymi można także utworzyć [Właściwość zasobów](#vchowcreatingbindablestockproperty)możliwej do powiązania.

> [!NOTE]
> W tej procedurze przyjęto założenie, że istnieje projekt kontrolki ActiveX, który jest podklasą kontrolki systemu Windows.

#### <a name="to-add-a-bindable-getset-method-using-the-add-property-wizard"></a>Aby dodać metodę get/set do powiązania za pomocą Kreatora dodawania właściwości

1. Załaduj projekt kontrolki.

1. Na stronie **Ustawienia kontroli** wybierz klasę okna dla kontrolki do podklasy. Na przykład możesz chcieć utworzyć podklasę kontrolki edycji.

1. Załaduj projekt kontrolki.

1. Kliknij prawym przyciskiem myszy węzeł interfejsu dla kontrolki.

   Spowoduje to otwarcie menu skrótów.

1. W menu skrótów kliknij polecenie **Dodaj** , a następnie kliknij przycisk **Dodaj właściwość**.

1. Wpisz nazwę właściwości w polu **Nazwa właściwości** . Użyj `MyProp` w tym przykładzie.

1. Wybierz typ danych z listy rozwijanej **Typ właściwości** . Użyj **`short`** w tym przykładzie.

1. W obszarze **Typ implementacji**kliknij pozycję **Pobierz/ustaw metody**.

1. Zaznacz następujące pola wyboru na karcie atrybuty IDL: możliwe do **powiązania**, **requestedit**, **displaybind**i **defaultbind** , aby dodać atrybuty do definicji właściwości w projekcie. Plik IDL. Te atrybuty sprawiają, że formant jest widoczny dla użytkownika i ustaw właściwość Stock jako domyślną właściwość, którą można powiązać.

1. Kliknij przycisk **Zakończ**.

1. Zmodyfikuj treść `SetMyProp` funkcji, tak aby zawierała następujący kod:

   [!code-cpp[NVC_MFC_AxData#2](codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_2.cpp)]

1. Parametr przesłany do `BoundPropertyChanged` funkcji i `BoundPropertyRequestEdit` jest identyfikatorem DISPID właściwości, który jest parametrem przesłanym do atrybutu ID () właściwości w. Plik IDL.

1. Zmodyfikuj funkcję [OnOcmCommand](mfc-activex-controls-subclassing-a-windows-control.md) , aby zawierała następujący kod:

   [!code-cpp[NVC_MFC_AxData#1](codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_1.cpp)]

1. Zmodyfikuj `OnDraw` funkcję tak, aby zawierała następujący kod:

   [!code-cpp[NVC_MFC_AxData#3](codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_3.cpp)]

1. Do publicznej sekcji pliku nagłówkowego plik nagłówkowy klasy kontrolki, Dodaj następujące definicje (konstruktorów) dla zmiennych składowych:

   [!code-cpp[NVC_MFC_AxData#4](codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_4.h)]

1. Ustaw następujący wiersz jako ostatni wiersz w `DoPropExchange` funkcji:

   [!code-cpp[NVC_MFC_AxData#5](codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_5.cpp)]

1. Zmodyfikuj `OnResetState` funkcję tak, aby zawierała następujący kod:

   [!code-cpp[NVC_MFC_AxData#6](codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_6.cpp)]

1. Zmodyfikuj `GetMyProp` funkcję tak, aby zawierała następujący kod:

   [!code-cpp[NVC_MFC_AxData#7](codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_7.cpp)]

Teraz można skompilować projekt, który będzie rejestrował formant. Po wstawieniu kontrolki w oknie dialogowym zostaną dodane **pola danych** i właściwości **źródła danych** , a teraz można wybrać źródło danych i pole do wyświetlenia w formancie.

## <a name="see-also"></a>Zobacz także

[Kontrolki ActiveX MFC](mfc-activex-controls.md)
