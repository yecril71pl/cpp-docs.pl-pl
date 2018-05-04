---
title: Kolekcje i wyliczenia ATL | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- enumerator interfaces
- collections, ATL classes
- enumerators, ATL classes
- collection interfaces
ms.assetid: b2d37119-3ab2-4e0a-b65b-f377f07e4098
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 537d7e8b7264beddc68805ab8b8dec2ce7883859
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="atl-collections-and-enumerators"></a>Kolekcje i wyliczenia ATL
A `collection` jest obiekt COM, który udostępnia interfejs, który zezwala na dostęp do grupy elementów danych (nieprzetworzone dane lub inne obiekty). Interfejs, który wykonuje normy dla dostępowi do grupy obiektów nosi nazwę *interfejs kolekcji*.  
  
 Co najmniej podać interfejsy kolekcji **liczba** właściwość, która zwraca liczbę elementów w kolekcji, **elementu** właściwości, która zwraca element z kolekcji oparte na indeks, a `_NewEnum` właściwość, która zwraca moduł wyliczający dla kolekcji. Opcjonalnie można podać interfejsy kolekcji **Dodaj** i **Usuń** metody umożliwiające elementów do wstawienia do lub usunięty z kolekcji, a **wyczyść** metody do usunięcia wszystkie elementy.  
  
 `enumerator` Jest obiekt COM, który udostępnia interfejs dla iteracji elementów w kolekcji. Interfejsy modułu wyliczającego zapewniają dostęp szeregowy do elementów kolekcji za pomocą czterech metod wymagane: `Next`, **Pomiń**, **zresetować**, i `Clone`.  
  
 Użytkownik może dowiedzieć się więcej o interfejsy modułu wyliczającego przez informacji o archetypal (ale całkowicie urojony) [IEnumXXXX](https://msdn.microsoft.com/library/ms680089.aspx) interfejsu.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Klasy kolekcji i wyliczeń ATL](../atl/atl-collection-and-enumerator-classes.md)  
 Krótko opisano oraz zawiera łącza do klasy ATL, które pomogą Ci implementować kolekcje i wyliczenia.  
  
 [Zasady projektowania interfejsów kolekcji i wyliczeń](../atl/design-principles-for-collection-and-enumerator-interfaces.md)  
 W tym artykule omówiono zasady projektowania za każdego typu interfejsu.  
  
 [Implementowanie kolekcji opartej na standardowej bibliotece C++](../atl/implementing-an-stl-based-collection.md)  
 Przykład rozszerzonej, który przeprowadzi Cię przez implementację kolekcji na podstawie standardowa biblioteka C++.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [ATL](../atl/active-template-library-atl-concepts.md)  
 Zawiera łącza do tematów koncepcyjne na temat programowania przy użyciu biblioteki Active Template Library.  
  
 [Przykładowe ATLCollections](../visual-cpp-samples.md)  
 Przykład przedstawiający użycie `ICollectionOnSTLImpl` i `CComEnumOnSTL`i implementację klasy zasady niestandardowe kopiowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Pojęcia](../atl/active-template-library-atl-concepts.md)

