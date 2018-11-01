---
title: 'Porady: tworzenie bezpiecznej kolekcji'
ms.date: 11/04/2016
helpviewer_keywords:
- type-safe collections [MFC]
- serializing collection-class elements [MFC]
- collection classes [MFC], type safety
- SerializeElements function [MFC]
- collection classes [MFC], template-based
- serialization [MFC], collection classes
- collection classes [MFC], deriving from nontemplate
ms.assetid: 7230b2db-4283-4083-b098-eb231bf5b89e
ms.openlocfilehash: 12ecec7562a9241fab30b859727a22e467e6eeb0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50581795"
---
# <a name="how-to-make-a-type-safe-collection"></a>Porady: tworzenie bezpiecznej kolekcji

W tym artykule wyjaśniono, jak tworzyć kolekcje bezpieczny dla typów danych. Tematy obejmują:

- [Przy użyciu klas na podstawie szablonu dla zabezpieczeń typów](#_core_using_template.2d.based_classes_for_type_safety)

- [Implementowanie funkcji pomocnika](#_core_implementing_helper_functions)

- [Używanie klas kolekcji nieszablonu](#_core_using_nontemplate_collection_classes)

Biblioteki klas Microsoft Foundation udostępnia wstępnie zdefiniowane bezpieczne kolekcje na podstawie szablonów języka C++. Ponieważ są one szablonów, w ramach tych zajęć pomagają zapewnić bezpieczeństwo typów i łatwość użycia bez rzutowania typu i inne dodatkowe prace związane ze stosowaniem klasy nieszablonu w tym celu. Próbki MFC [ZBIERANIE](../visual-cpp-samples.md) demonstruje użycie klasy kolekcji oparte na szablonach, które w aplikacji MFC. Ogólnie rzecz biorąc Użyj tych klas za każdym razem, gdy piszesz nowy kod kolekcji.

##  <a name="_core_using_template.2d.based_classes_for_type_safety"></a> Przy użyciu klas na podstawie szablonu dla zabezpieczeń typów

#### <a name="to-use-template-based-classes"></a>Aby użyć klasy oparte na szablonach

1. Zadeklaruj zmienną typu klas kolekcji. Na przykład:

   [!code-cpp[NVC_MFCCollections#7](../mfc/codesnippet/cpp/how-to-make-a-type-safe-collection_1.cpp)]

1. Wywołaj element członkowski funkcji obiektu kolekcji. Na przykład:

   [!code-cpp[NVC_MFCCollections#8](../mfc/codesnippet/cpp/how-to-make-a-type-safe-collection_2.cpp)]

1. Jeśli to konieczne, należy zaimplementować [funkcji pomocnika](../mfc/reference/collection-class-helpers.md) i [serializeelements —](../mfc/reference/collection-class-helpers.md#serializeelements). Aby uzyskać informacji dotyczących implementowania tych funkcji, zobacz [implementowania funkcji pomocnika](#_core_implementing_helper_functions).

Ten przykład przedstawia deklarację elementu na liście liczb całkowitych. Pierwszy parametr w kroku 1 jest typ danych przechowywanych jako elementy listy. Drugi parametr określa, jak dane są przekazywane do i zwracane przez funkcje Członkowskie klasy kolekcji, takie jak `Add` i `GetAt`.

##  <a name="_core_implementing_helper_functions"></a> Implementowanie funkcji pomocnika

Klasy kolekcji oparte na szablonach `CArray`, `CList`, i `CMap` za pomocą pięciu funkcji pomocnika globalne, które można dostosować zgodnie z potrzebami dla klasy pochodnej kolekcji. Aby uzyskać informacje na temat tych funkcji pomocnika, zobacz [pomocnicy klasy kolekcji](../mfc/reference/collection-class-helpers.md) w *odwołanie MFC*. Implementacja funkcji serializacji jest niezbędne dla większości zastosowań klasy kolekcji oparte na szablonach.

###  <a name="_core_serializing_elements"></a> Serializacja elementów

`CArray`, `CList`, I `CMap` klasy wywołania `SerializeElements` elementy kolekcji do przechowywania lub odczytać ich z archiwum.

Domyślna implementacja klasy `SerializeElements` funkcji pomocnika nie bitowe zapisu z obiektów do archiwum lub bitowej odczytu do obiektów, w zależności od tego, czy obiekty są przechowywane w archiwum lub pobierane z archiwum. Zastąp `SerializeElements` Jeśli ta akcja nie jest właściwe.

Jeśli Twoja kolekcja przechowuje obiekty opracowane na podstawie `CObject` używasz `IMPLEMENT_SERIAL` makra w implementacji klasy elementu kolekcji, możesz korzystać z zalet funkcji serializacji wbudowanych w `CArchive` i `CObject`:

[!code-cpp[NVC_MFCCollections#9](../mfc/codesnippet/cpp/how-to-make-a-type-safe-collection_3.cpp)]

Operatory przeciążone wstawiania `CArchive` wywołania `CObject::Serialize` (lub zastąpienie tych funkcji) dla każdego `CPerson` obiektu.

##  <a name="_core_using_nontemplate_collection_classes"></a> Używanie klas kolekcji Nieszablonu

Biblioteka MFC obsługuje klasy kolekcji wprowadzone za pomocą MFC w wersji 1.0. Te klasy nie są oparte na szablonach. Może służyć do zawierać dane z obsługiwanych typów `CObject*`, `UINT`, `DWORD`, i `CString`. Możesz użyć tych kolekcji wstępnie zdefiniowanych (takie jak `CObList`) do przechowywania kolekcji wszystkie obiekty opracowane na podstawie `CObject`. Biblioteka MFC zawiera również inne kolekcje wstępnie zdefiniowanych na potrzeby przechowywania typy pierwotne, takie jak `UINT` i void wskaźników (`void`*). Ogólnie rzecz biorąc ale często jest przydatne do zdefiniowania własnych kolekcji bezpieczny do przechowywania obiektów, klasa i jej pochodnych. Należy pamiętać, że ten sposób nie z klasy kolekcji oparte na szablonach więcej pracy niż przy użyciu klas na podstawie szablonu.

Istnieją dwa sposoby tworzenia bezpieczne kolekcje z kolekcjami nieszablonu:

1. Za pomocą kolekcji nieszablonu rzutowanie typu, jeśli to konieczne. Jest to łatwiejsza metoda.

1. Dziedziczyć i rozszerzać nieszablonu bezpiecznej kolekcji.

#### <a name="to-use-the-nontemplate-collections-with-type-casting"></a>Kolekcje nieszablonu za pomocą rzutowanie typów

1. Użyj jednej z klas nieszablonu, takich jak `CWordArray`bezpośrednio.

   Na przykład można utworzyć `CWordArray` i dodać do niego wszystkie wartości 32-bitowych, a następnie pobrać jednego z nich. Nie ma nic więcej, aby zrobić. Wystarczy użyć wstępnie zdefiniowanych funkcji.

   Umożliwia także wstępnie zdefiniowane kolekcji, takie jak `CObList`, aby pomieścić wszystkie obiekty opracowane na podstawie `CObject`. A `CObList` kolekcja jest zdefiniowana na potrzeby przechowywania wskaźniki do `CObject`. Po pobraniu obiektu z listy może być konieczne Rzutuj wynik metody na właściwy typ. od `CObList` funkcje zwracają wskaźniki do `CObject`. Na przykład, jeśli przechowujesz `CPerson` obiekty w `CObList` kolekcji, należy rzutować pobrany element jako wskaźnik do `CPerson` obiektu. W poniższym przykładzie użyto `CObList` kolekcję zawierającą `CPerson` obiektów:

   [!code-cpp[NVC_MFCCollections#10](../mfc/codesnippet/cpp/how-to-make-a-type-safe-collection_4.cpp)]

   Ta technika, za pomocą typu kolekcji wstępnie zdefiniowanych i rzutowania, gdy jest to konieczne może być odpowiednie dla wielu niezbędne do kolekcji. Jeśli potrzebujesz więcej funkcji lub więcej bezpieczeństwa typu użycie na podstawie szablonu klasy lub należy wykonać w następnej procedurze.

#### <a name="to-derive-and-extend-a-nontemplate-type-safe-collection"></a>Pochodzić i rozszerzać nieszablonu bezpiecznej kolekcji

1. Dziedziczyć klasy kolekcji z jednej z klas nieszablonu wstępnie zdefiniowane.

   Po utworzeniu klasy pochodnej klasy, można dodać funkcje otoki bezpieczny, zapewniając interfejs bezpieczny do istniejących funkcji.

   Na przykład, jeśli pochodzi z listy `CObList` do przechowywania `CPerson` obiektów, można dodać funkcje otoki `AddHeadPerson` i `GetHeadPerson`, jak pokazano poniżej.

   [!code-cpp[NVC_MFCCollections#11](../mfc/codesnippet/cpp/how-to-make-a-type-safe-collection_5.h)]

   Te funkcje otoki zapewnić bezpieczny sposób Dodawanie i pobieranie `CPerson` obiekty z listy pochodnych. Możesz zobaczyć, że dla `GetHeadPerson` funkcji, po prostu poddajesz enkapsulacji rzutowanie typu.

   Można również dodać nowe funkcje przez definiowanie nowych funkcji, które rozszerzają możliwości kolekcji, a nie zawijanie istniejących funkcji w otoki bezpiecznegop typu. Na przykład artykułu [usuwanie wszystkich obiektów z kolekcji CObject](../mfc/deleting-all-objects-in-a-cobject-collection.md) w tym artykule opisano funkcję, aby usunąć wszystkie obiekty zawarte na liście. Tej funkcji może być dodane do klasy pochodnej jako funkcję składową.

## <a name="see-also"></a>Zobacz też

[Kolekcje](../mfc/collections.md)

