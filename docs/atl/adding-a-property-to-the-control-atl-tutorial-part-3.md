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
ms.openlocfilehash: fda9359da6ddc48248874227d58f0c184af45c54
ms.sourcegitcommit: 9b442b44ee912822d06cabec826aac4a8d82ec75
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2018
---
# <a name="adding-a-property-to-the-control-atl-tutorial-part-3"></a>Dodawanie właściwości do kontrolki (ALT — Samouczek, część 3)
`IPolyCtl` to interfejs, który zawiera kontrolki niestandardowe metody i właściwości, a właściwość spowoduje dodanie do niej.  
  
### <a name="to-add-a-property-using-the-add-property-wizard"></a>Aby dodać właściwość przy użyciu Kreatora dodawania właściwości  
  
1.  W widoku klas rozwiń gałąź wielokąta.  
  
2.  Kliknij prawym przyciskiem myszy IPolyCtl.  
  
3.  W menu skrótów kliknij **Dodaj**, a następnie kliknij przycisk **Dodaj właściwość**.  
  
     Pojawi się Kreator dodawania właściwości.  
  
4.  Na liście rozwijanej typów właściwości, wybierz `SHORT`.  
  
5.  Typ `Sides` jako **nazwy właściwości.**  
  
6.  Kliknij przycisk **Zakończ** aby zakończyć dodawanie właściwości.  
  
 Po dodaniu właściwości do interfejsu MIDL (program, który kompiluje pliki .idl) definiuje `Get` metodę pobierania jej wartość i `Put` metody określania nowej wartości. Te metody są nazywane dołączając `put_` i `get_` nazwę właściwości.  
  
 Kreator dodawania właściwości dodaje potrzebne wiersze do pliku .idl. Dodano również `Get` i `Put` funkcji prototypy do definicji klasy w PolyCtl.h i dodaje pustą implementację do PolyCtl.cpp. Można to sprawdzić, otwierając PolyCtl.cpp i wyszukiwanie funkcji `get_Sides` i `put_Sides`.  
  
 Mimo że masz teraz szkielet funkcje do ustawiania i pobierania właściwości, musi on miejsce do przechowywania. Utworzysz zmienną do przechowywania właściwości i odpowiednio aktualizacji funkcji.  
  
#### <a name="to-create-a-variable-to-store-the-property-and-update-the-put-and-get-methods"></a>Aby utworzyć zmienną do przechowywania właściwości i metody put aktualizacji i metodom get  
  
1.  W Eksploratorze rozwiązań Otwórz PolyCtl.h i Dodaj następujący wiersz po definicji `m_clrFillColor`:  
  
     [!code-cpp[NVC_ATL_Windowing#44](../atl/codesnippet/cpp/adding-a-property-to-the-control-atl-tutorial-part-3_1.h)]  
  
2.  Ustaw wartość domyślną `m_nSides`. Ustaw jako domyślny kształtu Trójkąt przez dodanie wiersza do konstruktora w PolyCtl.h:  
  
     [!code-cpp[NVC_ATL_Windowing#45](../atl/codesnippet/cpp/adding-a-property-to-the-control-atl-tutorial-part-3_2.h)]  
  
3.  Implementowanie `Get` i `Put` metody. `get_Sides` i `put_Sides` deklaracje funkcji zostały dodane do PolyCtl.h. Zastąp kod w PolyCtl.cpp dla `get_Sides` i `put_Sides` z następującym kodem:  
  
     [!code-cpp[NVC_ATL_Windowing#46](../atl/codesnippet/cpp/adding-a-property-to-the-control-atl-tutorial-part-3_3.cpp)]  
  
 `get_Sides` Metoda zwraca bieżącą wartość `Sides` właściwości za pośrednictwem `pVal` wskaźnika. W `put_Sides` użytkownika to ustawienie zapewnia kod metody `Sides` dozwolonej wartości dla właściwości. Wartość minimalna musi być 3, a ponieważ tablicę punktów będzie używany dla każdej strony, 100 jest uzasadnione limit wartości maksymalnej.  
  
 Istnieje już właściwość o nazwie `Sides`. W następnym kroku zostanie zmieniony kod rysowania z niego korzystać.  
  
 [Wróć do kroku 2](../atl/adding-a-control-atl-tutorial-part-2.md) &#124; [do kroku 4](../atl/changing-the-drawing-code-atl-tutorial-part-4.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Samouczek](../atl/active-template-library-atl-tutorial.md)

