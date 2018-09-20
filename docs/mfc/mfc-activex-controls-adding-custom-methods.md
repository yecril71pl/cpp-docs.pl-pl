---
title: 'Kontrolki ActiveX MFC: Dodawanie metod niestandardowych | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], methods
- PtInCircle custom method [MFC]
ms.assetid: 8f8dc344-44a0-4021-8db5-4cdd3d700e18
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 428f43d5cd1a0cfaa4b5f829b59208ce96eab85d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46441086"
---
# <a name="mfc-activex-controls-adding-custom-methods"></a>Kontrolki ActiveX MFC: dodawanie metod niestandardowych

Niestandardowe metody różnią się od metod standardowych, w tym, że nie są już zaimplementowane przez `COleControl`. Należy podać implementacja dla każdej niestandardowej metody dodanych do formantu.

>[!IMPORTANT]
> ActiveX jest technologią starszą, która nie powinny być używane w przypadku nowych wdrożeń. Aby uzyskać więcej informacji na temat nowych technologii, które wypierają ActiveX zobacz [formantów ActiveX](activex-controls.md).

Użytkownik formantu ActiveX, można wywołać metodę niestandardowe, w dowolnym momencie, aby wykonać akcje specyficzne dla kontrolki. Wpis mapy wysyłania niestandardowych metod jest DISP_FUNCTION formularza.

##  <a name="_core_adding_a_custom_method_with_classwizard"></a> Dodawanie niestandardowej metody z Kreator dodawania metody

Poniższa procedura demonstruje, dodając niestandardową metodę ptincircle — do formantu ActiveX szkielet kodu. Ptincircle — Określa, czy współrzędne przekazany do kontrolki są wewnątrz lub na zewnątrz koła. Tę samą procedurę można również dodawać inne niestandardowe metody. Zastąp nazwę niestandardową metodę i jego parametrów ptincircle — Nazwa metody i parametrów.

> [!NOTE]
>  W tym przykładzie użyto `InCircle` funkcji z tego artykułu zdarzenia. Aby uzyskać więcej informacji na temat tej funkcji, zobacz artykuł [kontrolki ActiveX MFC: Dodawanie zdarzeń niestandardowych do kontrolki ActiveX](../mfc/mfc-activex-controls-adding-custom-events.md).

#### <a name="to-add-the-ptincircle-custom-method-using-the-add-method-wizard"></a>Aby dodać ptincircle — metoda niestandardowa, za pomocą Kreatora dodawania — metoda

1. Załaduj projekt formantu.

1. W widoku klas rozwiń węzeł biblioteki kontrolki.

1. Kliknij prawym przyciskiem myszy węzeł interfejsu dla kontrolki (drugi węzeł węzła biblioteki), aby otworzyć menu skrótów.

1. W menu skrótów kliknij **Dodaj** a następnie kliknij przycisk **Dodaj metodę**.

     Spowoduje to otwarcie Kreatora dodawania metody.

1. W **nazwę metody** wpisz *ptincircle —*.

1. W **wewnętrzna nazwa** wpisz nazwę metody wewnętrznej funkcji lub użyj wartości domyślnej (w tym przypadku *ptincircle —*).

1. W **typie zwracanym** kliknij **VARIANT_BOOL** dla zwracanego typu metody.

1. Za pomocą **typ parametru** i **Nazwa parametru** formantów, Dodaj parametr o nazwie *xCoord* (typ *OLE_XPOS_PIXELS*).

9. Za pomocą **typ parametru** i **Nazwa parametru** formantów, Dodaj parametr o nazwie *yCoord* (typ *OLE_YPOS_PIXELS*).

10. Kliknij przycisk **Zakończ**.

##  <a name="_core_classwizard_changes_for_custom_methods"></a> Dodaj zmiany kreatora metody dla metod niestandardowych

Po dodaniu niestandardowej metody, Kreator dodawania metody sprawia, że pewne zmiany do formantu nagłówka klasy (. Godz.), jak i implementację (. Plikach CPP). Następujący wiersz jest dodawany do deklaracji mapy wysyłania w nagłówku klasy formantu (. H) plik:

[!code-cpp[NVC_MFC_AxUI#18](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-methods_1.h)]

Ten kod deklaruje procedury obsługi wysyłania metodę o nazwie `PtInCircle`. Ta funkcja może być wywoływana przez użytkownika kontroli przy użyciu zewnętrzną nazwę `PtInCircle`.

Następujący wiersz jest dodawany do formantu. Plik IDL:

[!code-cpp[NVC_MFC_AxUI#19](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-methods_2.idl)]

Ten wiersz przypisuje `PtInCircle` metody określonej numer identyfikacyjny, metoda pozycji na liście właściwości i metod Kreator dodawania metody. Ponieważ Kreator dodawania metody została użyta, aby dodać niestandardową metodę, wpis dla niego został dodany automatycznie do projektu. Plik IDL.

Ponadto, znajduje się następujący wiersz w implementacji (. Plik CPP) klasy kontrolki, zostanie dodany do mapy wysyłania formantu:

[!code-cpp[NVC_MFC_AxUI#20](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-methods_3.cpp)]

DISP_FUNCTION — makro mapuje metody `PtInCircle` funkcję obsługi formantu, `PtInCircle`, deklaruje typ zwracany jako **VARIANT_BOOL**i deklaruje dwa parametry typu **VTS_XPOS_PIXELS** i **VTS_YPOSPIXELS** mają być przekazane do `PtInCircle`.

Ponadto Kreator dodawania metody dodaje funkcję klasy zastępczej `CSampleCtrl::PtInCircle` do dolnej części kontrolki implementacji (. Plik CPP). Aby uzyskać `PtInCircle` działanie, jak wspomniano wcześniej, jego muszą zostać zmodyfikowane w następujący sposób:

[!code-cpp[NVC_MFC_AxUI#21](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-methods_4.cpp)]

## <a name="see-also"></a>Zobacz też

[Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)<br/>
[Widok klasy i Przeglądarka obiektów, ikony](/visualstudio/ide/class-view-and-object-browser-icons)

