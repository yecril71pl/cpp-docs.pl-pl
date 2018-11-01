---
title: Zalecenia dotyczące wybierania klasy kolekcji
ms.date: 11/04/2016
helpviewer_keywords:
- type safety of collection classes [MFC]
- collection classes [MFC], serialization
- collection classes [MFC], speed
- collection classes [MFC], type safety
- collection classes [MFC], choosing
- collection classes [MFC], functionality
- shapes, collection
- collection classes [MFC], template-based
- MFC collection classes [MFC], characteristics
- collection classes [MFC], about collection classes [MFC]
- serialization [MFC], collection classes
- collection classes [MFC], duplicates allowed
- collection classes [MFC], shapes
ms.assetid: a82188cd-443f-40d8-a244-edf292a53db4
ms.openlocfilehash: 2c8cb323feb44618909895a4ee536ad3b7832173
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50446738"
---
# <a name="recommendations-for-choosing-a-collection-class"></a>Zalecenia dotyczące wybierania klasy kolekcji

Ten artykuł zawiera szczegółowe informacje, które ułatwiają wybieranie klasy kolekcji do własnych potrzeb konkretnej aplikacji.

Wybór klasy kolekcji zależy od wielu czynników, takich jak:

- Funkcje kształt klasy: kolejność, indeksowania i wydajność, jak pokazano na [kolekcji elementów kształtu](#_core_collection_shape_features) tabeli w dalszej części tego tematu

- Czy klasa korzysta z szablonów języka C++

- Czy można wykonywać serializację elementów zapisanych w kolekcji

- Czy elementów zapisanych w kolekcji mogą można utworzyć zrzutu diagnostyki

- Czy kolekcja jest bezpieczny

Poniższa tabela [kolekcji elementów kształtu](#_core_collection_shape_features), znajduje się podsumowanie właściwości kształtów dostępnych kolekcji.

- Kolumny, 2 i 3 opisano każdego z kształtów, kolejność i dostęp do właściwości. W tabeli termin "uporządkowane" oznacza, że kolejność, w którym elementy są wstawiane i usuwane określa ich kolejność, w kolekcji; nie oznacza to, że elementy są sortowane według ich zawartości. Termin "indexed" oznacza, że elementy w kolekcji mogą być pobierane według indeksu liczba całkowita, podobnie jak elementy w tablicy typowy.

- Kolumny 4 i 5 opisują wydajność każdego z kształtów. W aplikacji, które wymagają wielu wstawień do kolekcji szybkości wstawiania może być szczególnie ważne; dla innych aplikacji szybkość wyszukiwania może być niezwykle ważne.

- Kolumna 6 opisuje, czy każdy kształt zezwala na zduplikowane elementy.

### <a name="_core_collection_shape_features"></a>  Kolekcja elementów kształtu

|Kształt|Uporządkowane|Indeksowane|Wstaw element|Wyszukiwanie określonego elementu|Zduplikowane elementy|
|-----------|--------------|--------------|-----------------------|----------------------------------|-------------------------|
|Lista|Tak|Nie|Szybka|Powolne|Tak|
|Tablica|Tak|Przez int|Powolne|Powolne|Tak|
|Mapy|Nie|Według klucza|Szybka|Szybka|Tak (wartości) (kluczy)|

Poniższa tabela [właściwości z kolekcji klas MFC](#_core_characteristics_of_mfc_collection_classes), znajduje się podsumowanie innych istotnych cech określonych klasy kolekcji MFC jako przewodnika do zaznaczenia. Wybór może zależeć od tego, czy klasa opiera się na szablonów języka C++, czy jego elementów może być Zserializowany za pośrednictwem dokumentu MCF [serializacji](../mfc/serialization-in-mfc.md) mechanizmu, czy jego elementy można utworzyć zrzutu za pomocą MFC użytkownika diagnostycznych zrzucanie mechanizmu, lub czy klasa jest bezpieczny — oznacza to, czy może zagwarantować typ elementów przechowywanych w i pobierane z kolekcji na podstawie klasy.

### <a name="_core_characteristics_of_mfc_collection_classes"></a>  Właściwości klasy kolekcji MFC

|Class|Używa języka C++<br /><br /> szablony|Może być<br /><br /> serializacji|Może być<br /><br /> Wykonano zrzutu|jest<br /><br /> bezpieczne|
|-----------|------------------------------|---------------------------|-----------------------|-----------------------|
|`CArray`|Tak|Tak 1|Tak 1|Nie|
|`CByteArray`|Nie|Tak|Tak|Tak 3|
|`CDWordArray`|Nie|Tak|Tak|Tak 3|
|`CList`|Tak|Tak 1|Tak 1|Nie|
|`CMap`|Tak|Tak 1|Tak 1|Nie|
|`CMapPtrToPtr`|Nie|Nie|Tak|Nie|
|`CMapPtrToWord`|Nie|Nie|Tak|Nie|
|`CMapStringToOb`|Nie|Tak|Tak|Nie|
|`CMapStringToPtr`|Nie|Nie|Tak|Nie|
|`CMapStringToString`|Nie|Tak|Tak|Tak 3|
|`CMapWordToOb`|Nie|Tak|Tak|Nie|
|`CMapWordToPtr`|Nie|Nie|Tak|Nie|
|`CObArray`|Nie|Tak|Tak|Nie|
|`CObList`|Nie|Tak|Tak|Nie|
|`CPtrArray`|Nie|Nie|Tak|Nie|
|`CPtrList`|Nie|Nie|Tak|Nie|
|`CStringArray`|Nie|Tak|Tak|Tak 3|
|`CStringList`|Nie|Tak|Tak|Tak 3|
|`CTypedPtrArray`|Tak|Zależy od 2|Tak|Tak|
|`CTypedPtrList`|Tak|Zależy od 2|Tak|Tak|
|`CTypedPtrMap`|Tak|Zależy od 2|Tak|Tak|
|`CUIntArray`|Nie|Nie|Tak|Tak 3|
|`CWordArray`|Nie|Tak|Tak|Tak 3|

1. Do serializacji, należy jawnie wywołać obiekt kolekcji `Serialize` funkcji; aby zrzutu, należy jawnie wywołać jej `Dump` funkcji. Nie można użyć formy `ar << collObj` do serializacji lub formularzu `dmp` `<< collObj` do zrzutu.

2. Uszeregowieniem zależy od bazowego typu kolekcji. Na przykład, jeśli tablica wpisane wskaźnika opiera się na `CObArray`, jest możliwy do serializacji; Jeśli na podstawie `CPtrArray`, nie jest możliwy do serializacji. Ogólnie rzecz biorąc nie można serializować klasy "Ptr".

3. Jeśli oznaczona tak, w tej kolumnie, klasy kolekcji nieszablonu jest bezpieczny, pod warunkiem używać zgodnie z oczekiwaniami. Na przykład, jeśli przechowujesz bajtów w `CByteArray`, tablica jest bezpieczny. Ale jeśli jest ona używana do przechowywania znaków, jego bezpieczeństwa typu jest mniej niektórych.

## <a name="see-also"></a>Zobacz też

[Kolekcje](../mfc/collections.md)<br/>
[Klasy oparte na szablonach](../mfc/template-based-classes.md)<br/>
[Instrukcje: tworzenie bezpiecznej kolekcji](../mfc/how-to-make-a-type-safe-collection.md)<br/>
[Uzyskiwanie dostępu do wszystkich składowych kolekcji](../mfc/accessing-all-members-of-a-collection.md)

