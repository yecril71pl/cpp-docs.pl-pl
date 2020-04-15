---
title: 'Formanty MFC ActiveX: dodawanie metod niestandardowych'
ms.date: 09/12/2018
helpviewer_keywords:
- MFC ActiveX controls [MFC], methods
- PtInCircle custom method [MFC]
ms.assetid: 8f8dc344-44a0-4021-8db5-4cdd3d700e18
ms.openlocfilehash: 88d486248eab5d980463764db34bf40b05b830dc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364713"
---
# <a name="mfc-activex-controls-adding-custom-methods"></a>Formanty MFC ActiveX: dodawanie metod niestandardowych

Metody niestandardowe różnią się od metod magazynowych `COleControl`tym, że nie są już implementowane przez plik . Należy podać implementacji dla każdej metody niestandardowej, które można dodać do formantu.

>[!IMPORTANT]
> ActiveX to starsza technologia, która nie powinna być używana do nowego rozwoju. Aby uzyskać więcej informacji na temat nowoczesnych technologii, które zastępują ActiveX, zobacz [ActiveX Controls](activex-controls.md).

Użytkownik formantu ActiveX może wywołać metodę niestandardową w dowolnym momencie, aby wykonać akcje specyficzne dla kontroli. Wpis mapy wysyłki dla metod niestandardowych jest DISP_FUNCTION formularza.

## <a name="adding-a-custom-method-with-the-add-method-wizard"></a><a name="_core_adding_a_custom_method_with_classwizard"></a>Dodawanie metody niestandardowej za pomocą Kreatora dodawania metody

Poniższa procedura pokazuje dodanie metody niestandardowej PtInCircle do kodu szkieletu formantu ActiveX. PtInCircle określa, czy współrzędne przekazywane do formantu znajdują się wewnątrz lub na zewnątrz okręgu. Ta sama procedura może być również używana do dodawania innych metod niestandardowych. Zastąp nazwę metody niestandardowej i jej parametry dla nazwy i parametrów metody PtInCircle.

> [!NOTE]
> W tym przykładzie `InCircle` używa funkcji z artykułu Zdarzenia. Aby uzyskać więcej informacji na temat tej funkcji, zobacz artykuł [MFC ActiveX Controls: Dodawanie zdarzeń niestandardowych do formantu ActiveX](../mfc/mfc-activex-controls-adding-custom-events.md).

#### <a name="to-add-the-ptincircle-custom-method-using-the-add-method-wizard"></a>Aby dodać metodę niestandardową PtInCircle za pomocą Kreatora dodawania metody

1. Załaduj projekt formantu.

1. W widoku klasy rozwiń węzeł biblioteki formantu.

1. Kliknij prawym przyciskiem myszy węzeł interfejsu formantu (drugi węzeł węzła biblioteki), aby otworzyć menu skrótów.

1. W menu skrótów kliknij polecenie **Dodaj,** a następnie kliknij pozycję **Dodaj metodę**.

   Spowoduje to otwarcie Kreatora dodawania metody.

1. W polu **Nazwa metody** wpisz *PtInCircle*.

1. W polu **Nazwa wewnętrzna** wpisz nazwę funkcji wewnętrznej metody lub użyj wartości domyślnej (w tym przypadku *PtInCircle*).

1. W polu **Zwracany typ** kliknij **VARIANT_BOOL** dla typu zwracanej metody.

1. Za pomocą **kontrolek Typ parametru** i **Nazwa parametru** dodaj parametr o nazwie *xCoord* (typ *OLE_XPOS_PIXELS*).

1. Za pomocą **kontrolek Typ parametru** i **Nazwa parametru** dodaj parametr o nazwie *yCoord* (typ *OLE_YPOS_PIXELS*).

1. Kliknij przycisk **Zakończ**.

## <a name="add-method-wizard-changes-for-custom-methods"></a><a name="_core_classwizard_changes_for_custom_methods"></a>Dodawanie zmian kreatora metod dla metod niestandardowych

Po dodaniu metody niestandardowej Kreator dodawania metody wprowadza pewne zmiany w nagłówku klasy kontrolnej (. H) i wdrożenie (. CPP). Następujący wiersz jest dodawany do deklaracji mapy wysyłki w nagłówku klasy kontrolnej (. H) plik:

[!code-cpp[NVC_MFC_AxUI#18](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-methods_1.h)]

Ten kod deklaruje program obsługi `PtInCircle`metody wysyłki o nazwie . Ta funkcja może być wywoływana przez `PtInCircle`użytkownika formantu przy użyciu nazwy zewnętrznej .

Następujący wiersz jest dodawany do formantu . Plik IDL:

[!code-cpp[NVC_MFC_AxUI#19](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-methods_2.idl)]

Ten wiersz przypisuje `PtInCircle` metodę określony numer identyfikatora, położenie metody na liście Metod Kreatora dodawania metody i właściwości. Ponieważ Kreator dodawania metody został użyty do dodania metody niestandardowej, wpis został automatycznie dodany do projektu . IDL.

Ponadto następujący wiersz, znajduje się w realizacji (. CPP) klasy kontrolnej, jest dodawany do mapy wysyłki formantu:

[!code-cpp[NVC_MFC_AxUI#20](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-methods_3.cpp)]

Makro DISP_FUNCTION mapuje metodę `PtInCircle` na funkcję obsługi formantu, `PtInCircle`deklaruje, że typ zwracany ma być **VARIANT_BOOL**i deklaruje dwa parametry typu **VTS_XPOS_PIXELS** i **VTS_YPOSPIXELS,** które mają zostać przekazane do `PtInCircle`.

Na koniec Kreator dodawania metody `CSampleCtrl::PtInCircle` dodaje funkcję skrótową do dolnej części implementacji formantu (. CPP). Aby `PtInCircle` funkcja ta funkcjonowała wcześniej, musi być zmieniona w następujący sposób:

[!code-cpp[NVC_MFC_AxUI#21](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-methods_4.cpp)]

## <a name="see-also"></a>Zobacz też

[Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)<br/>
[Ikony widoku klasy i przeglądarki obiektów](/visualstudio/ide/class-view-and-object-browser-icons)
