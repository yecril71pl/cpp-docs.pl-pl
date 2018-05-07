---
title: Kolekcje | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC, collections
- arrays [MFC], classes
- MFC collection classes
- shapes, collection
- collection classes [MFC], MFC
- collections, about collections
- array templates [MFC]
- collection classes [MFC], template-based
- collection classes [MFC], about collection classes
- collection classes [MFC], maps
- collection classes [MFC], arrays
- shapes
- collection classes [MFC], lists
- collection classes [MFC], shapes
ms.assetid: 02586e4c-851d-41d0-a722-feb11c17c74c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: beae5370c86bf0142b29f029778083f3042ae931
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="collections"></a>Kolekcje
Microsoft Foundation Class Library zawiera klasy kolekcji do zarządzania grupami obiektów. Te klasy istnieją dwa typy:  
  
-   [Klasy kolekcji utworzone na podstawie szablonów języka C++](#_core_the_template_based_collection_classes)  
  
-   [Klasy kolekcji, które nie są tworzone za pomocą szablonów](#_core_the_collection_classes_not_based_on_templates)  
  
> [!NOTE]
>  Jeśli kod używa już nieszablonu klasy kolekcji, można nadal z nich korzystać. Jeśli piszesz nowe klasy bezpiecznej kolekcji dla typów danych, zalecane jest użycie nowszej klasy oparte na szablonach.  
  
##  <a name="_core_collection_shapes"></a> Kolekcja kształtów  
 Klasy kolekcji jest określony przez jego "kształtu" i typów elementów. Kształt odwołuje się do sposób obiekty są zorganizowane i przechowywane w kolekcji. MFC udostępnia trzy podstawowe kolekcji kształtów: list, stałych i map (znanej także jako słowniki). Można wybrać kształtu kolekcji, który jest najbardziej nadaje się do konkretnego problemu programowania.  
  
 Krótko później w tym temacie opisano każdego z trzech kształtów w określonej kolekcji. Aby porównać funkcje kształtów, aby określić, która jest najbardziej przydatna w przypadku programu, zobacz [zalecenia dotyczące wybierania klasy kolekcji](../mfc/recommendations-for-choosing-a-collection-class.md).  
  
-   Lista  
  
     Klasy list zawiera uporządkowana lista nieindeksowanych elementy zaimplementowane jako podwójnie połączonej listy. Lista "head" i "fragmentu" i dodawanie lub usuwanie elementów z head lub fragmentu, lub wstawiania lub usuwania elementów w środku, jest bardzo szybko.  
  
-   Tablica  
  
     Klasa tablicy udostępnia dynamicznie rozmiarze, uporządkowanej i indeksowane całkowitą Tablica obiektów.  
  
-   Mapy (słowniku)  
  
     Mapy jest kolekcją, które kojarzy z obiektem wartości klucza obiektu.  
  
##  <a name="_core_the_template_based_collection_classes"></a> Klasy kolekcji oparte na szablonach  
 Najprostszym sposobem wykonania bezpiecznej kolekcji, który zawiera obiekty dowolnego typu jest użycia jednej z klas MFC na podstawie szablonu. Przykłady tych klas, zobacz przykład MFC [ZBIERANIE](../visual-cpp-samples.md).  
  
 W poniższej tabeli wymieniono klasy kolekcji oparte na szablonach MFC.  
  
### <a name="collection-template-classes"></a>Kolekcja klas szablonów  
  
|Zawartość kolekcji|Tablice|Listy|Mapy|  
|-------------------------|------------|-----------|----------|  
|Kolekcje obiektów dowolnego typu|`CArray`|`CList`|`CMap`|  
|Kolekcje wskaźników do obiektów dowolnego typu|`CTypedPtrArray`|`CTypedPtrList`|`CTypedPtrMap`|  
  
##  <a name="_core_the_collection_classes_not_based_on_templates"></a> Klasy kolekcji nie są oparte na szablonach  
 Jeśli aplikacja już używa klasy nieszablonu MFC, można nadal z nich korzystać. Dla nowych kolekcji, zalecamy użycie klasy oparte na szablonach. W poniższej tabeli wymieniono klasy kolekcji MFC, które nie są oparte na szablonach.  
  
### <a name="nontemplate-collection-classes"></a>Klasy kolekcji nieszablonu  
  
|Tablice|Listy|Mapy|  
|------------|-----------|----------|  
|`CObArray`|`CObList`|`CMapPtrToWord`|  
|`CByteArray`|`CPtrList`|`CMapPtrToPtr`|  
|`CDWordArray`|`CStringList`|`CMapStringToOb`|  
|`CPtrArray`||`CMapStringToPtr`|  
|`CStringArray`||`CMapStringToString`|  
|`CWordArray`||`CMapWordToOb`|  
|`CUIntArray`||`CMapWordToPtr`|  
  
 W tabeli właściwości klasy kolekcji MFC [zalecenia dotyczące wybierania klasy kolekcji](../mfc/recommendations-for-choosing-a-collection-class.md) opisano klasy kolekcji MFC pod względem tych właściwości (inne niż kształt):  
  
-   Określa, czy klasa korzysta z szablonów języka C++  
  
-   Określa, czy może być Zserializowany elementy przechowywane w kolekcji  
  
-   Określa, czy elementy przechowywane w kolekcji można można utworzyć zrzutu diagnostyki  
  
-   Określa, czy kolekcja jest bezpieczne  
  
### <a name="what-do-you-want-to-do"></a>Co chcesz zrobić  
  
#### <a name="general-collection-class-tasks"></a>Klasa kolekcji ogólnych zadań  
  
-   [Zalecenia dotyczące wybierania klasy kolekcji](../mfc/recommendations-for-choosing-a-collection-class.md)  
  
-   [Instrukcje: tworzenie bezpiecznej kolekcji](../mfc/how-to-make-a-type-safe-collection.md)  
  
-   [Tworzenie kolekcji stosów i kolejek](../mfc/creating-stack-and-queue-collections.md)  
  
-   [CArray::Add](../mfc/reference/carray-class.md#add)  
  
#### <a name="template-based-collection-class-tasks"></a>Klasy kolekcji oparte na szablonach zadań  
  
-   [Klasy oparte na szablonach](../mfc/template-based-classes.md)  
  
#### <a name="accessing-the-members-of-a-collection-template-based-or-not"></a>Uzyskiwanie dostępu do elementów członkowskich kolekcji (na podstawie szablonu lub nie)  
  
-   [Uzyskiwanie dostępu do wszystkich składowych kolekcji](../mfc/accessing-all-members-of-a-collection.md)  
  
-   [Usuwanie wszystkich obiektów z kolekcji CObject](../mfc/deleting-all-objects-in-a-cobject-collection.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Pojęcia](../mfc/mfc-concepts.md)   
 [Tematy ogólne dotyczące MFC](../mfc/general-mfc-topics.md)

