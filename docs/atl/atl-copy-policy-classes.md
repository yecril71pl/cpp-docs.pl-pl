---
title: Klasy zasad kopii ATL
ms.date: 11/04/2016
helpviewer_keywords:
- data [C++], ATL
- classes [C++], copy policy
- copy policy classes [C++]
- _Copy class
- _CopyInterface class
ms.assetid: 06704b68-d318-4c5d-a65b-71457fe9d00d
ms.openlocfilehash: 73bec31b4ae140797c85a06ee7c5023c9e0c4446
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58776963"
---
# <a name="atl-copy-policy-classes"></a>Klasy zasad kopii ATL

Klasy zasad kopii są [klasy narzędzi](../atl/utility-classes.md) używane do zainicjowania, kopiowania i usuwania danych. Klasy zasad kopii pozwalają zdefiniować semantyka kopiowania dla dowolnego typu danych i do definiowania konwersje między różnymi typami danych.

Używa klasy zasad kopii ATL w ich implementacji następujące szablony:

- [CComEnumImpl](../atl/reference/ccomenumimpl-class.md)

- [IEnumOnSTLImpl](../atl/reference/ienumonstlimpl-class.md)

- [ICollectionOnSTLImpl](../atl/reference/icollectiononstlimpl-class.md)

Poprzez hermetyzację informacji potrzebnych do kopiowania lub przekonwertować danych w kopii klasy zasad, który może być przekazywany jako argument szablonu, deweloperzy ATL zostały podane dla extreme możliwość ponownego wykorzystania tych klas. Na przykład jeśli musisz wdrożyć kolekcji za pomocą dowolnego typu dowolne dane, wszystko, co należy podać to polityki odpowiedniej kopii. nigdy nie mają dostępu do kodu, który implementuje kolekcji.

## <a name="definition"></a>Definicja

Zgodnie z definicją klasa, która oferuje następujące funkcje statyczne jest klasy zasad kopii:

`static void init(` `DestinationType` `* p);`

`static HRESULT copy(` `DestinationType` `* pTo, const`  `SourceType` `* pFrom);`

`static void destroy(` `DestinationType` `* p);`

Możesz zastąpić typy `DestinationType` i *SourceType* z typami dowolne dane dla każdej zasady kopii.

> [!NOTE]
>  Chociaż można zdefiniować klasy zasad kopii dla wszystkich typów dowolne dane, użyj klasy w kodzie ATL należy ograniczyć typy, które są uwzględnione. Na przykład, gdy za pomocą zasad kopii klasy kolekcji ATL lub implementacji modułu wyliczającego `DestinationType` musi być typem, który może służyć jako parametr metody interfejsu COM.

Użyj **init** zainicjować danych, **kopiowania** do kopiowania danych i **zniszczyć** zwolnienie danych. Znaczenie inicjalizacji, kopiowanie i niszczeniem domeny klasy zasad kopii i różnią się w zależności od typów danych związane.

Istnieją dwa wymagania dotyczące użycia i implementacja klasy zasad kopii:

- Pierwszy parametr **kopiowania** tylko musi otrzymać bit wskaźnik do danych, które zostały wcześniej zainicjowana przy użyciu **init**.

- **zniszcz** tylko musi otrzymać bit wskaźnik do danych, które zostały wcześniej zainicjowana przy użyciu **init** lub kopiowany za pośrednictwem **kopiowania**.

## <a name="standard-implementations"></a>Standardowe wdrożenia

ATL zawiera dwie klasy zasad kopii w formie `_Copy` i `_CopyInterface` klasy szablonów:

- `_Copy` Klasa umożliwia jednorodnych kopiowanie tylko (nie konwersji między typami danych), ponieważ oferuje ona tylko określić zarówno parametr jednego szablonu `DestinationType` i *SourceType*. Ogólną implementację ten szablon nie zawiera inicjowanie lub niszczenie kodu i używa `memcpy` do kopiowania danych. ATL udostępnia również specjalizacje `_Copy` wariant, LPOLESTR, OLEVERB i CONNECTDATA typów danych.

- `_CopyInterface` Klasa udostępnia implementację na potrzeby kopiowania wskaźniki interfejsu następujące standardowe reguły COM. Ponownie ta klasa umożliwia tylko jednorodnych kopiowanie, więc używa przypisanie proste i wywołania `AddRef` do wykonania kopii.

## <a name="custom-implementations"></a>Niestandardowe implementacje

Zazwyczaj należy zdefiniować własne klasy zasad kopii heterogenicznych kopiowania (czyli konwersji między typami danych). Niektóre przykłady kopii niestandardowych zasad klas, Przyjrzyj się pliki VCUE_Copy.h i VCUE_CopyString.h w [ATLCollections](../overview/visual-cpp-samples.md) próbki. Te pliki zawierają dwie klasy zasad kopię szablonu, `GenericCopy` i `MapCopy`, oraz liczbę specjalizacje `GenericCopy` dla różnych typów danych.

### <a name="genericcopy"></a>GenericCopy

`GenericCopy` Umożliwia określenie *SourceType* i `DestinationType` jako argumenty szablonu. Poniżej przedstawiono najbardziej ogólny kształt `GenericCopy` klasy z VCUE_Copy.h:

[!code-cpp[NVC_ATL_COM#30](../atl/codesnippet/cpp/atl-copy-policy-classes_1.h)]

VCUE_Copy.h zawiera również następujące specjalizacje tej klasy: `GenericCopy<BSTR>`, `GenericCopy<VARIANT, BSTR>`, `GenericCopy<BSTR, VARIANT>`. VCUE_CopyString.h zawiera specjalizacje kopiowania z **std::string**s: `GenericCopy<std::string>`, `GenericCopy<VARIANT, std::string>`, i `GenericCopy<BSTR, std::string>`. Można zwiększyć `GenericCopy` , zapewniając dalsze specjalizacje samodzielnie.

### <a name="mapcopy"></a>MapCopy

`MapCopy` przyjęto założenie, że dane są kopiowane są przechowywane w mapę C++ Standard Library-style, więc umożliwia określenie typu mapy, w którym są przechowywane dane, a następnie wpisz docelowy. Implementacja klasy używa tylko definicje typów dostarczonych przez *MapType* klasy można ustalić typu źródła danych oraz wywołanie odpowiedniego `GenericCopy` klasy. Nie specjalizacje tej klasy są wymagane.

[!code-cpp[NVC_ATL_COM#31](../atl/codesnippet/cpp/atl-copy-policy-classes_2.h)]

## <a name="see-also"></a>Zobacz także

[Implementowanie kolekcji opartej na standardowej bibliotece C++](../atl/implementing-an-stl-based-collection.md)<br/>
[ATLCollections Sample](../overview/visual-cpp-samples.md)
