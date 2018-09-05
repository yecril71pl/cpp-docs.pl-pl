---
title: Dodawanie właściwości do kontrolki (ALT — samouczek, część 3) | Dokumentacja firmy Microsoft
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: f775fe34-103b-4f07-9999-400e987ee030
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f1e90da3fe44613b0c530e801d963eaddd9d783e
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43756911"
---
# <a name="adding-a-property-to-the-control-atl-tutorial-part-3"></a>Dodawanie właściwości do kontrolki (ALT — Samouczek, część 3)

`IPolyCtl` interfejs, który zawiera kontrolki niestandardowe metody i właściwości, a właściwość spowoduje dodanie do niego.

### <a name="to-add-a-property-using-the-add-property-wizard"></a>Aby dodać właściwość przy użyciu Kreatora dodawania właściwości

1. W widoku klas rozwiń gałąź wielokąta.

2. Kliknij prawym przyciskiem myszy IPolyCtl.

3. W menu skrótów kliknij **Dodaj**, a następnie kliknij przycisk **Dodaj właściwość**.

     Pojawi się Kreator dodawania właściwości.

4. Na liście rozwijanej typów właściwości, wybierz `SHORT`.

5. Typ *boki* jako **nazwy właściwości.**

6. Kliknij przycisk **Zakończ** aby zakończyć dodawanie właściwości.

Jeśli dodasz właściwość do interfejsu MIDL (program, który kompiluje pliki .idl) definiuje `Get` metodę pobierania jej wartość i `Put` metody do ustawiania nowych wartości. Te metody są nazywane przez dołączenie `put_` i `get_` nazwa właściwości.

Kreator dodawania właściwości dodaje niezbędne wiersze do pliku .idl. Dodaje także `Get` i `Put` funkcji prototypów do definicji klasy w PolyCtl.h i dodaje implementację pusty PolyCtl.cpp. Można to sprawdzić, otwierając PolyCtl.cpp i szukasz funkcji `get_Sides` i `put_Sides`.

Mimo, że masz teraz szkielet funkcje do ustawiania i pobierania właściwości, musi ona miejsce do przechowywania. Utworzy zmienną do przechowywania właściwości i w związku z tym aktualizacji funkcji.

#### <a name="to-create-a-variable-to-store-the-property-and-update-the-put-and-get-methods"></a>Aby utworzyć zmienną do przechowywania właściwości i aktualizowanie put i metodom get

1. W Eksploratorze rozwiązań Otwórz PolyCtl.h i Dodaj następujący wiersz po definicji `m_clrFillColor`:

     [!code-cpp[NVC_ATL_Windowing#44](../atl/codesnippet/cpp/adding-a-property-to-the-control-atl-tutorial-part-3_1.h)]

2. Ustaw wartość domyślną `m_nSides`. Ustaw jako domyślny, kształt trójkąta przez dodanie wiersza do konstruktora w PolyCtl.h:

     [!code-cpp[NVC_ATL_Windowing#45](../atl/codesnippet/cpp/adding-a-property-to-the-control-atl-tutorial-part-3_2.h)]

3. Implementowanie `Get` i `Put` metody. `get_Sides` i `put_Sides` deklaracje funkcji zostały dodane do PolyCtl.h. Zastąp kod w PolyCtl.cpp dla `get_Sides` i `put_Sides` następującym kodem:

     [!code-cpp[NVC_ATL_Windowing#46](../atl/codesnippet/cpp/adding-a-property-to-the-control-atl-tutorial-part-3_3.cpp)]

`get_Sides` Metoda zwraca bieżącą wartość `Sides` właściwości, za pośrednictwem `pVal` wskaźnika. W `put_Sides` użytkownika to ustawienie zapewnia kod metody `Sides` właściwość dozwolonej wartości. Minimalna muszą mieć od 3, a tablica punktów będzie używane dla każdej strony, 100 jest uzasadnione limit maksymalnej wartości.

Masz teraz właściwość o nazwie `Sides`. W następnym kroku zmienisz kod rysowania z niego korzystać.

[Wróć do kroku 2](../atl/adding-a-control-atl-tutorial-part-2.md) &#124; [do kroku 4](../atl/changing-the-drawing-code-atl-tutorial-part-4.md)

## <a name="see-also"></a>Zobacz też

[Samouczek](../atl/active-template-library-atl-tutorial.md)

