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
ms.openlocfilehash: 3fba3a3c6cd3fecbda7f46575b1d72c450c44019
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361868"
---
# <a name="collections"></a>Kolekcje

Biblioteka klas programu Microsoft Foundation udostępnia klasy kolekcji do zarządzania grupami obiektów. Klasy te są dwojaki:

- [Klasy kolekcji utworzone na podstawie szablonów języka C++](#_core_the_template_based_collection_classes)

- [Klasy kolekcji nie utworzone z szablonów](#_core_the_collection_classes_not_based_on_templates)

> [!NOTE]
> Jeśli kod już używa klas kolekcji nontemplate, można nadal z nich korzystać. Jeśli piszesz nowe klasy kolekcji bezpieczne dla własnych typów danych, zaleca się użycie nowszych klas opartych na szablonie.

## <a name="collection-shapes"></a><a name="_core_collection_shapes"></a>Kształty kolekcji

Klasa kolekcji charakteryzuje się "kształtem" i rodzajami jej elementów. Kształt odnosi się do sposobu, w jaki obiekty są zorganizowane i przechowywane przez kolekcję. MFC zawiera trzy podstawowe kształty kolekcji: listy, tablice i mapy (znane również jako słowniki). Można wybrać kształt kolekcji, który jest najbardziej odpowiedni do konkretnego problemu programowania.

Każdy z trzech dostarczonych kształtów kolekcji jest opisany krótko w dalszej części tego tematu. Aby porównać cechy kształtów, które pomogą Ci zdecydować, który program jest najlepszy dla programu, zobacz [Zalecenia dotyczące wybierania klasy kolekcji](../mfc/recommendations-for-choosing-a-collection-class.md).

- List

   Klasa listy zawiera uporządkowaną, nieindeksowana listę elementów, zaimplementowana jako podwójnie połączona lista. Lista ma "głowę" i "ogon", a dodawanie lub usuwanie elementów z głowy lub ogona lub wstawianie lub usuwanie elementów w środku jest bardzo szybkie.

- Tablica

   Klasa tablicy zapewnia dynamicznie dobraną, uporządkowaną i indeksowany numer całkowity tablicę obiektów.

- Mapa (znana również jako słownik)

   Mapa to kolekcja, która kojarzy obiekt klucza z obiektem wartości.

## <a name="the-template-based-collection-classes"></a><a name="_core_the_template_based_collection_classes"></a>Klasy kolekcji oparte na szablonach

Najprostszym sposobem zaimplementowania kolekcji bezpieczne typu, która zawiera obiekty dowolnego typu jest użycie jednej z klas opartych na szablonie MFC. Przykłady tych klas można znaleźć w przykładzie MFC [COLLECT](../overview/visual-cpp-samples.md).

W poniższej tabeli wymieniono klasy kolekcji oparte na szablonie MFC.

### <a name="collection-template-classes"></a>Klasy szablonów kolekcji

|Zawartość kolekcji|Tablice|Listy|Maps|
|-------------------------|------------|-----------|----------|
|Kolekcje obiektów dowolnego typu|`CArray`|`CList`|`CMap`|
|Kolekcje wskaźników do obiektów dowolnego typu|`CTypedPtrArray`|`CTypedPtrList`|`CTypedPtrMap`|

## <a name="the-collection-classes-not-based-on-templates"></a><a name="_core_the_collection_classes_not_based_on_templates"></a>Klasy kolekcji nie oparte na szablonach

Jeśli aplikacja już używa klas niepamiętnych MFC, można nadal z nich korzystać. Jednak dla nowych kolekcji zaleca się użycie klas opartych na szablonie. W poniższej tabeli wymieniono klasy kolekcji MFC, które nie są oparte na szablonach.

### <a name="nontemplate-collection-classes"></a>Klasy kolekcji nontemplate

|Tablice|Listy|Maps|
|------------|-----------|----------|
|`CObArray`|`CObList`|`CMapPtrToWord`|
|`CByteArray`|`CPtrList`|`CMapPtrToPtr`|
|`CDWordArray`|`CStringList`|`CMapStringToOb`|
|`CPtrArray`||`CMapStringToPtr`|
|`CStringArray`||`CMapStringToString`|
|`CWordArray`||`CMapWordToOb`|
|`CUIntArray`||`CMapWordToPtr`|

Charakterystyka MFC Kolekcji klasy tabeli w [zalecenia dotyczące wyboru klasy kolekcji](../mfc/recommendations-for-choosing-a-collection-class.md) opisuje klasy kolekcji MFC pod względem tych cech (innych niż kształt):

- Czy klasa używa szablonów języka C++

- Czy elementy przechowywane w kolekcji mogą być serializowane

- Czy elementy przechowywane w kolekcji mogą być po cenach dumpingowych do diagnostyki

- Czy kolekcja jest bezpieczna

### <a name="what-do-you-want-to-do"></a>Co chcesz zrobić

#### <a name="general-collection-class-tasks"></a>Zadania klasy kolekcji ogólnej

- [Zalecenia dotyczące wybierania klasy kolekcji](../mfc/recommendations-for-choosing-a-collection-class.md)

- [Instrukcje: tworzenie bezpiecznej kolekcji](../mfc/how-to-make-a-type-safe-collection.md)

- [Tworzenie kolekcji stosów i kolejek](../mfc/creating-stack-and-queue-collections.md)

- [CArray::Dodaj](../mfc/reference/carray-class.md#add)

#### <a name="template-based-collection-class-tasks"></a>Zadania klasy kolekcji oparte na szablonie

- [Klasy oparte na szablonach](../mfc/template-based-classes.md)

#### <a name="accessing-the-members-of-a-collection-template-based-or-not"></a>Uzyskiwanie dostępu do członków kolekcji (oparte na szablonach lub nie)

- [Uzyskiwanie dostępu do wszystkich elementów członkowskich kolekcji](../mfc/accessing-all-members-of-a-collection.md)

- [Usuwanie wszystkich obiektów z kolekcji CObject](../mfc/deleting-all-objects-in-a-cobject-collection.md)

## <a name="see-also"></a>Zobacz też

[Pojęcia](../mfc/mfc-concepts.md)<br/>
[Tematy ogólne dotyczące MFC](../mfc/general-mfc-topics.md)
