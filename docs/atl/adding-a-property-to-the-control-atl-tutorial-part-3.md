---
title: Dodawanie właściwości do kontrolki (ALT — Samouczek, część 3)
ms.custom: get-started-article
ms.date: 09/26/2018
ms.assetid: f775fe34-103b-4f07-9999-400e987ee030
ms.openlocfilehash: b5f9f9c8fde44dd67a9a05aeae0f91fb7b5f2f4d
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57281021"
---
# <a name="adding-a-property-to-the-control-atl-tutorial-part-3"></a>Dodawanie właściwości do kontrolki (ALT — Samouczek, część 3)

`IPolyCtl` interfejs, który zawiera kontrolki niestandardowe metody i właściwości, a właściwość spowoduje dodanie do niego.

### <a name="to-add-the-property-definitions-to-your-project"></a>Aby dodać definicji właściwości do projektu

1. W **Widok klas**, rozwiń węzeł `Polygon` gałęzi.

1. Kliknij prawym przyciskiem myszy `IPolyCtl`.

1. W menu skrótów kliknij **Dodaj**, a następnie kliknij przycisk **Dodaj właściwość**. **Dodaj właściwość** pojawi się Kreator.

1. Typ `Sides` jako **nazwa właściwości**.

1. Na liście rozwijanej **typ właściwości**, wybierz opcję `short`.

1. Kliknij przycisk **OK** aby zakończyć dodawanie właściwości.

1. Z **Eksploratora rozwiązań**, otwórz Polygon.idl i Zastąp następujące wiersze na końcu `IPolyCtl : IDispatch` interfejsu:

    ```cpp
    short get_Sides();
    void set_Sides(short value);
    ```

    with

    ```cpp
    [propget, id(1), helpstring("property Sides")] HRESULT Sides([out, retval] short *pVal);
    [propput, id(1), helpstring("property Sides")] HRESULT Sides([in] short newVal);
    ```

1. Z **Eksploratora rozwiązań**, otwórz PolyCtl.h i dodaj następujące wiersze po definicji `m_clrFillColor`:

    [!code-cpp[NVC_ATL_Windowing#44](../atl/codesnippet/cpp/adding-a-property-to-the-control-atl-tutorial-part-3_1.h)]

Mimo, że masz teraz szkielet funkcje do ustawiania i pobierania właściwości i zmienną do przechowywania właściwości, należy zaimplementować funkcje odpowiednio.

### <a name="to-update-the-get-and-put-methods"></a>Aby zaktualizować get i put metody

1. Ustaw wartość domyślną `m_nSides`. Ustaw jako domyślny, kształt trójkąta przez dodanie wiersza do konstruktora w PolyCtl.h:

    [!code-cpp[NVC_ATL_Windowing#45](../atl/codesnippet/cpp/adding-a-property-to-the-control-atl-tutorial-part-3_2.h)]

1. Implementowanie `Get` i `Put` metody. `get_Sides` i `put_Sides` deklaracje funkcji zostały dodane do PolyCtl.h. Teraz Dodaj kod dla `get_Sides` i `put_Sides` do PolyCtl.cpp następującym kodem:

    [!code-cpp[NVC_ATL_Windowing#46](../atl/codesnippet/cpp/adding-a-property-to-the-control-atl-tutorial-part-3_3.cpp)]

`get_Sides` Metoda zwraca bieżącą wartość `Sides` właściwości, za pośrednictwem `pVal` wskaźnika. W `put_Sides` użytkownika to ustawienie zapewnia kod metody `Sides` właściwość dozwolonej wartości. Minimalna muszą mieć od 3, a tablica punktów będzie używane dla każdej strony, 100 jest uzasadnione limit maksymalnej wartości.

Masz teraz właściwość o nazwie `Sides`. W następnym kroku zmienisz kod rysowania z niego korzystać.

[Wróć do kroku 2](../atl/adding-a-control-atl-tutorial-part-2.md) &#124; [do kroku 4](../atl/changing-the-drawing-code-atl-tutorial-part-4.md)

## <a name="see-also"></a>Zobacz także

[Samouczek](../atl/active-template-library-atl-tutorial.md)
