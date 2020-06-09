---
title: Kolekcje
ms.date: 11/04/2016
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
ms.openlocfilehash: f2cd03afbb09dff38298454658c3d3dc2dfa6a8a
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619347"
---
# <a name="collections"></a>Kolekcje

Biblioteka MFC zawiera klasy kolekcji do zarządzania grupami obiektów. Te klasy są dwa typy:

- [Klasy kolekcji utworzone na podstawie szablonów języka C++](#_core_the_template_based_collection_classes)

- [Klasy kolekcji nie zostały utworzone na podstawie szablonów](#_core_the_collection_classes_not_based_on_templates)

> [!NOTE]
> Jeśli kod używa już klas kolekcji nieszablonowych, można nadal z nich korzystać. Jeśli tworzysz nowe klasy kolekcji bezpiecznych dla typu danych, zalecamy użycie nowszych klas opartych na szablonach.

## <a name="collection-shapes"></a><a name="_core_collection_shapes"></a>Kształty kolekcji

Klasa kolekcji jest scharakteryzowana przy użyciu jej "Shape" i typów jej elementów. Kształt odwołuje się do sposobu, w jaki obiekty są zorganizowane i przechowywane w kolekcji. MFC oferuje trzy podstawowe kształty kolekcji: listy, tablice i mapy (znane również jako słowniki). Można wybrać kształt kolekcji, który jest najbardziej odpowiedni dla danego problemu programistycznego.

Każdy z trzech podanych kształtów kolekcji został krótko opisany w dalszej części tego tematu. Aby porównać funkcje kształtów, aby ułatwić podjęcie decyzji, która jest Najlepsza dla programu, zobacz [zalecenia dotyczące wybierania klasy kolekcji](recommendations-for-choosing-a-collection-class.md).

- Lista

   Klasa list zawiera uporządkowaną, nieindeksowaną listę elementów, zaimplementowaną jako połączoną listę. Lista zawiera "główne" i "ogon" oraz dodawanie lub usuwanie elementów z głowy lub ogona, lub wstawianie lub usuwanie elementów w środku, jest bardzo szybka.

- Tablica

   Klasa Array zapewnia dynamiczną, uporządkowaną i poindeksowaną tablicę obiektów.

- Mapa (znana także jako słownik)

   Mapa jest kolekcją, która kojarzy obiekt klucza z obiektem wartości.

## <a name="the-template-based-collection-classes"></a><a name="_core_the_template_based_collection_classes"></a>Klasy kolekcji opartej na szablonach

Najprostszym sposobem implementacji kolekcji bezpiecznej do typów, która zawiera obiekty dowolnego typu, jest użycie jednej z klas opartych na szablonie MFC. Aby zapoznać się z przykładami tych klas, zobacz [zbieranie](../overview/visual-cpp-samples.md)próbek MFC.

Poniższa tabela zawiera listę klas kolekcji opartych na szablonie MFC.

### <a name="collection-template-classes"></a>Klasy szablonu kolekcji

|Zawartość kolekcji|Tablice|Listy|Maps|
|-------------------------|------------|-----------|----------|
|Kolekcje obiektów dowolnego typu|`CArray`|`CList`|`CMap`|
|Kolekcje wskaźników do obiektów dowolnego typu|`CTypedPtrArray`|`CTypedPtrList`|`CTypedPtrMap`|

## <a name="the-collection-classes-not-based-on-templates"></a><a name="_core_the_collection_classes_not_based_on_templates"></a>Klasy kolekcji, które nie są oparte na szablonach

Jeśli aplikacja używa już klas MFC, można nadal z nich korzystać. Jednak w przypadku nowych kolekcji zalecamy korzystanie z klas opartych na szablonach. W poniższej tabeli wymieniono klasy kolekcji MFC, które nie są oparte na szablonach.

### <a name="nontemplate-collection-classes"></a>Klasy kolekcji nieszablonowych

|Tablice|Listy|Maps|
|------------|-----------|----------|
|`CObArray`|`CObList`|`CMapPtrToWord`|
|`CByteArray`|`CPtrList`|`CMapPtrToPtr`|
|`CDWordArray`|`CStringList`|`CMapStringToOb`|
|`CPtrArray`||`CMapStringToPtr`|
|`CStringArray`||`CMapStringToString`|
|`CWordArray`||`CMapWordToOb`|
|`CUIntArray`||`CMapWordToPtr`|

Charakterystyki tabeli klas kolekcji MFC w [zaleceniach dotyczących wybierania klasy kolekcji](recommendations-for-choosing-a-collection-class.md) opisują klasy kolekcji MFC pod względem tych cech (innych niż kształt):

- Czy Klasa używa szablonów języka C++

- Czy elementy przechowywane w kolekcji mogą być serializowane

- Czy elementy przechowywane w kolekcji mogą być zrzucane na potrzeby diagnostyki

- Czy kolekcja jest bezpieczna pod względem typu

### <a name="what-do-you-want-to-do"></a>Co chcesz zrobić

#### <a name="general-collection-class-tasks"></a>Ogólne zadania klasy kolekcji

- [Zalecenia dotyczące wybierania klasy kolekcji](recommendations-for-choosing-a-collection-class.md)

- [Instrukcje: tworzenie bezpiecznej kolekcji](how-to-make-a-type-safe-collection.md)

- [Tworzenie kolekcji stosów i kolejek](creating-stack-and-queue-collections.md)

- [CArray:: Add](reference/carray-class.md#add)

#### <a name="template-based-collection-class-tasks"></a>Zadania klasy kolekcji opartej na szablonach

- [Klasy oparte na szablonach](template-based-classes.md)

#### <a name="accessing-the-members-of-a-collection-template-based-or-not"></a>Uzyskiwanie dostępu do elementów członkowskich kolekcji (opartych na szablonie lub nie)

- [Uzyskiwanie dostępu do wszystkich elementów członkowskich kolekcji](accessing-all-members-of-a-collection.md)

- [Usuwanie wszystkich obiektów z kolekcji CObject](deleting-all-objects-in-a-cobject-collection.md)

## <a name="see-also"></a>Zobacz też

[Pojęcia](mfc-concepts.md)<br/>
[Tematy ogólne dotyczące MFC](general-mfc-topics.md)
