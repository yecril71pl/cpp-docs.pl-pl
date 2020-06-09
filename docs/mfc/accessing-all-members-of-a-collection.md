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
ms.openlocfilehash: 0d8b5491ee5321171ef358308f3c1548e43953d3
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616493"
---
# <a name="accessing-all-members-of-a-collection"></a>Uzyskiwanie dostępu do wszystkich elementów członkowskich kolekcji

Klasy kolekcji tablic MFC — oparte na szablonach i nie — używają indeksów, aby uzyskiwać dostęp do ich elementów. Lista MFC i klasy kolekcji mapy — oparte na szablonach, a nie — Użyj wskaźnika typu **pozycja** , aby opisać daną pozycję w kolekcji. Aby uzyskać dostęp do co najmniej jednego elementu członkowskiego tych kolekcji, należy najpierw zainicjować wskaźnik położenia, a następnie wielokrotnie przekazać tę pozycję do kolekcji i poproszony o zwrócenie następnego elementu. Kolekcja nie jest odpowiedzialna za utrzymanie informacji o stanie postępu iteracji. Te informacje są przechowywane w wskaźniku położenia. Jednak w przypadku konkretnego położenia kolekcja jest odpowiedzialna za zwracanie następnego elementu.

W poniższych procedurach pokazano, jak wykonać iterację trzech głównych typów kolekcji dostarczonych z MFC:

- [Iterowanie tablicy](#_core_to_iterate_an_array)

- [Iterowanie listy](#_core_to_iterate_a_list)

- [Iterowanie mapy](#_core_to_iterate_a_map)

### <a name="to-iterate-an-array"></a><a name="_core_to_iterate_an_array"></a>Aby wykonać iterację tablicy

1. Użyj numerów sekwencyjnych indeksów z `GetAt` funkcją składową:

   [!code-cpp[NVC_MFCCollections#12](codesnippet/cpp/accessing-all-members-of-a-collection_1.cpp)]

   W tym przykładzie używa tablicy wskaźników typu, która zawiera wskaźniki do `CPerson` obiektów. Tablica pochodzi od klasy `CObArray` , jednej z wstępnie zdefiniowanych klas. `GetAt`Zwraca wskaźnik do `CPerson` obiektu. Dla klas kolekcji wskaźników wpisanych — tablice lub listy — pierwszy parametr określa klasę bazową; drugi parametr określa typ do zapisania.

   `CTypedPtrArray`Klasa przeciąża również operator **[]** , aby można było użyć niestandardowej składni indeksu tablicy w celu uzyskania dostępu do elementów tablicy. Alternatywą dla instrukcji w treści pętli **for** jest

   [!code-cpp[NVC_MFCCollections#13](codesnippet/cpp/accessing-all-members-of-a-collection_2.cpp)]

   Ten operator istnieje w wersjach **const** i non-**const** . Wersja **stałej** , która jest wywoływana dla tablic **stałych** , może występować tylko po prawej stronie instrukcji przypisania.

### <a name="to-iterate-a-list"></a><a name="_core_to_iterate_a_list"></a>Aby wykonać iterację listy

1. Użyj funkcji składowych `GetHeadPosition` i `GetNext` w celu przechodzenia przez listę:

   [!code-cpp[NVC_MFCCollections#14](codesnippet/cpp/accessing-all-members-of-a-collection_3.cpp)]

   Ten przykład używa listy wskaźników z określonym typem, aby zawierać wskaźniki do `CPerson` obiektów. Deklaracja listy jest podobna do tej dla tablicy w procedurze [do iteracji tablicy](#_core_to_iterate_an_array) , ale pochodzi od klasy `CObList` . `GetNext`Zwraca wskaźnik do `CPerson` obiektu.

### <a name="to-iterate-a-map"></a><a name="_core_to_iterate_a_map"></a>Aby wykonać iterację mapy

1. Użyj, `GetStartPosition` Aby przejść do początku mapy i `GetNextAssoc` wielokrotnie uzyskać następny klucz i wartość z mapy, jak pokazano na poniższym przykładzie:

   [!code-cpp[NVC_MFCCollections#15](codesnippet/cpp/accessing-all-members-of-a-collection_4.cpp)]

   W tym przykładzie zastosowano prosty szablon mapy (a nie kolekcja wskaźników typu), który używa `CString` kluczy i przechowuje wskaźniki do `CPerson` obiektów. W przypadku korzystania z funkcji dostępu, takich jak `GetNextAssoc` , Klasa dostarcza wskaźników do `CPerson` obiektów. Jeśli zamiast tego używasz jednej z kolekcji map nieszablonowych, musisz rzutować zwracany `CObject` wskaźnik na wskaźnik do `CPerson` .

    > [!NOTE]
    >  W przypadku map nieszablonowych kompilator wymaga odwołania do `CObject` wskaźnika w ostatnim parametrze do `GetNextAssoc` . Na wejściu należy rzutować wskaźniki do tego typu, jak pokazano w następnym przykładzie.

   Rozwiązanie szablonu jest prostsze i zapewnia lepsze bezpieczeństwo typów. Kod nieszablonowy jest bardziej skomplikowany, jak widać tutaj:

   [!code-cpp[NVC_MFCCollections#16](codesnippet/cpp/accessing-all-members-of-a-collection_5.cpp)]

Aby uzyskać więcej informacji, zobacz [usuwanie wszystkich obiektów w kolekcji CObject](deleting-all-objects-in-a-cobject-collection.md).

## <a name="see-also"></a>Zobacz też

[Kolekcje](collections.md)
