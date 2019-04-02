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
ms.openlocfilehash: f3dea68deaae73313fe389be49e8bbed7da3c93a
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58767187"
---
# <a name="collections"></a>Kolekcje

Biblioteki klas Microsoft Foundation udostępnia klasy kolekcji do zarządzania grupami obiektów. Te klasy są dwa typy:

- [Klasy kolekcji utworzone na podstawie szablonów języka C++](#_core_the_template_based_collection_classes)

- [Klasy kolekcji, które nie są tworzone za pomocą szablonów](#_core_the_collection_classes_not_based_on_templates)

> [!NOTE]
>  Jeśli Twój kod używa już nieszablonu klasy kolekcji, można nadal z nich korzystać. Jeśli piszesz nowych klas kolekcji bezpieczny dla typów danych, zaleca się użycie nowszej klas na podstawie szablonu.

##  <a name="_core_collection_shapes"></a> Kształty kolekcji

Klasa kolekcji jest określony przez jego "kształt" i typów elementów. Kształt odnosi się do sposób obiekty są zorganizowane oraz przechowywane w kolekcji. Biblioteka MFC zawiera trzy kształty podstawowe kolekcji: list, tablic i map (znany także jako słowników). Możesz wybrać kształt kolekcji, która najbardziej nadaje się do konkretnego problemu programowania.

Każdy z trzech kształtów w określonej kolekcji opisano skrótowo w dalszej części tego tematu. Aby porównać funkcje kształty, aby pomóc w podjęciu decyzji, co jest najlepsze dla Twojego programu, zobacz [zalecenia dotyczące wybierania klasy kolekcji](../mfc/recommendations-for-choosing-a-collection-class.md).

- List

   Klasa listy udostępnia uporządkowana lista nieindeksowanych elementów, zaimplementowane jako podwójnie połączoną listą. Lista "head" i "tail" i jest bardzo szybkie dodawanie lub usuwanie elementów, head lub ogona, lub wstawiania lub usuwania elementów w środku.

- Tablica

   Array — klasa zawiera dynamicznie wielkości, uporządkowane i indeksowane całkowitą Tablica obiektów.

- Mapa (Słownik)

   Mapa jest kolekcja, która powoduje skojarzenie klucza obiektu z obiektu wartości.

##  <a name="_core_the_template_based_collection_classes"></a> Klasy kolekcji oparte na szablonach

Najłatwiejszym sposobem realizowania bezpiecznej kolekcji, który zawiera obiekty dowolnego typu jest użyć jednej z klas MFC na podstawie szablonu. Aby uzyskać przykłady tych klas, zobacz przykład MFC [ZBIERANIE](../overview/visual-cpp-samples.md).

W poniższej tabeli wymieniono klasy kolekcji oparte na szablonach MFC.

### <a name="collection-template-classes"></a>Kolekcja klas szablonów

|Zawartość kolekcji|Tablice|Listy|Maps|
|-------------------------|------------|-----------|----------|
|Kolekcje obiektów dowolnego typu|`CArray`|`CList`|`CMap`|
|Kolekcje wskaźników do obiektów dowolnego typu|`CTypedPtrArray`|`CTypedPtrList`|`CTypedPtrMap`|

##  <a name="_core_the_collection_classes_not_based_on_templates"></a> Klasy kolekcji nie są oparte na szablonach

Jeśli aplikacja już korzysta z klasy nieszablonu MFC, można nadal z nich korzystać. Dla nowych kolekcji, zalecamy użycie klas na podstawie szablonu. W poniższej tabeli wymieniono klasy kolekcji MFC, które nie są oparte na szablonach.

### <a name="nontemplate-collection-classes"></a>Klasy kolekcji nieszablonu

|Tablice|Listy|Maps|
|------------|-----------|----------|
|`CObArray`|`CObList`|`CMapPtrToWord`|
|`CByteArray`|`CPtrList`|`CMapPtrToPtr`|
|`CDWordArray`|`CStringList`|`CMapStringToOb`|
|`CPtrArray`||`CMapStringToPtr`|
|`CStringArray`||`CMapStringToString`|
|`CWordArray`||`CMapWordToOb`|
|`CUIntArray`||`CMapWordToPtr`|

Właściwości klasy kolekcji MFC tabelę [zalecenia dotyczące wybierania klasy kolekcji](../mfc/recommendations-for-choosing-a-collection-class.md) opisuje klasy kolekcji MFC pod względem tych cech (inne niż kształtu):

- Czy klasa korzysta z szablonów języka C++

- Czy można wykonywać serializację elementów zapisanych w kolekcji

- Czy elementów zapisanych w kolekcji mogą można utworzyć zrzutu diagnostyki

- Czy kolekcja jest bezpieczny

### <a name="what-do-you-want-to-do"></a>Co chcesz zrobić

#### <a name="general-collection-class-tasks"></a>Klasa kolekcji ogólnych zadań

- [Zalecenia dotyczące wybierania klasy kolekcji](../mfc/recommendations-for-choosing-a-collection-class.md)

- [Instrukcje: Tworzenie bezpiecznej kolekcji](../mfc/how-to-make-a-type-safe-collection.md)

- [Tworzenie kolekcji stosów i kolejek](../mfc/creating-stack-and-queue-collections.md)

- [CArray::Add](../mfc/reference/carray-class.md#add)

#### <a name="template-based-collection-class-tasks"></a>Klasy kolekcji oparte na szablonach zadania

- [Klasy oparte na szablonach](../mfc/template-based-classes.md)

#### <a name="accessing-the-members-of-a-collection-template-based-or-not"></a>Uzyskiwanie dostępu do elementów członkowskich kolekcji (oparte na szablonach lub nie)

- [Uzyskiwanie dostępu do wszystkich składowych kolekcji](../mfc/accessing-all-members-of-a-collection.md)

- [Usuwanie wszystkich obiektów z kolekcji CObject](../mfc/deleting-all-objects-in-a-cobject-collection.md)

## <a name="see-also"></a>Zobacz także

[Pojęcia](../mfc/mfc-concepts.md)<br/>
[Tematy ogólne dotyczące MFC](../mfc/general-mfc-topics.md)
