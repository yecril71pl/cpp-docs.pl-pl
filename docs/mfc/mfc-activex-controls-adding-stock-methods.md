---
title: 'Kontrolki ActiveX MFC: dodawanie metod standardowych'
ms.date: 09/12/2018
helpviewer_keywords:
- MFC ActiveX controls [MFC], stock methods
- MFC ActiveX controls [MFC], methods
- DoClick method [MFC]
ms.assetid: bc4fad78-cabd-4cc0-a798-464b1a682f0b
ms.openlocfilehash: 1e47e45efe27c9562cf8500f8941bcf0e259448a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50585032"
---
# <a name="mfc-activex-controls-adding-stock-methods"></a>Kontrolki ActiveX MFC: dodawanie metod standardowych

Podstawowe metody różni się od niestandardowej metody, w tym, że został już zaimplementowany przez klasę [COleControl](../mfc/reference/colecontrol-class.md). Na przykład `COleControl` zawiera funkcję wstępnie zdefiniowanego elementu członkowskiego, która obsługuje metodę odświeżania kontrolki. Wpis mapy wysyłania dla tej metody akcji jest DISP_STOCKFUNC_REFRESH.

>[!IMPORTANT]
> ActiveX jest technologią starszą, która nie powinny być używane w przypadku nowych wdrożeń. Aby uzyskać więcej informacji na temat nowych technologii, które zastępują ActiveX zobacz [formantów ActiveX](activex-controls.md).

`COleControl` obsługuje dwie podstawowe metody: DoClick i odświeżania. Po wywołaniu polecenia Odśwież przez kontrolki użytkownika można natychmiast zaktualizować wygląd formantu; DoClick wywoływaną ognia formantu kliknij zdarzenie.

|Metoda|Wpis mapy wysyłania|Komentarz|
|------------|------------------------|-------------|
|`DoClick`|**(DISP_STOCKPROP_DOCLICK)**|Wyzwala zdarzenie Click.|
|`Refresh`|**(DISP_STOCKPROP_REFRESH)**|Aktualizacje od razu wygląd formantu.|

##  <a name="_core_adding_a_stock_method_using_classwizard"></a> Dodawanie metody akcji przy użyciu Kreator dodawania metody

Dodawanie metody akcji jest proste przy użyciu [Kreator dodawania metody](../ide/add-method-wizard.md). Poniższa procedura demonstruje, Dodawanie metody odświeżania do formantu, który został utworzony za pomocą Kreatora kontrolek ActiveX MFC.

#### <a name="to-add-the-stock-refresh-method-using-the-add-method-wizard"></a>Aby dodać podstawowe metody odświeżania za pomocą Kreatora dodawania — metoda

1. Załaduj projekt formantu.

1. W widoku klas rozwiń węzeł biblioteki kontrolki.

1. Kliknij prawym przyciskiem myszy węzeł interfejsu dla kontrolki (drugi węzeł węzła biblioteki), aby otworzyć menu skrótów.

1. W menu skrótów kliknij **Dodaj** a następnie kliknij przycisk **Dodaj metodę**.

   Spowoduje to otwarcie Kreatora dodawania metody.

1. W **nazwę metody** kliknij **Odśwież**.

1. Kliknij przycisk **Zakończ**.

##  <a name="_core_classwizard_changes_for_stock_methods"></a> Dodaj zmiany kreatora metody dla metod standardowych

Ponieważ podstawowy metoda odświeżania jest obsługiwana przez klasę bazową dla formantu, **Kreator dodawania metody** nie zmienia się z deklaracji klasy formantu w dowolny sposób. Dodaje wpis dla metody do mapy wysyłania kontrolki a w jej. Plik IDL. Następujący wiersz zostanie dodany do mapy wysyłania formantu, znajduje się w swojej implementacji (. Plik CPP):

[!code-cpp[NVC_MFC_AxUI#16](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-methods_1.cpp)]

Dzięki temu metoda odświeżania dostępne dla użytkowników do formantu.

Następujący wiersz jest dodawany do formantu. Plik IDL:

[!code-cpp[NVC_MFC_AxUI#17](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-methods_2.idl)]

Ten wiersz przypisuje metoda odświeżanie określony numer Identyfikatora.

## <a name="see-also"></a>Zobacz też

[Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)

