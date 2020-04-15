---
title: 'Formanty MFC ActiveX: dodawanie metod standardowych'
ms.date: 09/12/2018
helpviewer_keywords:
- MFC ActiveX controls [MFC], stock methods
- MFC ActiveX controls [MFC], methods
- DoClick method [MFC]
ms.assetid: bc4fad78-cabd-4cc0-a798-464b1a682f0b
ms.openlocfilehash: ec59ccc0cbd48fc3114eb2dc0833dd3dd65691de
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364671"
---
# <a name="mfc-activex-controls-adding-stock-methods"></a>Formanty MFC ActiveX: dodawanie metod standardowych

Metoda zapasowa różni się od metody niestandardowej tym, że jest już zaimplementowana przez klasę [COleControl](../mfc/reference/colecontrol-class.md). Na przykład `COleControl` zawiera wstępnie zdefiniowaną funkcję elementu członkowskiego, która obsługuje Refresh metody formantu. Wpis mapy wysyłki dla tej metody magazynowej jest DISP_STOCKFUNC_REFRESH.

>[!IMPORTANT]
> ActiveX to starsza technologia, która nie powinna być używana do nowego rozwoju. Aby uzyskać więcej informacji na temat nowoczesnych technologii, które zastępują ActiveX, zobacz [ActiveX Controls](activex-controls.md).

`COleControl`obsługuje dwie metody składowania: DoClick i Refresh. Odświeżanie jest wywoływane przez użytkownika formantu, aby natychmiast zaktualizować wygląd formantu; DoClick jest wywoływany do wywołania click kontroli zdarzenia.

|Metoda|Wpis mapy wysyłki|Komentarz|
|------------|------------------------|-------------|
|`DoClick`|**DISP_STOCKPROP_DOCLICK( )**|Uruchamia zdarzenie Click.|
|`Refresh`|**DISP_STOCKPROP_REFRESH( )**|Natychmiast aktualizuje wygląd formantu.|

## <a name="adding-a-stock-method-using-the-add-method-wizard"></a><a name="_core_adding_a_stock_method_using_classwizard"></a>Dodawanie metody magazynowej za pomocą Kreatora dodawania metody

Dodawanie metody magazynowej jest proste za pomocą [Kreatora dodawania metody](../ide/add-method-wizard.md). Poniższa procedura pokazuje dodanie Refresh metody do formantu utworzonego za pomocą Kreatora sterowania MFC ActiveX.

#### <a name="to-add-the-stock-refresh-method-using-the-add-method-wizard"></a>Aby dodać metodę odświeżania zapasów za pomocą Kreatora dodawania metody

1. Załaduj projekt formantu.

1. W widoku klasy rozwiń węzeł biblioteki formantu.

1. Kliknij prawym przyciskiem myszy węzeł interfejsu formantu (drugi węzeł węzła biblioteki), aby otworzyć menu skrótów.

1. W menu skrótów kliknij polecenie **Dodaj,** a następnie kliknij pozycję **Dodaj metodę**.

   Spowoduje to otwarcie Kreatora dodawania metody.

1. W polu **Nazwa metody** kliknij pozycję **Odśwież**.

1. Kliknij przycisk **Zakończ**.

## <a name="add-method-wizard-changes-for-stock-methods"></a><a name="_core_classwizard_changes_for_stock_methods"></a>Dodawanie zmian kreatora metod dla metod magazynowych

Ponieważ czas Refresh metoda jest obsługiwana przez klasę podstawową formantu, **Kreator dodawania metody** nie zmienia deklaracji klasy formantu w żaden sposób. Dodaje wpis dla metody do mapy wysyłki formantu i do jego . IDL. Następujący wiersz jest dodawany do mapy wysyłki formantu, znajdującej się w jego implementacji (. CPP):

[!code-cpp[NVC_MFC_AxUI#16](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-methods_1.cpp)]

Dzięki temu Refresh metoda dostępna dla użytkowników formantu.

Następujący wiersz jest dodawany do formantu . Plik IDL:

[!code-cpp[NVC_MFC_AxUI#17](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-methods_2.idl)]

Ten wiersz przypisuje metody Odśwież określony numer do obydwojców.

## <a name="see-also"></a>Zobacz też

[Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)
