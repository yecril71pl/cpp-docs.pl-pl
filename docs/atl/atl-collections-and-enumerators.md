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
ms.openlocfilehash: 00265d3ce0f8ea867021500777d93991d245be47
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43204816"
---
# <a name="atl-collections-and-enumerators"></a>Kolekcje i wyliczenia ATL
Element `collection` jest obiektem COM, który udostępnia interfejs, który umożliwia dostęp do jednej grupy elementów danych (nieprzetworzone dane lub innych obiektów). Interfejs, który następuje standardy dla zapewnienia dostępu do grupy obiektów jest znany jako *kolekcji interfejs*.  
  
 Jako minimum, należy podać interfejsów kolekcji `Count` właściwość, która zwraca liczbę elementów w kolekcji, `Item` właściwość, która zwraca element z kolekcji, w oparciu o indeks, a `_NewEnum` właściwość, która zwraca Moduł wyliczający dla kolekcji. Opcjonalnie można podać interfejsów kolekcji `Add` i `Remove` metody umożliwiające elementy, które mają być wstawiane do lub usuwane z kolekcji, a `Clear` metodę, aby usunąć wszystkie elementy.  
  
 `enumerator` Jest obiektem COM, który udostępnia interfejs dla iteracji elementów w kolekcji. Interfejsy modułu wyliczającego zapewniają dostęp szeregowy do elementów kolekcji za pomocą czterech metod wymagane: `Next`, `Skip`, `Reset`, i `Clone`.  
  
 Dowiedz się więcej na temat interfejsy modułu wyliczającego, zapoznając się odwoływać się do zawartości takie jak [IEnumString](/windows/desktop/api/objidl/nn-objidl-ienumstring) interfejsu.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Klasy kolekcji i wyliczeń ATL](../atl/atl-collection-and-enumerator-classes.md)  
 Krótko opisano i udostępnia łącza do klas ATL, które pomoże Ci zaimplementować kolekcje i wyliczenia.  
  
 [Zasady projektowania interfejsów kolekcji i wyliczeń](../atl/design-principles-for-collection-and-enumerator-interfaces.md)  
 W tym artykule omówiono zasady projektowania za każdy typ interfejsu.  
  
 [Implementowanie kolekcji opartej na standardowej bibliotece C++](../atl/implementing-an-stl-based-collection.md)  
 Przykładem rozszerzonego przeprowadzi Cię przez implementację kolekcję na podstawie standardowej biblioteki języka C++.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [ATL](../atl/active-template-library-atl-concepts.md)  
 Zawiera łącza do tematów pojęciowych dotyczące programowania przy użyciu biblioteki Active Template Library.  
  
 [Przykładowe ATLCollections](../visual-cpp-samples.md)  
 Przykład demonstruje użycie `ICollectionOnSTLImpl` i `CComEnumOnSTL`i wykonania kopii niestandardowych zasad klas.  
  
## <a name="see-also"></a>Zobacz też  
 [Pojęcia](../atl/active-template-library-atl-concepts.md)

