---
title: Klasy zasad kopiowania ATL
ms.date: 11/04/2016
helpviewer_keywords:
- data [C++], ATL
- classes [C++], copy policy
- copy policy classes [C++]
- _Copy class
- _CopyInterface class
ms.assetid: 06704b68-d318-4c5d-a65b-71457fe9d00d
ms.openlocfilehash: f40f31124d4547076249a7459ac4b63cc25305d1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317379"
---
# <a name="atl-copy-policy-classes"></a>Klasy zasad kopiowania ATL

Klasy zasad kopiowania są [klasami narzędzi używanymi](../atl/utility-classes.md) do inicjowania, kopiowania i usuwania danych. Klasy zasad kopiowania umożliwiają definiowanie semantyki kopiowania dla dowolnego typu danych oraz definiowanie konwersji między różnymi typami danych.

ATL używa klas zasad kopiowania w swoich implementacjach następujących szablonów:

- [CComEnumImpl (Polski)](../atl/reference/ccomenumimpl-class.md)

- [IEnumOnSTLImpl](../atl/reference/ienumonstlimpl-class.md)

- [Icollectiononstlimpl](../atl/reference/icollectiononstlimpl-class.md)

Hermetyzując informacje potrzebne do kopiowania lub konwertowania danych w klasie zasad kopiowania, które mogą być przekazywane jako argument szablonu, deweloperzy ATL zapewnili ekstremalne możliwości ponownego użycia tych klas. Na przykład jeśli trzeba zaimplementować kolekcji przy użyciu dowolnego typu danych, wszystko, co musisz podać, to odpowiednie zasady kopiowania; nigdy nie trzeba dotykać kodu, który implementuje kolekcji.

## <a name="definition"></a>Definicja

Z definicji klasa, która zapewnia następujące funkcje statyczne jest klasą zasad kopiowania:

`static void init(` `DestinationType` `* p);`

`static HRESULT copy(` `DestinationType` `* pTo, const`  `SourceType` `* pFrom);`

`static void destroy(` `DestinationType` `* p);`

Można zastąpić typy `DestinationType` i *SourceType* dowolne typy danych dla każdej zasady kopiowania.

> [!NOTE]
> Chociaż można zdefiniować klasy zasad kopiowania dla dowolnych typów danych, użycie klas w kodzie ATL powinno ograniczyć typy, które mają sens. Na przykład podczas korzystania z klasy zasad kopiowania z kolekcji ATL lub wyliczanie implementacji, musi być typem, `DestinationType` który może służyć jako parametr w metodzie interfejsu COM.

**Init** służy do inicjowania danych, **kopiowania** do kopiowania danych i **niszczenia** w celu zwolnienia danych. Dokładne znaczenie inicjowania, kopiowania i niszczenia są domeną klasy zasad kopiowania i będą się różnić w zależności od typów danych.

Istnieją dwa wymagania dotyczące używania i implementacji klasy zasad kopiowania:

- Pierwszy parametr do **skopiowania** musi odbierać tylko wskaźnik do danych, które zostały wcześniej zainicjowane przy użyciu **init**.

- **destroy** musi otrzymać tylko wskaźnik do danych, które zostały wcześniej zainicjowane przy użyciu **init** lub skopiowane za pomocą **kopii**.

## <a name="standard-implementations"></a>Implementacje standardowe

ATL udostępnia dwie klasy zasad kopiowania w postaci klas szablonów `_Copy` i `_CopyInterface` szablonów:

- Klasa `_Copy` umożliwia tylko jednorodne kopiowanie (nie konwersja między typami danych), ponieważ `DestinationType` oferuje tylko jeden parametr szablonu, aby określić zarówno i *SourceType*. Ogólna implementacja tego szablonu nie zawiera kodu `memcpy` inicjowania ani niszczenia i służy do kopiowania danych. ATL zapewnia również specjalizacje `_Copy` dla typów danych VARIANT, LPOLESTR, OLEVERB i CONNECTDATA.

- Klasa `_CopyInterface` zapewnia implementację kopiowania wskaźników interfejsu zgodnie ze standardowymi regułami COM. Po raz kolejny ta klasa umożliwia tylko jednorodne kopiowanie, więc `AddRef` używa prostego przypisania i wywołania do wykonania kopii.

## <a name="custom-implementations"></a>Implementacje niestandardowe

Zazwyczaj należy zdefiniować własne klasy zasad kopiowania dla heterogenicznego kopiowania (czyli konwersji między typami danych). W przypadku niektórych przykładów klas zasad kopiowania niestandardowego, spójrz na pliki VCUE_Copy.h i VCUE_CopyString.h w przykładzie [ATLCollections.](../overview/visual-cpp-samples.md) Pliki te zawierają dwie klasy `GenericCopy` `MapCopy`zasad kopiowania szablonów i `GenericCopy` , plus szereg specjalizacji dla różnych typów danych.

### <a name="genericcopy"></a>Genericcopy

`GenericCopy`umożliwia określenie *sourcetype* i `DestinationType` jako argumenty szablonu. Oto najbardziej ogólna forma `GenericCopy` klasy z VCUE_Copy.h:

[!code-cpp[NVC_ATL_COM#30](../atl/codesnippet/cpp/atl-copy-policy-classes_1.h)]

VCUE_Copy.h zawiera również następujące specjalizacje tej `GenericCopy<BSTR>` `GenericCopy<VARIANT, BSTR>`klasy: , , `GenericCopy<BSTR, VARIANT>`. VCUE_CopyString.h zawiera specjalizacje do kopiowania z **std::string**s: `GenericCopy<std::string>`, `GenericCopy<VARIANT, std::string>`, i `GenericCopy<BSTR, std::string>`. Możesz poprawić, `GenericCopy` zapewniając kolejne specjalizacje własne.

### <a name="mapcopy"></a>Kopia mapy

`MapCopy`zakłada, że kopiowane dane są przechowywane na mapie w stylu biblioteki standardowej języka C++, dzięki czemu można określić typ mapy, na której dane są przechowywane i typ docelowy. Implementacja klasy po prostu używa typedefs dostarczone przez *MapType* klasy, aby określić typ `GenericCopy` danych źródłowych i wywołać odpowiednią klasę. Nie są potrzebne żadne specjalizacje tej klasy.

[!code-cpp[NVC_ATL_COM#31](../atl/codesnippet/cpp/atl-copy-policy-classes_2.h)]

## <a name="see-also"></a>Zobacz też

[Implementowanie kolekcji opartej na standardowej bibliotece języka C++](../atl/implementing-an-stl-based-collection.md)<br/>
[AtlCollections Przykład](../overview/visual-cpp-samples.md)
