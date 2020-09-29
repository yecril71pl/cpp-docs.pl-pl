---
title: 'Formanty MFC ActiveX: dodawanie metod standardowych'
ms.date: 09/12/2018
helpviewer_keywords:
- MFC ActiveX controls [MFC], stock methods
- MFC ActiveX controls [MFC], methods
- DoClick method [MFC]
ms.assetid: bc4fad78-cabd-4cc0-a798-464b1a682f0b
ms.openlocfilehash: b4b01e4fb202cfd7a923d22cb57ce5ec6988e11d
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91502288"
---
# <a name="mfc-activex-controls-adding-stock-methods"></a>Formanty MFC ActiveX: dodawanie metod standardowych

Metoda magazynowa różni się od metody niestandardowej w tym, że została już zaimplementowana przez klasę [COleControl](reference/colecontrol-class.md). Na przykład `COleControl` zawiera wstępnie zdefiniowaną funkcję członkowską, która obsługuje metodę Refresh dla kontrolki. Wpis mapy wysyłania dla tej metody spisu jest DISP_STOCKFUNC_REFRESH.

>[!IMPORTANT]
> Kontrolka ActiveX to Starsza technologia, która nie powinna być używana do nowych celów programistycznych. Aby uzyskać więcej informacji na temat nowoczesnych technologii, które zastępują ActiveX, zobacz [kontrolki ActiveX](activex-controls.md).

`COleControl` obsługuje dwie metody podstawowe: DoClick i Refresh. Odświeżanie jest wywoływane przez użytkownika kontrolki w celu natychmiastowej aktualizacji wyglądu kontrolki; DoClick jest wywoływana w celu wyzwolenia zdarzenia kliknięcia kontrolki.

|Metoda|Wpis mapy wysyłania|Komentarz|
|------------|------------------------|-------------|
|`DoClick`|**DISP_STOCKPROP_DOCLICK ()**|Uruchamia zdarzenie kliknięcia.|
|`Refresh`|**DISP_STOCKPROP_REFRESH ()**|Natychmiast aktualizuje wygląd formantu.|

## <a name="adding-a-stock-method-using-the-add-method-wizard"></a><a name="_core_adding_a_stock_method_using_classwizard"></a> Dodawanie metody giełdowej przy użyciu Kreatora dodawania metody

Dodawanie metody giełdowej jest proste przy użyciu [Kreatora dodawania metody](../ide/adding-a-method-visual-cpp.md#add-method-wizard). Poniższa procedura pokazuje, jak dodać metodę Refresh do kontrolki utworzonej przy użyciu kreatora kontrolek ActiveX MFC.

#### <a name="to-add-the-stock-refresh-method-using-the-add-method-wizard"></a>Aby dodać metodę odświeżania magazynu za pomocą Kreatora dodawania metody

1. Załaduj projekt kontrolki.

1. W Widok klasy rozwiń węzeł Biblioteka formantu.

1. Kliknij prawym przyciskiem myszy węzeł interfejsu dla formantu (drugi węzeł węzła biblioteki), aby otworzyć menu skrótów.

1. W menu skrótów kliknij pozycję **Dodaj** , a następnie kliknij pozycję **Dodaj metodę**.

   Spowoduje to otwarcie Kreatora dodawania metody.

1. W polu **Nazwa metody** kliknij przycisk **Odśwież**.

1. Kliknij przycisk **Zakończ**.

## <a name="add-method-wizard-changes-for-stock-methods"></a><a name="_core_classwizard_changes_for_stock_methods"></a> Dodawanie zmian w Kreatorze metody dla metod podstawowych

Ponieważ metoda odświeżania magazynu jest obsługiwana przez klasę bazową formantu, **Kreator dodawania metody** nie zmienia deklaracji klasy kontrolki w jakikolwiek sposób. Dodaje wpis dla metody do mapy wysyłania kontrolki i do jej. Plik IDL. Poniższy wiersz jest dodawany do mapy wysyłania kontrolki, która znajduje się w jej implementacji (. CPP):

[!code-cpp[NVC_MFC_AxUI#16](codesnippet/cpp/mfc-activex-controls-adding-stock-methods_1.cpp)]

Dzięki temu Metoda odświeżania jest dostępna dla użytkowników formantu.

Do kontrolki zostanie dodany następujący wiersz. Plik IDL:

[!code-cpp[NVC_MFC_AxUI#17](codesnippet/cpp/mfc-activex-controls-adding-stock-methods_2.idl)]

Ten wiersz służy do przypisywania metody Refresh określonego numeru IDENTYFIKACYJNego.

## <a name="see-also"></a>Zobacz też

[Kontrolki ActiveX MFC](mfc-activex-controls.md)
