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
ms.openlocfilehash: 41ac0180242aea3143a1df2c32dc81fb18cd7dca
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370779"
---
# <a name="mfc-activex-controls-using-data-binding-in-an-activex-control"></a>Kontrolki ActiveX MFC: używanie powiązania danych w kontrolce ActiveX

Jednym z bardziej zaawansowanych zastosowań formantów ActiveX jest powiązanie danych, co umożliwia właściwość formantu do powiązania z określonym polem w bazie danych. Gdy użytkownik modyfikuje dane w tej właściwości powiązanej, formant powiadamia bazę danych i żąda aktualizacji pola rekordu. Baza danych następnie powiadamia kontrolę nad powodzenie lub niepowodzenie żądania.

>[!IMPORTANT]
> ActiveX to starsza technologia, która nie powinna być używana do nowego rozwoju. Aby uzyskać więcej informacji na temat nowoczesnych technologii, które zastępują ActiveX, zobacz [ActiveX Controls](activex-controls.md).

W tym artykule opisano stronę kontrolną zadania. Implementowanie interakcji powiązania danych z bazą danych jest odpowiedzialny za kontenera kontroli. Sposób zarządzania interakcjami bazy danych w kontenerze wykracza poza zakres tej dokumentacji. Jak przygotować formant do powiązania danych jest wyjaśnione w pozostałej części tego artykułu.

![Diagram koncepcyjny kontroli danych&#45;powiązanych](../mfc/media/vc374v1.gif "Diagram koncepcyjny kontroli danych&#45;powiązanych") <br/>
Diagram koncepcyjny formantu związanego z danymi

Klasa `COleControl` udostępnia funkcje elementów członkowskich, które sprawiają, że powiązanie danych jest łatwym procesem do zaimplementowania. Pierwsza [funkcja, BoundPropertyRequestEdit](../mfc/reference/colecontrol-class.md#boundpropertyrequestedit), służy do żądania uprawnień do zmiany wartości właściwości. [BoundPropertyChanged](../mfc/reference/colecontrol-class.md#boundpropertychanged), druga funkcja, jest wywoływana po pomyślnej zmianie wartości właściwości.

W tym artykule omówiono następujące tematy:

- [Tworzenie właściwości stockowej możliwej do wiązania](#vchowcreatingbindablestockproperty)

- [Tworzenie metody get/set możliwej do wiązania](#vchowcreatingbindablegetsetmethod)

## <a name="creating-a-bindable-stock-property"></a><a name="vchowcreatingbindablestockproperty"></a>Tworzenie właściwości stockowej możliwej do wiązania

Istnieje możliwość utworzenia właściwości magazynu związane z danymi, chociaż jest bardziej prawdopodobne, że będzie chcesz [bindable get/ set metody](#vchowcreatingbindablegetsetmethod).

> [!NOTE]
> Właściwości magazynowe `bindable` mają `requestedit` domyślnie atrybuty i atrybuty.

#### <a name="to-add-a-bindable-stock-property-using-the-add-property-wizard"></a>Aby dodać właściwość magazynu, która można powiązać za pomocą Kreatora dodawania właściwości

1. Rozpocznij projekt za pomocą [Kreatora sterowania MFC ActiveX](../mfc/reference/mfc-activex-control-wizard.md).

1. Kliknij prawym przyciskiem myszy węzeł interfejsu dla formantu.

   Spowoduje to otwarcie menu skrótów.

1. W menu skrótów kliknij polecenie **Dodaj,** a następnie kliknij pozycję **Dodaj właściwość**.

1. Wybierz jeden z wpisów z listy rozwijanej **Nazwa właściwości.** Na przykład można wybrać **tekst**.

   Ponieważ **Text** jest właściwością magazynu, atrybuty **bindable** i **requestedit** są już zaznaczone.

1. Zaznacz następujące pola wyboru na karcie **Atrybuty IDL:** **displaybind** i **defaultbind,** aby dodać atrybuty do definicji właściwości w projekcie . IDL. Te atrybuty sprawiają, że formant jest widoczny dla użytkownika i uczynić właściwość magazynu domyślną właściwość do wiązania.

W tym momencie formant może wyświetlać dane ze źródła danych, ale użytkownik nie będzie mógł zaktualizować pól danych. Jeśli chcesz, aby formant mógł również aktualizować dane, zmień `OnOcmCommand` funkcję [OnOcmCommand,](../mfc/mfc-activex-controls-subclassing-a-windows-control.md) aby wyglądała następująco:

[!code-cpp[NVC_MFC_AxData#1](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_1.cpp)]

Teraz można utworzyć projekt, który zarejestruje formant. Po wstawieniu formantu w oknie dialogowym zostaną dodane właściwości **Pole danych** i **Źródło danych,** a teraz można wybrać źródło danych i pole do wyświetlenia w formancie.

## <a name="creating-a-bindable-getset-method"></a><a name="vchowcreatingbindablegetsetmethod"></a>Tworzenie metody get/set możliwej do wiązania

Oprócz metody get/set związanej z danymi można również utworzyć [właściwość magazynu, którą można powiązać.](#vchowcreatingbindablestockproperty)

> [!NOTE]
> W tej procedurze przyjęto założenie, że masz projekt formantu ActiveX, który podklasuje formant systemu Windows.

#### <a name="to-add-a-bindable-getset-method-using-the-add-property-wizard"></a>Aby dodać metodę get/set można powiązać za pomocą Kreatora dodawania właściwości

1. Załaduj projekt formantu.

1. Na stronie **Ustawienia sterowania** wybierz klasę okna dla formantu do podklasy. Na przykład można podklasy kontrolki EDIT.

1. Załaduj projekt formantu.

1. Kliknij prawym przyciskiem myszy węzeł interfejsu dla formantu.

   Spowoduje to otwarcie menu skrótów.

1. W menu skrótów kliknij polecenie **Dodaj,** a następnie kliknij pozycję **Dodaj właściwość**.

1. Wpisz nazwę właściwości w polu **Nazwa właściwości.** Użyj `MyProp` w tym przykładzie.

1. Wybierz typ danych z listy rozwijanej **Typ właściwości.** W tym przykładzie **użyj skrótu.**

1. W przypadku **typu implementacji**kliknij pozycję **Pobierz/Ustaw metody**.

1. Zaznacz następujące pola wyboru na karcie Atrybuty IDL: **bindable**, **requestedit**, **displaybind**i **defaultbind** , aby dodać atrybuty do definicji właściwości w projekcie . IDL. Te atrybuty sprawiają, że formant jest widoczny dla użytkownika i uczynić właściwość magazynu domyślną właściwość do wiązania.

1. Kliknij przycisk **Zakończ**.

1. Zmodyfikuj treść funkcji tak, `SetMyProp` aby zawierała następujący kod:

   [!code-cpp[NVC_MFC_AxData#2](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_2.cpp)]

1. Parametr przekazany do `BoundPropertyChanged` `BoundPropertyRequestEdit` funkcji i jest dispid właściwości, który jest parametr przekazany do id() atrybut właściwości w . IDL.

1. Zmodyfikuj [onocmcommand](../mfc/mfc-activex-controls-subclassing-a-windows-control.md) funkcji, więc zawiera następujący kod:

   [!code-cpp[NVC_MFC_AxData#1](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_1.cpp)]

1. Zmodyfikuj `OnDraw` funkcję tak, aby zawierała następujący kod:

   [!code-cpp[NVC_MFC_AxData#3](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_3.cpp)]

1. Do sekcji publicznej pliku nagłówka pliku nagłówka dla klasy kontrolnej dodaj następujące definicje (konstruktory) dla zmiennych elementów członkowskich:

   [!code-cpp[NVC_MFC_AxData#4](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_4.h)]

1. Ustaw ostatni wiersz w `DoPropExchange` funkcji:

   [!code-cpp[NVC_MFC_AxData#5](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_5.cpp)]

1. Zmodyfikuj `OnResetState` funkcję tak, aby zawierała następujący kod:

   [!code-cpp[NVC_MFC_AxData#6](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_6.cpp)]

1. Zmodyfikuj `GetMyProp` funkcję tak, aby zawierała następujący kod:

   [!code-cpp[NVC_MFC_AxData#7](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_7.cpp)]

Teraz można utworzyć projekt, który zarejestruje formant. Po wstawieniu formantu w oknie dialogowym zostaną dodane właściwości **Pole danych** i **Źródło danych,** a teraz można wybrać źródło danych i pole do wyświetlenia w formancie.

## <a name="see-also"></a>Zobacz też

[Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)
