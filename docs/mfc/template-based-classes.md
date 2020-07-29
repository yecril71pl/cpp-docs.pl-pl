---
title: Klasy oparte na szablonach
ms.date: 11/04/2016
helpviewer_keywords:
- type-safe collections
- CTypedPtrList class [MFC], template-based classes
- arrays [MFC], classes
- arrays [MFC], pointers
- typed pointers, collections of
- arrays [MFC], template-based
- CArray class [MFC], template-based classes
- simple template-based collections
- simple array collection classes [MFC]
- typed pointers
- collections, typed-pointer
- CList class [MFC], template-based classes
- collection classes [MFC], template-based
- CTypedPtrMap class [MFC], template-based classes
- pointers, collections of typed
- CTypedPtrArray class [MFC], template-based classes
- MFC collection classes [MFC], template-based
- template-based collection classes [MFC]
- simple list collection classes [MFC]
ms.assetid: c69fc95b-c8f6-4a99-abed-517c9898ef0c
ms.openlocfilehash: eceee4421b43515b9b246f4af26a1a3741c6b25b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230457"
---
# <a name="template-based-classes"></a>Klasy oparte na szablonach

W tym artykule opisano klasy kolekcji z bezpiecznym typem na podstawie szablonu w MFC w wersji 3,0 i nowszych. Korzystanie z tych szablonów do tworzenia kolekcji bezpiecznych dla typów jest wygodniejsze i zapewnia bardziej wydajne bezpieczeństwo typów niż korzystanie z klas kolekcji nieopartych na szablonach.

MFC wstępnie definiuje dwie kategorie kolekcji opartych na szablonach:

- [Proste klasy tablic, list i map](#_core_using_simple_array.2c_.list.2c_.and_map_templates)

   `CArray`, `CList`, `CMap`

- [Tablice, listy i mapy wpisanych wskaźników](#_core_using_typed.2d.pointer_collection_templates)

   `CTypedPtrArray`, `CTypedPtrList`, `CTypedPtrMap`

Proste klasy kolekcji są wyprowadzane z klasy `CObject` , dzięki czemu dziedziczą serializacji, tworzenie dynamiczne i inne właściwości `CObject` . Klasy kolekcji wskaźników z określonym typem wymagają określenia klasy pochodnej, która musi być jedną z kolekcji wskaźników nieszablonowych wstępnie zdefiniowanych przez MFC, takich jak `CPtrList` lub `CPtrArray` . Nowa Klasa kolekcji dziedziczy z określonej klasy bazowej, a funkcje składowe nowej klasy używają hermetyzowanych wywołań do elementów członkowskich klasy podstawowej w celu wymuszenia bezpieczeństwa typu.

Aby uzyskać więcej informacji na temat szablonów języka C++, zobacz [Szablony](../cpp/templates-cpp.md) w *dokumentacji języka c++*.

## <a name="using-simple-array-list-and-map-templates"></a><a name="_core_using_simple_array.2c_.list.2c_.and_map_templates"></a>Używanie prostych szablonów tablicowych, list i map

Aby używać prostych szablonów kolekcji, musisz wiedzieć, jakiego rodzaju dane można przechowywać w tych kolekcjach i jakich parametrów użyć w deklaracjach kolekcji.

### <a name="simple-array-and-list-usage"></a><a name="_core_simple_array_and_list_usage"></a>Proste użycie tablicy i listy

Proste klasy Array i list, [CArray](../mfc/reference/carray-class.md) i [CList](../mfc/reference/clist-class.md), przyjmują dwa parametry: *Type* i `ARG_TYPE` . Klasy te mogą przechowywać dowolny typ danych określony w parametrze *typu* :

- Podstawowe typy danych języka C++, takie jak **`int`** , **`char`** i**`float`**

- Struktury i klasy języka C++

- Inne zdefiniowane typy

Aby uzyskać wygodę i wydajność, można użyć parametru *ARG_TYPE* , aby określić typ argumentów funkcji. Zazwyczaj należy określić *ARG_TYPE* jako odwołanie do typu, który został nazwany w parametrze *typu* . Na przykład:

[!code-cpp[NVC_MFCCollections#1](../mfc/codesnippet/cpp/template-based-classes_1.cpp)]

Pierwszy przykład deklaruje kolekcję tablicową, `myArray` która zawiera element **`int`** s. Drugi przykład deklaruje kolekcję list, `myList` która przechowuje `CPerson` obiekty. Niektóre funkcje elementów członkowskich klas kolekcji przyjmują argumenty, których typ jest określony przez parametr szablonu *ARG_TYPE* . Na przykład `Add` funkcja członkowska klasy `CArray` przyjmuje *ARG_TYPE* argument:

[!code-cpp[NVC_MFCCollections#2](../mfc/codesnippet/cpp/template-based-classes_2.cpp)]

### <a name="simple-map-usage"></a><a name="_core_simple_map_usage"></a>Proste użycie mapy

Prosta Klasa map, [CMAP](../mfc/reference/cmap-class.md), przyjmuje cztery parametry: *Key*, *ARG_KEY*, *Value*i *ARG_VALUE*. Podobnie jak w przypadku klas Array i list, klasy map mogą przechowywać dowolny typ danych. W przeciwieństwie do tablic i list, które indeksuje i porządkują dane przechowywane, mapują skojarzone klucze i wartości: uzyskuje się dostęp do wartości przechowywanej na mapie, określając klucz skojarzony z wartością. Parametr *klucza* określa typ danych kluczy używanych do uzyskiwania dostępu do danych przechowywanych na mapie. Jeśli typ *klucza* jest strukturą lub klasą, parametr *ARG_KEY* jest zazwyczaj odwołaniem do typu określonego w *kluczu*. *Wartość* parametru określa typ elementów przechowywanych na mapie. Jeśli typ *ARG_VALUE* jest strukturą lub klasą, parametr *ARG_VALUE* jest zazwyczaj odwołaniem do typu określonego w polu *wartość*. Na przykład:

[!code-cpp[NVC_MFCCollections#3](../mfc/codesnippet/cpp/template-based-classes_3.cpp)]

Pierwszy przykład zapisuje `MY_STRUCT` wartości, uzyskuje dostęp do nich przez **`int`** klucze i zwraca dostępne `MY_STRUCT` elementy przez odwołanie. Drugi przykład zapisuje `CPerson` wartości, uzyskuje dostęp do nich według `CString` kluczy i zwraca odwołania do elementów, do których można uzyskać dostęp. Ten przykład może reprezentować prostą książkę adresową, w której można wyszukiwać osoby według nazwiska.

Ponieważ parametr *klucza* jest typu `CString` , a parametr *key_type* jest typu `LPCSTR` , klucze są przechowywane na mapie jako elementy typu, `CString` ale są przywoływane w funkcjach, takich jak `SetAt` wskaźniki typu `LPCSTR` . Na przykład:

[!code-cpp[NVC_MFCCollections#4](../mfc/codesnippet/cpp/template-based-classes_4.cpp)]

## <a name="using-typed-pointer-collection-templates"></a><a name="_core_using_typed.2d.pointer_collection_templates"></a>Korzystanie z szablonów kolekcji wskaźników typu

Aby używać szablonów kolekcji wskaźników typu, musisz wiedzieć, jakiego rodzaju dane można przechowywać w tych kolekcjach i jakich parametrów użyć w deklaracjach kolekcji.

### <a name="typed-pointer-array-and-list-usage"></a><a name="_core_typed.2d.pointer_array_and_list_usage"></a>Tablica wskaźników typu i użycie listy

Klasy i tablice wskaźników typu, [CTypedPtrArray](../mfc/reference/ctypedptrarray-class.md) i [CTypedPtrList](../mfc/reference/ctypedptrlist-class.md), przyjmują dwa parametry: *BASE_CLASS* i *Type*. Klasy te mogą przechowywać dowolny typ danych określony w parametrze *typu* . Są one wyprowadzane z jednej z klas kolekcji nienależących do szablonu, która przechowuje wskaźniki; Tę klasę bazową należy określić w *BASE_CLASS*. W przypadku tablic Użyj jednego `CObArray` lub `CPtrArray` . W przypadku list Użyj jednego `CObList` lub `CPtrList` .

W efekcie w przypadku deklarowania kolekcji na podstawie, Załóżmy `CObList` , Nowa klasa nie tylko dziedziczy elementy członkowskie swojej klasy bazowej, ale również deklaruje szereg dodatkowych bezpiecznych funkcji elementów członkowskich i operatorów, które pomagają zapewnić bezpieczeństwo typu przez hermetyzację wywołań do elementów członkowskich klasy bazowej. Te hermetyzacje zarządzają wszelką wymaganą konwersją typu. Na przykład:

[!code-cpp[NVC_MFCCollections#5](../mfc/codesnippet/cpp/template-based-classes_5.cpp)]

Pierwszy przykład deklaruje tablicę wskaźników typu, `myArray` , pochodny od `CObArray` . Tablica przechowuje i zwraca wskaźniki do `CPerson` obiektów (gdzie `CPerson` jest klasą pochodną `CObject` ). Można wywołać dowolną `CObArray` funkcję członkowską lub wywołać nowe bezpieczne typy `GetAt` i `ElementAt` funkcje lub użyć operatora typu Safe **[]** .

Drugi przykład deklaruje listę wskaźników typu, `myList` , pochodny od `CPtrList` . Lista przechowuje i zwraca wskaźniki do `MY_STRUCT` obiektów. Klasa oparta na `CPtrList` jest używana do przechowywania wskaźników do obiektów, które nie są wyprowadzane z `CObject` . `CTypedPtrList`ma wiele bezpiecznych funkcji składowych typu:,,,,, `GetHead` `GetTail` `RemoveHead` `RemoveTail` `GetNext` `GetPrev` i `GetAt` .

### <a name="typed-pointer-map-usage"></a><a name="_core_typed.2d.pointer_map_usage"></a>Użycie mapy wskaźnika typu

Klasa mapy typu wskaźnika [CTypedPtrMap](../mfc/reference/ctypedptrmap-class.md), przyjmuje trzy parametry: *BASE_CLASS*, *klucz*i *wartość*. *BASE_CLASS* parametr określa klasę, z której należy utworzyć nową klasę: `CMapPtrToWord` ,,, `CMapPtrToPtr` , `CMapStringToPtr` `CMapWordToPtr` `CMapStringToOb` i tak dalej. *Klucz* jest analogiczny do *klucza* w `CMap` : określa typ klucza używanego do wyszukiwania. *Wartość* jest analogiczna do *wartości* w `CMap` : określa typ obiektu przechowywanego na mapie. Na przykład:

[!code-cpp[NVC_MFCCollections#6](../mfc/codesnippet/cpp/template-based-classes_6.cpp)]

Pierwszy przykład jest oparty na mapie `CMapPtrToPtr` — używa `CString` kluczy mapowanych na wskaźniki do `MY_STRUCT` . Można wyszukać przechowywany wskaźnik, wywołując bezpieczną `Lookup` funkcję składową typu. Możesz użyć operatora **[]** , aby wyszukać przechowywany wskaźnik i dodać go, jeśli nie zostanie znaleziony. I można wykonać iterację mapy przy użyciu funkcji bezpiecznego typu `GetNextAssoc` . Możesz również wywołać inne funkcje składowe klasy `CMapPtrToPtr` .

Drugim przykładem jest mapa oparta na `CMapStringToOb` — używa kluczy ciągów mapowanych na przechowywane wskaźniki do `CMyObject` obiektów. Można użyć tych samych bezpiecznych dla typu elementów członkowskich opisanych w poprzednim akapicie lub wywołać elementy członkowskie klasy `CMapStringToOb` .

> [!NOTE]
> Jeśli określisz **`class`** Typ lub jako **`struct`** parametr *wartości* , a nie wskaźnik lub odwołanie do typu, Klasa lub struktura muszą mieć Konstruktor kopiujący.

Aby uzyskać więcej informacji, zobacz [jak tworzyć Kolekcje bezpieczne dla typów](../mfc/how-to-make-a-type-safe-collection.md).

## <a name="see-also"></a>Zobacz także

[Kolekcje](../mfc/collections.md)
