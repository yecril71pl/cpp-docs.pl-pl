---
title: Dodawanie właściwości do kontrolki (ALT — Samouczek, część 3)
ms.custom: get-started-article
ms.date: 09/26/2018
ms.assetid: f775fe34-103b-4f07-9999-400e987ee030
ms.openlocfilehash: 288dc9f5af57c02639d15a9a971419a633cfc08d
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127590"
---
# <a name="adding-a-property-to-the-control-atl-tutorial-part-3"></a>Dodawanie właściwości do kontrolki (ALT — Samouczek, część 3)

`IPolyCtl` to interfejs, który zawiera niestandardowe metody i właściwości kontrolki, i doda do niej właściwość.

### <a name="to-add-the-property-definitions-to-your-project"></a>Aby dodać definicje właściwości do projektu

1. W **Widok klasy**rozwiń gałąź `Polygon`.

1. Kliknij prawym przyciskiem myszy `IPolyCtl`.

1. W menu skrótów kliknij polecenie **Dodaj**, a następnie kliknij przycisk **Dodaj właściwość**. Zostanie wyświetlony Kreator **dodawania właściwości** .

1. Wpisz `Sides` jako **nazwę właściwości**.

1. Z listy rozwijanej **Typ właściwości**wybierz pozycję `short`.

1. Kliknij przycisk **OK** , aby zakończyć dodawanie właściwości.

1. Z **Eksplorator rozwiązań**Otwórz wielokąt. idl i zastąp następujące wiersze na końcu interfejsu `IPolyCtl : IDispatch`:

    ```cpp
    short get_Sides();
    void set_Sides(short value);
    ```

    elementem

    ```cpp
    [propget, id(1), helpstring("property Sides")] HRESULT Sides([out, retval] short *pVal);
    [propput, id(1), helpstring("property Sides")] HRESULT Sides([in] short newVal);
    ```

1. W **Eksplorator rozwiązań**Otwórz plik PolyCtl. h i Dodaj następujące wiersze po definicji `m_clrFillColor`:

    [!code-cpp[NVC_ATL_Windowing#44](../atl/codesnippet/cpp/adding-a-property-to-the-control-atl-tutorial-part-3_1.h)]

Mimo że masz teraz funkcje szkieletowe, aby ustawić i pobrać właściwość oraz zmienną do przechowywania właściwości, należy odpowiednio zaimplementować funkcje.

### <a name="to-update-the-get-and-put-methods"></a>Aby zaktualizować metody get i Put

1. Ustaw wartość domyślną `m_nSides`. Ustaw domyślny kształt trójkąta poprzez dodanie linii do konstruktora w PolyCtl. h:

    [!code-cpp[NVC_ATL_Windowing#45](../atl/codesnippet/cpp/adding-a-property-to-the-control-atl-tutorial-part-3_2.h)]

1. Zaimplementuj metody `Get` i `Put`. Deklaracje funkcji `get_Sides` i `put_Sides` zostały dodane do PolyCtl. h. Teraz Dodaj kod dla `get_Sides` i `put_Sides` do PolyCtl. cpp z następującymi czynnościami:

    [!code-cpp[NVC_ATL_Windowing#46](../atl/codesnippet/cpp/adding-a-property-to-the-control-atl-tutorial-part-3_3.cpp)]

Metoda `get_Sides` zwraca bieżącą wartość właściwości `Sides` za pomocą wskaźnika `pVal`. W metodzie `put_Sides`, kod gwarantuje, że użytkownik ustawia właściwość `Sides` na akceptowalną wartość. Minimalna wartość musi być równa 3, a ponieważ dla każdej strony zostanie użyta tablica punktów, 100 to rozsądny limit wartości maksymalnej.

Masz teraz właściwość o nazwie `Sides`. W następnym kroku zmienisz kod rysowania, aby go używać.

[Wróć do kroku 2](../atl/adding-a-control-atl-tutorial-part-2.md) &#124; [w kroku 4](../atl/changing-the-drawing-code-atl-tutorial-part-4.md)

## <a name="see-also"></a>Zobacz też

[Samouczek](../atl/active-template-library-atl-tutorial.md)
