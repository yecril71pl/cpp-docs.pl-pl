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
ms.openlocfilehash: 6ee4603f03ef8a95c218b0fe040e9606aab99ebb
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620011"
---
# <a name="how-to-make-a-type-safe-collection"></a>Porady: tworzenie bezpiecznej kolekcji

W tym artykule wyjaśniono, jak zapewnić bezpieczne tworzenie kolekcji dla własnych typów danych. Tematy obejmują:

- [Korzystanie z klas opartych na szablonach w celu zapewnienia bezpieczeństwa typów](#_core_using_template.2d.based_classes_for_type_safety)

- [Implementowanie funkcji pomocnika](#_core_implementing_helper_functions)

- [Korzystanie z klas kolekcji nieszablonowych](#_core_using_nontemplate_collection_classes)

Biblioteka MFC zapewnia wstępnie zdefiniowane bezpieczne kolekcje na podstawie szablonów języka C++. Ponieważ są to szablony, te klasy pomagają zapewnić bezpieczeństwo typów i łatwość użycia bez rzutowania typów i innych dodatkowych zadań związanych z użyciem w tym celu klasy niebędącej szablonami. [Zbieranie](../overview/visual-cpp-samples.md) próbek MFC ilustruje użycie klas kolekcji opartych na szablonach w aplikacji MFC. Ogólnie rzecz biorąc, Użyj tych klas przy każdej pisaniu nowego kodu kolekcji.

## <a name="using-template-based-classes-for-type-safety"></a><a name="_core_using_template.2d.based_classes_for_type_safety"></a>Korzystanie z klas opartych na szablonach w celu zapewnienia bezpieczeństwa typów

#### <a name="to-use-template-based-classes"></a>Aby używać klas opartych na szablonach

1. Zadeklaruj zmienną typu klasy kolekcji. Przykład:

   [!code-cpp[NVC_MFCCollections#7](codesnippet/cpp/how-to-make-a-type-safe-collection_1.cpp)]

1. Wywołaj funkcje członkowskie obiektu kolekcja. Przykład:

   [!code-cpp[NVC_MFCCollections#8](codesnippet/cpp/how-to-make-a-type-safe-collection_2.cpp)]

1. W razie potrzeby Zaimplementuj [funkcje pomocnika](reference/collection-class-helpers.md) i [SerializeElements](reference/collection-class-helpers.md#serializeelements). Aby uzyskać informacje na temat implementowania tych funkcji, zobacz [Implementowanie funkcji pomocnika](#_core_implementing_helper_functions).

Ten przykład pokazuje deklarację listy liczb całkowitych. Pierwszy parametr w kroku 1 jest typem danych przechowywanych jako elementy listy. Drugi parametr określa, w jaki sposób dane mają być przesyłane do i zwracane z funkcji członkowskich klasy kolekcji, takich jak `Add` i `GetAt` .

## <a name="implementing-helper-functions"></a><a name="_core_implementing_helper_functions"></a>Implementowanie funkcji pomocnika

Klasy kolekcji oparte na szablonach `CArray` `CList` i `CMap` używają pięciu globalnych funkcji pomocniczych, które można dostosować zgodnie z potrzebami dla klasy kolekcji pochodnej. Aby uzyskać informacje na temat tych funkcji pomocnika, zobacz sekcję [klasy kolekcji pomocników](reference/collection-class-helpers.md) w *dokumentacji MFC*. Implementacja funkcji serializacji jest niezbędna w przypadku większości przypadków użycia klas kolekcji opartych na szablonach.

### <a name="serializing-elements"></a><a name="_core_serializing_elements"></a>Serializowanie elementów

`CArray`Klasy, `CList` i są `CMap` wywoływane `SerializeElements` w celu przechowywania elementów kolekcji lub odczytywania ich z archiwum.

Domyślna implementacja `SerializeElements` funkcji pomocnika jest zapisem bitowym z obiektów do archiwum lub bitowym odczytem z archiwum do obiektów, w zależności od tego, czy obiekty są przechowywane lub pobierane z archiwum. Przesłoń, `SerializeElements` Jeśli ta akcja nie jest odpowiednia.

Jeśli w kolekcji są przechowywane obiekty pochodne `CObject` i używasz `IMPLEMENT_SERIAL` makra w implementacji klasy elementu kolekcji, możesz skorzystać z funkcji serializacji wbudowanych w `CArchive` i `CObject` :

[!code-cpp[NVC_MFCCollections#9](codesnippet/cpp/how-to-make-a-type-safe-collection_3.cpp)]

Przeciążone operatory wstawiania dla `CArchive` wywołania `CObject::Serialize` (lub przesłonięcia tej funkcji) dla każdego `CPerson` obiektu.

## <a name="using-nontemplate-collection-classes"></a><a name="_core_using_nontemplate_collection_classes"></a>Korzystanie z klas kolekcji nieszablonowych

MFC obsługuje również klasy kolekcji wprowadzone z MFC w wersji 1,0. Te klasy nie są oparte na szablonach. Mogą one służyć do przechowywania danych obsługiwanych typów `CObject*` ,, `UINT` `DWORD` i `CString` . Za pomocą tych wstępnie zdefiniowanych kolekcji (takich jak `CObList` ) można przechowywać kolekcje wszystkich obiektów pochodzących od `CObject` . MFC udostępnia również inne wstępnie zdefiniowane kolekcje do przechowywania typów pierwotnych, takich jak `UINT` i wskaźników void ( `void` *). Ogólnie rzecz biorąc, często warto definiować własne kolekcje bezpieczne dla typów w celu przechowywania obiektów z bardziej konkretną klasą i jej pochodnych. Należy pamiętać, że wykonanie tej operacji z klasami kolekcji, które nie są oparte na szablonach, nie działa dłużej niż przy użyciu klas opartych na szablonach.

Istnieją dwa sposoby tworzenia bezpiecznych kolekcji z kolekcjami nienależącymi do szablonu:

1. W razie potrzeby Użyj kolekcji nieszablonowych z funkcją rzutowania typu. Jest to prostsze podejście.

1. Dziedzicz z i rozbuduj kolekcję niebędącą bezpiecznym typem.

#### <a name="to-use-the-nontemplate-collections-with-type-casting"></a>Aby użyć kolekcji nieszablonowych z rzutowania typu

1. Użyj jednej z klas nieszablonowych, takich jak `CWordArray` , bezpośrednio.

   Na przykład można utworzyć `CWordArray` i dodać dowolne wartości 32-bitowe, a następnie je pobrać. Nic nie rób. Wystarczy użyć wstępnie zdefiniowanych funkcji.

   Można również użyć wstępnie zdefiniowanej kolekcji, takiej jak `CObList` ,, aby przechowywać wszystkie obiekty pochodne od `CObject` . `CObList`Kolekcja jest zdefiniowana do przechowywania wskaźników do `CObject` . Gdy pobierasz obiekt z listy, może być konieczne rzutowanie wyniku na właściwy typ, ponieważ `CObList` funkcje zwracają wskaźniki do `CObject` . Na przykład, Jeśli przechowujesz `CPerson` obiekty w `CObList` kolekcji, musisz rzutować pobrany element na wskaźnik do `CPerson` obiektu. Poniższy przykład używa `CObList` kolekcji do przechowywania `CPerson` obiektów:

   [!code-cpp[NVC_MFCCollections#10](codesnippet/cpp/how-to-make-a-type-safe-collection_4.cpp)]

   Ta technika użycia wstępnie zdefiniowanego typu kolekcji i rzutowania w miarę potrzeb może być odpowiednia dla wielu potrzeb kolekcji. Jeśli potrzebujesz dodatkowych funkcji lub zapewnienia bezpieczeństwa typów, użyj klasy opartej na szablonach lub postępuj zgodnie z następną procedurą.

#### <a name="to-derive-and-extend-a-nontemplate-type-safe-collection"></a>Aby utworzyć i rozłożyć kolekcję niebędącą bezpiecznym typem dla nieszablonu

1. Utwórz własną klasę kolekcji z jednej ze wstępnie zdefiniowanych klas nieszablonowych.

   Podczas wyprowadzania klasy można dodać funkcje otoki bezpieczne dla typów, aby zapewnić bezpieczny dla typu interfejs do istniejących funkcji.

   Na przykład jeśli pochodną jest lista z `CObList` do przechowywania `CPerson` obiektów, można dodać funkcje otoki `AddHeadPerson` i `GetHeadPerson` , jak pokazano poniżej.

   [!code-cpp[NVC_MFCCollections#11](codesnippet/cpp/how-to-make-a-type-safe-collection_5.h)]

   Te funkcje otoki zapewniają bezpieczny dla typu sposób dodawania i pobierania `CPerson` obiektów z listy pochodnej. Możesz zobaczyć, że dla `GetHeadPerson` funkcji jest po prostu hermetyzacja rzutowania typu.

   Możesz również dodać nową funkcję, definiując nowe funkcje, które zwiększają możliwości kolekcji, a nie tylko umieszczając istniejące funkcje w otokach bezpiecznych dla typów. Na przykład artykuł [usuwanie wszystkich obiektów w kolekcji CObject](deleting-all-objects-in-a-cobject-collection.md) zawiera opis funkcji usuwania wszystkich obiektów znajdujących się na liście. Tę funkcję można dodać do klasy pochodnej jako funkcji składowej.

## <a name="see-also"></a>Zobacz też

[Kolekcje](collections.md)
