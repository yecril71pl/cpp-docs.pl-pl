---
title: 'Porady: tworzenie bezpiecznej kolekcji | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- type-safe collections [MFC]
- serializing collection-class elements [MFC]
- collection classes [MFC], type safety
- SerializeElements function [MFC]
- collection classes [MFC], template-based
- serialization [MFC], collection classes
- collection classes [MFC], deriving from nontemplate
ms.assetid: 7230b2db-4283-4083-b098-eb231bf5b89e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1cbcdeec6e39e104625d1b5d47c494915a821d38
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36930036"
---
# <a name="how-to-make-a-type-safe-collection"></a>Porady: tworzenie bezpiecznej kolekcji
W tym artykule wyjaśniono, jak utworzyć kolekcje bezpieczne dla typów danych. Tematy obejmują:  
  
-   [Dla bezpieczeństwa typu przy użyciu klasy oparte na szablonach](#_core_using_template.2d.based_classes_for_type_safety)  
  
-   [Implementowanie funkcji pomocnika](#_core_implementing_helper_functions)  
  
-   [Przy użyciu klasy kolekcji nieszablonu](#_core_using_nontemplate_collection_classes)  
  
 Microsoft Foundation Class Library udostępnia wstępnie zdefiniowane bezpieczne kolekcje oparte na szablonach C++. Ponieważ są one szablony, te klasy zapewniają typu bezpieczeństwo i łatwość użycia bez rzutowanie typów i inne dodatkowe zadania związane ze stosowaniem klasy nieszablonu w tym celu. Przykładowe MFC [ZBIERANIE](../visual-cpp-samples.md) zademonstrowano użycie klasy kolekcji oparte na szablonach w aplikacji MFC. Ogólnie rzecz biorąc korzystając z tych klas pisanie nowego kodu kolekcje za każdym razem.  
  
##  <a name="_core_using_template.2d.based_classes_for_type_safety"></a> Dla bezpieczeństwa typu przy użyciu klasy oparte na szablonach  
  
#### <a name="to-use-template-based-classes"></a>Aby użyć klasy oparte na szablonach  
  
1.  Deklarowanie zmiennej typu klas kolekcji. Na przykład:  
  
     [!code-cpp[NVC_MFCCollections#7](../mfc/codesnippet/cpp/how-to-make-a-type-safe-collection_1.cpp)]  
  
2.  Wywołaj element członkowski funkcje obiektu kolekcji. Na przykład:  
  
     [!code-cpp[NVC_MFCCollections#8](../mfc/codesnippet/cpp/how-to-make-a-type-safe-collection_2.cpp)]  
  
3.  W razie potrzeby Implementowanie [funkcje pomocnicze](../mfc/reference/collection-class-helpers.md) i [serializeelements —](../mfc/reference/collection-class-helpers.md#serializeelements). Aby uzyskać informacje dotyczące implementacji tych funkcji, zobacz [implementowania funkcji pomocnika](#_core_implementing_helper_functions).  
  
 Ten przykład przedstawia deklaracji listy liczb całkowitych. Pierwszy parametr w kroku 1 jest typ danych przechowywanych jako elementy listy. Drugi parametr określa, jak dane ma być przekazane do i zwrócony z funkcji elementów członkowskich klasy kolekcji, takie jak `Add` i `GetAt`.  
  
##  <a name="_core_implementing_helper_functions"></a> Implementowanie funkcji pomocnika  
 Klasy kolekcji oparte na szablonach `CArray`, `CList`, i `CMap` za pomocą pięciu funkcji pomocnika globalne, które można dostosować zgodnie z potrzebami dla klasy pochodnej kolekcji. Aby uzyskać informacje na temat tych funkcji pomocnika, zobacz [pomocnicy klasy kolekcji](../mfc/reference/collection-class-helpers.md) w *odwołania MFC*. Implementacja funkcji serializacji jest niezbędne do zastosowań typu klas kolekcji na podstawie szablonu.  
  
###  <a name="_core_serializing_elements"></a> Elementy serializacji  
 `CArray`, `CList`, I `CMap` klasy wywołania `SerializeElements` do przechowywania elementów kolekcji do lub z nimi zapoznać z archiwum.  
  
 Domyślna implementacja `SerializeElements` funkcji Pomocnik nie bitowe zapisu z obiektów do archiwum lub bitowej odczytać archiwum do obiektów, w zależności od tego, czy obiekty są przechowywane w lub pobrać z archiwum. Zastąpienie `SerializeElements` Jeśli ta akcja nie jest odpowiedni.  
  
 Jeśli kolekcja przechowuje obiektów pochodzących od `CObject` i używasz `IMPLEMENT_SERIAL` makra w implementacji klasy elementu kolekcji, możesz korzystać wbudowane funkcje serializacji `CArchive` i `CObject`:  
  
 [!code-cpp[NVC_MFCCollections#9](../mfc/codesnippet/cpp/how-to-make-a-type-safe-collection_3.cpp)]  
  
 Operatory przeciążone wstawiania `CArchive` wywołać `CObject::Serialize` (lub zastąpienie tych funkcji) dla każdego `CPerson` obiektu.  
  
##  <a name="_core_using_nontemplate_collection_classes"></a> Przy użyciu klasy kolekcji Nieszablonu  
 MFC obsługuje również klasy kolekcji, wprowadzone w systemie MFC w wersji 1.0. Te klasy nie są oparte na szablonach. Może służyć zawiera dane z obsługiwanych typów `CObject*`, `UINT`, `DWORD`, i `CString`. Korzystając z tych wstępnie zdefiniowanych kolekcji (takich jak `CObList`) do przechowywania kolekcji wszystkie obiekty pochodne `CObject`. MFC zawiera również inne wstępnie zdefiniowanych kolekcje, aby pomieścić typy pierwotne, takie jak `UINT` i void wskaźników (`void`*). Ogólnie rzecz biorąc jednak warto często definiować własne kolekcje bezpieczny do przechowywania obiektów klasy bardziej szczegółowe i jego pochodne. Należy pamiętać, że ten sposób nie z klasy kolekcji oparte na szablonach więcej pracy niż przy użyciu klasy oparte na szablonach.  
  
 Istnieją dwa sposoby tworzenia bezpieczne kolekcje z kolekcji nieszablonu:  
  
1.  Za pomocą kolekcji nieszablonu rzutowanie typu, jeśli to konieczne. Jest to metoda łatwiejsze.  
  
2.  Dziedziczyć i rozszerzyć nieszablonu bezpiecznej kolekcji.  
  
#### <a name="to-use-the-nontemplate-collections-with-type-casting"></a>Należy używać kolekcji nieszablonu z rzutowanie typów  
  
1.  Użyj jednej z klas nieszablonu, takiego jak `CWordArray`, bezpośrednio.  
  
     Na przykład można utworzyć `CWordArray` i Dodaj do niej wartości 32-bitowe, a następnie je pobrać. Nie ma nic więcej robić. Wystarczy użyć wstępnie zdefiniowanych funkcji.  
  
     Umożliwia także wstępnie zdefiniowane kolekcji, takie jak `CObList`, aby pomieścić wszystkie obiekty pochodne `CObject`. A `CObList` Kolekcja została zdefiniowana, aby pomieścić wskaźniki do `CObject`. Podczas pobierania obiektu z listy, może być konieczne Rzutuj wynik do prawidłowego typu, ponieważ `CObList` zwracają wskaźniki do `CObject`. Na przykład, jeśli przechowujesz `CPerson` obiekty w `CObList` kolekcji, należy rzutować elementu pobrane do być wskaźnikiem do `CPerson` obiektu. W poniższym przykładzie użyto `CObList` kolekcję `CPerson` obiektów:  
  
     [!code-cpp[NVC_MFCCollections#10](../mfc/codesnippet/cpp/how-to-make-a-type-safe-collection_4.cpp)]  
  
     Ta technika przy użyciu typu kolekcji wstępnie zdefiniowane i rzutowanie w razie potrzeby może być odpowiednie dla wielu potrzeb kolekcji. Jeśli potrzebujesz więcej funkcji lub więcej zabezpieczenie typów używanie klasy oparte na szablonach, lub wykonaj następnej procedury.  
  
#### <a name="to-derive-and-extend-a-nontemplate-type-safe-collection"></a>Pochodzić i rozszerzać nieszablonu bezpiecznej kolekcji  
  
1.  Pochodną klasy kolekcji jednej z klas nieszablonu wstępnie zdefiniowane.  
  
     Jeśli pochodzi z klasy, można dodać funkcje otoki bezpieczny interfejs bezpieczny do istniejących funkcji.  
  
     Na przykład, jeśli pochodzi z listy `CObList` do przechowywania `CPerson` obiekty, można dodać funkcje otoki `AddHeadPerson` i `GetHeadPerson`, jak pokazano poniżej.  
  
     [!code-cpp[NVC_MFCCollections#11](../mfc/codesnippet/cpp/how-to-make-a-type-safe-collection_5.h)]  
  
     Te funkcje otoki zapewnić bezpieczny sposób Dodawanie i pobieranie `CPerson` obiektów na liście pochodnych. Można stwierdzić, że dla `GetHeadPerson` funkcji, są po prostu hermetyzując rzutowanie typu.  
  
     Możesz także dodać nowe funkcje przez definiowanie nowych funkcji, które rozszerzają możliwości kolekcji, a nie tylko zawijania istniejące funkcje w bezpieczny otoki. Na przykład artykuł [usuwanie wszystkich obiektów z kolekcji CObject](../mfc/deleting-all-objects-in-a-cobject-collection.md) opisano funkcję, aby usunąć wszystkie obiekty zawarte na liście. Tej funkcji można dodać do klasy pochodnej jako funkcję elementu członkowskiego.  
  
## <a name="see-also"></a>Zobacz też  
 [Kolekcje](../mfc/collections.md)

