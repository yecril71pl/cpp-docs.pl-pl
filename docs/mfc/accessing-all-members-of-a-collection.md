---
title: Uzyskiwanie dostępu do wszystkich elementów członkowskich kolekcji
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, collections
- enumerations [MFC]
- enumerating collections [MFC]
- collections [MFC], accessing
- collection classes [MFC]
- ', '
- ', '
- ', '
- ', '
- ', '
- ', '
- ', '
ms.assetid: 7bbae518-062e-4393-81f9-b22abd2e5f59
ms.openlocfilehash: b6c79164bc1049f39ce0af4e00341df8f234b34a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50628816"
---
# <a name="accessing-all-members-of-a-collection"></a>Uzyskiwanie dostępu do wszystkich elementów członkowskich kolekcji

Klasy kolekcji tablic MFC — zarówno na podstawie szablonu i nie — indeksów użyć, aby uzyskać dostęp do swoich elementów. Klasy kolekcji list i map MFC — zarówno na podstawie szablonu i nie — użyj wskaźnika typu **pozycji** do opisania określonej pozycji w kolekcji. Aby uzyskać dostęp do co najmniej jeden członkowie tych kolekcji, należy najpierw zainicjować wskaźnik położenia wielokrotnie przekazania tej pozycji do kolekcji i poproś go, aby powrócić do następnego elementu. Kolekcja nie jest odpowiedzialna za informacje o stanie o postępie iteracji. Te informacje są przechowywane w wskaźnik położenia. Ale biorąc pod uwagę określonego stanowiska, Kolekcja jest odpowiedzialna za zwrócenie następnego elementu.

Poniższe procedury pokazują, jak wykonać iterację trzy główne typy kolekcji dostarczanych z MFC:

- [Iteracja tablicy](#_core_to_iterate_an_array)

- [Iteracja listy](#_core_to_iterate_a_list)

- [Iteracja mapy](#_core_to_iterate_a_map)

### <a name="_core_to_iterate_an_array"></a> Do iteracji tablicy

1. Użyj sekwencyjne numery indeksu za pomocą `GetAt` funkcja elementu członkowskiego:

   [!code-cpp[NVC_MFCCollections#12](../mfc/codesnippet/cpp/accessing-all-members-of-a-collection_1.cpp)]

   W tym przykładzie użyto tablicy typizowanych wskaźników, które zawierają wskaźniki do `CPerson` obiektów. Tablica jest pochodną klasy `CObArray`, jeden z nieszablonu wstępnie zdefiniowanych klas. `GetAt` Zwraca wskaźnik do `CPerson` obiektu. W przypadku klas kolekcji wpisane wskaźnika — tablice i listy — pierwszy parametr określa klasę bazową; drugi parametr określa typ przechowywania.

   `CTypedPtrArray` Również klasy przeciążenia **[** operator tak, aby można było używać zwyczajowego składni indeks dolny tablicy do dostępu do elementów tablicy. Alternatywa dla instrukcji w treści **dla** jest pętla powyżej

   [!code-cpp[NVC_MFCCollections#13](../mfc/codesnippet/cpp/accessing-all-members-of-a-collection_2.cpp)]

   Ten operator istnieje zarówno w **const** i innych niż-**const** wersji. **Const** wersji, która jest wywoływana dla **const** tablic, mogą być wyświetlane tylko po prawej stronie instrukcji przypisania.

### <a name="_core_to_iterate_a_list"></a> Aby przejść do listy

1. Użyj funkcji elementów członkowskich `GetHeadPosition` i `GetNext` do sposobu pracy użytkownika za pośrednictwem listy:

   [!code-cpp[NVC_MFCCollections#14](../mfc/codesnippet/cpp/accessing-all-members-of-a-collection_3.cpp)]

   W tym przykładzie użyto typizowanych wskaźników listy zawierają wskaźniki do `CPerson` obiektów. Deklaracja listy podobny dla tablicy w procedurze [do iteracji tablicy](#_core_to_iterate_an_array) , ale jest pochodną klasy `CObList`. `GetNext` Zwraca wskaźnik do `CPerson` obiektu.

### <a name="_core_to_iterate_a_map"></a> Iteracyjne mapy

1. Użyj `GetStartPosition` do początku mapy i `GetNextAssoc` wielokrotnie uzyskać dalej klucza i wartości z mapy, jak pokazano na poniższym przykładzie:

   [!code-cpp[NVC_MFCCollections#15](../mfc/codesnippet/cpp/accessing-all-members-of-a-collection_4.cpp)]

   W tym przykładzie użyto szablonu proste mapy (zamiast kolekcji wpisane wskaźnika), który używa `CString` kluczy i przechowuje wskaźniki do `CPerson` obiektów. Jeśli używasz funkcji dostępu, takich jak `GetNextAssoc`, klasa oferuje wskaźniki do `CPerson` obiektów. Jeśli używasz jednej z kolekcji mapy nieszablonu zamiast tego, należy rzutować zwracany `CObject` wskaźnika do wskaźnika do `CPerson`.

    > [!NOTE]
    >  W przypadku map nieszablonu, kompilator wymaga odwołania do `CObject` wskaźnika w ostatnim parametrze do `GetNextAssoc`. W danych wejściowych należy rzutować wskaźniki dla tego typu, jak pokazano w następnym przykładzie.

   Szablon rozwiązania jest prostszy i pomaga zapewnić lepsze bezpieczeństwo typów. Kod nieszablonu jest bardziej skomplikowane, jak pokazano poniżej:

   [!code-cpp[NVC_MFCCollections#16](../mfc/codesnippet/cpp/accessing-all-members-of-a-collection_5.cpp)]

Aby uzyskać więcej informacji, zobacz [usuwanie wszystkich obiektów z kolekcji CObject](../mfc/deleting-all-objects-in-a-cobject-collection.md).

## <a name="see-also"></a>Zobacz też

[Kolekcje](../mfc/collections.md)

