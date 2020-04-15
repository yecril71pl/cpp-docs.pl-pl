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
ms.openlocfilehash: 1901100996a776244b57efe0951795ceec3c630a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377259"
---
# <a name="how-to-make-a-type-safe-collection"></a>Porady: tworzenie bezpiecznej kolekcji

W tym artykule wyjaśniono, jak tworzyć kolekcje bezpieczne dla własnych typów danych. Tematy obejmują:

- [Używanie klas opartych na szablonach dla bezpieczeństwa typów](#_core_using_template.2d.based_classes_for_type_safety)

- [Wdrażanie funkcji pomocnika](#_core_implementing_helper_functions)

- [Korzystanie z klas kolekcji nontemplate](#_core_using_nontemplate_collection_classes)

Biblioteka klas programu Microsoft Foundation udostępnia wstępnie zdefiniowane kolekcje bezpieczne dla typu oparte na szablonach języka C++. Ponieważ są szablonami, te klasy pomagają zapewnić bezpieczeństwo typu i łatwość użycia bez odlewania typu i innych dodatkowych prac związanych z używaniem klasy nontemplate w tym celu. Przykład MFC [COLLECT](../overview/visual-cpp-samples.md) pokazuje użycie klas kolekcji opartych na szablonie w aplikacji MFC. Ogólnie rzecz biorąc należy używać tych klas za każdym razem, gdy piszesz nowy kod kolekcji.

## <a name="using-template-based-classes-for-type-safety"></a><a name="_core_using_template.2d.based_classes_for_type_safety"></a>Używanie klas opartych na szablonach dla bezpieczeństwa typów

#### <a name="to-use-template-based-classes"></a>Aby użyć klas opartych na szablonach

1. Zadeklaruj zmienną typu klasy kolekcji. Przykład:

   [!code-cpp[NVC_MFCCollections#7](../mfc/codesnippet/cpp/how-to-make-a-type-safe-collection_1.cpp)]

1. Wywołanie funkcji członkowskich obiektu kolekcji. Przykład:

   [!code-cpp[NVC_MFCCollections#8](../mfc/codesnippet/cpp/how-to-make-a-type-safe-collection_2.cpp)]

1. W razie potrzeby zaimplementuj [funkcje pomocnika](../mfc/reference/collection-class-helpers.md) i [SerializeElements](../mfc/reference/collection-class-helpers.md#serializeelements). Aby uzyskać informacje na temat wdrażania tych funkcji, zobacz [Implementowanie funkcji pomocnika](#_core_implementing_helper_functions).

W tym przykładzie przedstawiono deklarację listy liczby całkowite. Pierwszym parametrem w kroku 1 jest typ danych przechowywanych jako elementy listy. Drugi parametr określa sposób przekazywania i zwracania danych z funkcji członkowskich klasy `Add` `GetAt`kolekcji, takich jak i .

## <a name="implementing-helper-functions"></a><a name="_core_implementing_helper_functions"></a>Wdrażanie funkcji pomocnika

Klasy kolekcji oparte `CArray` `CList`na `CMap` szablonach i użyj pięciu globalnych funkcji pomocnika, które można dostosować w razie potrzeby dla klasy kolekcji pochodnej. Aby uzyskać informacje na temat tych funkcji pomocnika, zobacz [Pomocnicy klas kolekcji](../mfc/reference/collection-class-helpers.md) w *odwołaniu MFC*. Implementacja funkcji serializacji jest niezbędna dla większości zastosowań klas kolekcji opartych na szablonie.

### <a name="serializing-elements"></a><a name="_core_serializing_elements"></a>Elementy serializujące

, `CArray` `CList`i `CMap` klasy `SerializeElements` wywołać do przechowywania elementów kolekcji lub odczytać je z archiwum.

Domyślna implementacja `SerializeElements` funkcji pomocnika wykonuje bitowy zapis z obiektów do archiwum lub bitowy odczyt z archiwum do obiektów, w zależności od tego, czy obiekty są przechowywane w archiwum, czy też pobierane z archiwum. Zastąd, `SerializeElements` jeśli ta akcja nie jest odpowiednia.

Jeśli kolekcja przechowuje obiekty `CObject` pochodzące `IMPLEMENT_SERIAL` z i używasz makra w implementacji klasy elementu kolekcji, `CArchive` `CObject`można skorzystać z wbudowanej funkcji serializacji i:

[!code-cpp[NVC_MFCCollections#9](../mfc/codesnippet/cpp/how-to-make-a-type-safe-collection_3.cpp)]

Przeciążony operator wstawiania dla `CArchive` wywołania `CObject::Serialize` (lub zastąpienia tej `CPerson` funkcji) dla każdego obiektu.

## <a name="using-nontemplate-collection-classes"></a><a name="_core_using_nontemplate_collection_classes"></a>Korzystanie z klas kolekcji nontemplate

MFC obsługuje również klasy kolekcji wprowadzone z MFC w wersji 1.0. Te klasy nie są oparte na szablonach. Mogą być używane do przechowywania danych `CObject*`obsługiwanych `DWORD`typów `CString`, `UINT`, i . Za pomocą tych wstępnie zdefiniowanych kolekcji `CObList`(takich jak ) można przechowywać kolekcje dowolnych obiektów pochodzących z programu `CObject`. MFC udostępnia również inne wstępnie zdefiniowane kolekcje do `UINT` przechowywania typów pierwotnych, takich jak i void wskaźniki (`void`*). Ogólnie rzecz biorąc, jednak często jest przydatne do definiowania własnych kolekcji typu bezpieczne do przechowywania obiektów bardziej szczegółowej klasy i jej pochodnych. Należy zauważyć, że w ten sposób z klas kolekcji nie na podstawie szablonów jest więcej pracy niż przy użyciu klas opartych na szablonie.

Istnieją dwa sposoby tworzenia kolekcji typu bezpieczne z kolekcji nontemplate:

1. Użyj kolekcji nontemplate, z odlewaniem typu, jeśli to konieczne. Jest to łatwiejsze podejście.

1. Wywodź z kolekcji bezpiecznej dla typu nontemplate i rozszerzaj ją.

#### <a name="to-use-the-nontemplate-collections-with-type-casting"></a>Aby użyć kolekcji niepamiętowych z odlewaniem typu

1. Użyj jednej z klas nontemplate, takich jak `CWordArray`, bezpośrednio.

   Na przykład można utworzyć `CWordArray` i dodać dowolne wartości 32-bitowe, a następnie pobrać je. Nie ma nic więcej do zrobienia. Wystarczy użyć wstępnie zdefiniowanej funkcji.

   Można również użyć wstępnie zdefiniowanej kolekcji, takiej jak `CObList`, `CObject`aby pomieścić wszystkie obiekty pochodzące z . Kolekcja `CObList` jest definiowana do `CObject`przechowywania wskaźników do . Podczas pobierania obiektu z listy może być trzeba rzutować wynik do `CObList` właściwego typu, `CObject`ponieważ funkcje zwracają wskaźniki do . Na przykład jeśli `CPerson` przechowujesz `CObList` obiekty w kolekcji, należy rzutować pobrany `CPerson` element, aby być wskaźnikiem do obiektu. W poniższym przykładzie `CObList` użyto kolekcji do przechowywania `CPerson` obiektów:

   [!code-cpp[NVC_MFCCollections#10](../mfc/codesnippet/cpp/how-to-make-a-type-safe-collection_4.cpp)]

   Ta technika przy użyciu wstępnie zdefiniowanego typu kolekcji i odlewania w razie potrzeby może być odpowiednia dla wielu potrzeb kolekcji. Jeśli potrzebujesz dodatkowych funkcji lub więcej bezpieczeństwa typu, użyj klasy opartej na szablonie lub wykonaj następną procedurę.

#### <a name="to-derive-and-extend-a-nontemplate-type-safe-collection"></a>Aby wyprowadzić i rozszerzyć kolekcję bezpieczną dla typu nontemplate

1. Wywodź własną klasę kolekcji z jednej z wstępnie zdefiniowanych klas nontemplate.

   Po wyprowadzeniu klasy można dodać funkcje otoki bezpieczne dla typu, aby zapewnić interfejs bezpieczny dla typu do istniejących funkcji.

   Na przykład, jeśli lista pochodzi `CObList` od `CPerson` do przechowywania obiektów, można `AddHeadPerson` `GetHeadPerson`dodać funkcje otoki i , jak pokazano poniżej.

   [!code-cpp[NVC_MFCCollections#11](../mfc/codesnippet/cpp/how-to-make-a-type-safe-collection_5.h)]

   Te funkcje otoki zapewniają bezpieczny dla typu `CPerson` sposób dodawania i pobierania obiektów z listy pochodnej. Widać, że dla `GetHeadPerson` funkcji, jesteś po prostu hermetyzowanie rzutowania typu.

   Można również dodać nowe funkcje, definiując nowe funkcje, które rozszerzają możliwości kolekcji, a nie tylko zawijania istniejących funkcji w otoki typu bezpieczne. Na przykład w artykule [Usuwanie wszystkich obiektów w kolekcji CObject](../mfc/deleting-all-objects-in-a-cobject-collection.md) opisuje funkcję usuwania wszystkich obiektów znajdujących się na liście. Ta funkcja może zostać dodana do klasy pochodnej jako funkcja elementu członkowskiego.

## <a name="see-also"></a>Zobacz też

[Kolekcje](../mfc/collections.md)
