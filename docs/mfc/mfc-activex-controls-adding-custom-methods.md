---
title: 'Formanty MFC ActiveX: dodawanie metod niestandardowych'
ms.date: 09/12/2018
helpviewer_keywords:
- MFC ActiveX controls [MFC], methods
- PtInCircle custom method [MFC]
ms.assetid: 8f8dc344-44a0-4021-8db5-4cdd3d700e18
ms.openlocfilehash: e32a1c372d89fc4ade414b20a0f77fa162807250
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626159"
---
# <a name="mfc-activex-controls-adding-custom-methods"></a>Formanty MFC ActiveX: dodawanie metod niestandardowych

Metody niestandardowe różnią się od metod podstawowych w tym, że nie zostały one jeszcze zaimplementowane przez `COleControl` . Musisz podać implementację dla każdej niestandardowej metody dodawanej do kontrolki.

>[!IMPORTANT]
> Kontrolka ActiveX to Starsza technologia, która nie powinna być używana do nowych celów programistycznych. Aby uzyskać więcej informacji na temat nowoczesnych technologii, które zastępują ActiveX, zobacz [kontrolki ActiveX](activex-controls.md).

Kontrolka ActiveX może w dowolnym momencie wywołać metodę niestandardową w celu wykonania akcji specyficznych dla kontroli. Wpis mapy wysyłania dla metod niestandardowych ma postać DISP_FUNCTION.

## <a name="adding-a-custom-method-with-the-add-method-wizard"></a><a name="_core_adding_a_custom_method_with_classwizard"></a>Dodawanie metody niestandardowej za pomocą Kreatora dodawania metody

Poniższa procedura pokazuje, jak dodać metodę niestandardową PtInCircle do kodu szkieletowego kontrolki ActiveX. PtInCircle określa, czy współrzędne przenoszone do kontrolki znajdują się wewnątrz okręgu, czy poza nim. Ta sama procedura służy również do dodawania innych metod niestandardowych. Podstaw nazwę metody niestandardowej i jej parametry dla nazwy i parametrów metody PtInCircle.

> [!NOTE]
> Ten przykład używa `InCircle` funkcji ze zdarzeń artykułu. Aby uzyskać więcej informacji na temat tej funkcji, zobacz artykuł [kontrolki ActiveX MFC: Dodawanie niestandardowych zdarzeń do kontrolki ActiveX](mfc-activex-controls-adding-custom-events.md).

#### <a name="to-add-the-ptincircle-custom-method-using-the-add-method-wizard"></a>Aby dodać metodę niestandardową PtInCircle za pomocą Kreatora dodawania metody

1. Załaduj projekt kontrolki.

1. W Widok klasy rozwiń węzeł Biblioteka formantu.

1. Kliknij prawym przyciskiem myszy węzeł interfejsu dla formantu (drugi węzeł węzła biblioteki), aby otworzyć menu skrótów.

1. W menu skrótów kliknij pozycję **Dodaj** , a następnie kliknij pozycję **Dodaj metodę**.

   Spowoduje to otwarcie Kreatora dodawania metody.

1. W polu **Nazwa metody** wpisz *PtInCircle*.

1. W polu **Nazwa wewnętrzna** wpisz nazwę wewnętrznej funkcji metody lub użyj wartości domyślnej (w tym przypadku *PtInCircle*).

1. W polu **zwracany typ** kliknij **VARIANT_BOOL** dla zwracanego typu metody.

1. Za pomocą kontrolek **Typ parametru** i **Nazwa parametru** Dodaj parametr o nazwie *xCoord* (typ *OLE_XPOS_PIXELS*).

1. Za pomocą kontrolek **Typ parametru** i **Nazwa parametru** Dodaj parametr o nazwie *yCoord* (typ *OLE_YPOS_PIXELS*).

1. Kliknij przycisk **Zakończ**.

## <a name="add-method-wizard-changes-for-custom-methods"></a><a name="_core_classwizard_changes_for_custom_methods"></a>Dodawanie zmian Kreatora metody dla metod niestandardowych

Po dodaniu metody niestandardowej Kreator dodawania metody wprowadza pewne zmiany w nagłówku klasy kontrolki (. H) i implementacja (. CPP). Następujący wiersz jest dodawany do deklaracji mapy wysyłania w nagłówku klasy kontrolki (. H):

[!code-cpp[NVC_MFC_AxUI#18](codesnippet/cpp/mfc-activex-controls-adding-custom-methods_1.h)]

Ten kod deklaruje procedurę obsługi metody wysyłania o nazwie `PtInCircle` . Ta funkcja może być wywoływana przez użytkownika kontroli przy użyciu nazwy zewnętrznej `PtInCircle` .

Do kontrolki zostanie dodany następujący wiersz. Plik IDL:

[!code-cpp[NVC_MFC_AxUI#19](codesnippet/cpp/mfc-activex-controls-adding-custom-methods_2.idl)]

Ten wiersz przypisuje `PtInCircle` metodę o określonym numerze identyfikacyjnym, pozycję metody w Kreatorze dodawania metody i liście właściwości. Ponieważ Kreator dodawania metody został użyty do dodania metody niestandardowej, wpis dla niego został dodany automatycznie do projektu. Plik IDL.

Ponadto Poniższy wiersz znajduje się w implementacji (. CPP) plik klasy kontrolki został dodany do mapy wysyłania kontrolki:

[!code-cpp[NVC_MFC_AxUI#20](codesnippet/cpp/mfc-activex-controls-adding-custom-methods_3.cpp)]

Makro DISP_FUNCTION mapuje metodę `PtInCircle` na funkcję procedury obsługi formantu, `PtInCircle` deklaruje zwracany typ do **VARIANT_BOOL**i deklaruje dwa parametry typu **VTS_XPOS_PIXELS** i **VTS_YPOSPIXELS** do przekazanie do `PtInCircle` .

Na koniec Kreator dodawania metody dodaje funkcję zastępczą `CSampleCtrl::PtInCircle` do dolnej części implementacji formantu (. CPP). Aby `PtInCircle` program działał jak wcześniej, należy go zmodyfikować w następujący sposób:

[!code-cpp[NVC_MFC_AxUI#21](codesnippet/cpp/mfc-activex-controls-adding-custom-methods_4.cpp)]

## <a name="see-also"></a>Zobacz też

[Kontrolki ActiveX MFC](mfc-activex-controls.md)<br/>
[Widok klasy i Przeglądarka obiektów ikon](/visualstudio/ide/class-view-and-object-browser-icons)
