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
ms.openlocfilehash: 53a4eb3e30048d9dc82722d912a026d63a87586d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371745"
---
# <a name="recommendations-for-choosing-a-collection-class"></a>Zalecenia dotyczące wybierania klasy kolekcji

Ten artykuł zawiera szczegółowe informacje mające na celu ułatwienie wyboru klasy kolekcji dla określonych potrzeb aplikacji.

Wybór klasy kolekcji zależy od wielu czynników, w tym:

- Cechy kształtu klasy: kolejność, indeksowanie i wydajność, jak pokazano w tabeli [Funkcje kształtu kolekcji](#_core_collection_shape_features) w dalszej części tego tematu

- Czy klasa używa szablonów języka C++

- Czy elementy przechowywane w kolekcji mogą być serializowane

- Czy elementy przechowywane w kolekcji mogą być po cenach dumpingowych do diagnostyki

- Czy kolekcja jest bezpieczna

W poniższej tabeli [funkcje kształtu kolekcji](#_core_collection_shape_features)podsumowano charakterystyki dostępnych kształtów kolekcji.

- Kolumny 2 i 3 opisują właściwości zamawiania i dostępu każdego kształtu. W tabeli termin "uporządkowany" oznacza, że kolejność wstawiania i usuwania towarów określa ich kolejność w kolekcji; nie oznacza to, że elementy są sortowane na ich zawartość. Termin "indeksowane" oznacza, że elementy w kolekcji mogą być pobierane przez indeks liczby całkowitej, podobnie jak elementy w typowej tablicy.

- Kolumny 4 i 5 opisują wydajność każdego kształtu. W aplikacjach, które wymagają wielu wstawień do kolekcji, szybkość wstawiania może być szczególnie ważne; w przypadku innych aplikacji szybkość wyszukiwania może być ważniejsza.

- Kolumna 6 opisuje, czy każdy kształt umożliwia zduplikowane elementy.

### <a name="collection-shape-features"></a><a name="_core_collection_shape_features"></a>Funkcje kształtu kolekcji

|Kształt|Zamówione|Indeksowane|Wstawianie elementu|Wyszukaj określony element|Duplikowane elementy|
|-----------|--------------|--------------|-----------------------|----------------------------------|-------------------------|
|List|Tak|Nie|Szybko|Powolny|Tak|
|Tablica|Tak|Przez int|Powolny|Powolny|Tak|
|Mapa|Nie|Według klucza|Szybko|Szybko|Nie (klucze) Tak (wartości)|

W [poniższej tabeli, Cechy klas kolekcji MFC](#_core_characteristics_of_mfc_collection_classes), podsumowuje inne ważne cechy określonych klas kolekcji MFC jako przewodnik do wyboru. Wybór może zależeć od tego, czy klasa jest oparta na szablonach C++, czy jej elementy mogą być serializowane za pomocą [mechanizmu serializacji](../mfc/serialization-in-mfc.md) dokumentów MFC, czy jego elementy mogą być po cenach dumpingowych za pośrednictwem mechanizmu dumpingu diagnostycznego MFC, czy klasa jest bezpieczna — to znaczy, czy można zagwarantować typ elementów przechowywanych i pobieranych z kolekcji na podstawie klasy.

### <a name="characteristics-of-mfc-collection-classes"></a><a name="_core_characteristics_of_mfc_collection_classes"></a>Charakterystyka klas kolekcji MFC

|Klasa|Używa języka C++<br /><br /> szablonów|Można<br /><br /> Szeregowane|Można<br /><br /> Po cenach dumpingowych|Is<br /><br /> bezpieczne dla typu|
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
|`CTypedPtrArray`|Tak|Zależy 2|Tak|Tak|
|`CTypedPtrList`|Tak|Zależy 2|Tak|Tak|
|`CTypedPtrMap`|Tak|Zależy 2|Tak|Tak|
|`CUIntArray`|Nie|Nie|Tak|Tak 3|
|`CWordArray`|Nie|Tak|Tak|Tak 3|

1. Aby serializować, należy jawnie wywołać `Serialize` funkcję obiektu kolekcji; do zrzutu, należy jawnie wywołać jego `Dump` funkcję. Nie można użyć `ar << collObj` formularza do serializacji lub zrzucenia formularza. `dmp` `<< collObj`

2. Serializability zależy od typu kolekcji podstawowej. Na przykład jeśli tablica wpisanego `CObArray`wskaźnika jest oparta na programie , jest serializable; jeśli opiera `CPtrArray`się na , nie jest serializable. Ogólnie rzecz biorąc nie można serializował klas "Ptr".

3. Jeśli zaznaczone tak w tej kolumnie, nontemplate collection klasy jest bezpieczny dla typu, pod warunkiem, że używasz go zgodnie z przeznaczeniem. Na przykład jeśli bajty są `CByteArray`przechowywane w , tablica jest bezpieczna dla typu. Ale jeśli używasz go do przechowywania znaków, jego bezpieczeństwo typu jest mniej pewne.

## <a name="see-also"></a>Zobacz też

[Kolekcje](../mfc/collections.md)<br/>
[Klasy oparte na szablonach](../mfc/template-based-classes.md)<br/>
[Instrukcje: tworzenie bezpiecznej kolekcji](../mfc/how-to-make-a-type-safe-collection.md)<br/>
[Uzyskiwanie dostępu do wszystkich elementów członkowskich kolekcji](../mfc/accessing-all-members-of-a-collection.md)
