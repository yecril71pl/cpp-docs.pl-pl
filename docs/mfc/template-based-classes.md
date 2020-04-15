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
ms.openlocfilehash: 29f5f815b62835aedbca1f79b797f826ea53d83b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370455"
---
# <a name="template-based-classes"></a>Klasy oparte na szablonach

W tym artykule wyjaśniono klasy kolekcji oparte na szablonie typu w wersji MFC 3.0 i nowszych. Korzystanie z tych szablonów do tworzenia kolekcji typu bezpieczne jest wygodniejsze i pomaga zapewnić bezpieczeństwo typów bardziej efektywnie niż przy użyciu klas kolekcji nie na podstawie szablonów.

MFC wstępnie definiuje dwie kategorie kolekcji opartych na szablonie:

- [Proste klasy tablic, list i map](#_core_using_simple_array.2c_.list.2c_.and_map_templates)

   `CArray`, `CList`, `CMap`

- [Tablice, listy i mapy wpisanych wskaźników](#_core_using_typed.2d.pointer_collection_templates)

   `CTypedPtrArray`, `CTypedPtrList`, `CTypedPtrMap`

Klasy kolekcji prostej są `CObject`wyprowadzane z klasy, więc dziedziczą serializację, `CObject`tworzenie dynamiczne i inne właściwości programu . Klasy kolekcji wskaźników maszynowych wymagają określenia klasy, z której pochodzisz — która musi być jedną z kolekcji wskaźników `CPtrList` nontemplate wstępnie zdefiniowanych przez MFC, takich jak . `CPtrArray` Nowa klasa kolekcji dziedziczy z określonej klasy podstawowej, a funkcje członkowskie nowej klasy używają zhermetyzowanych wywołań do elementów członkowskich klasy podstawowej, aby wymusić bezpieczeństwo typu.

Aby uzyskać więcej informacji na temat szablonów języka C++, zobacz [Szablony](../cpp/templates-cpp.md) w *odwołaniu do języka języka języka C++*.

## <a name="using-simple-array-list-and-map-templates"></a><a name="_core_using_simple_array.2c_.list.2c_.and_map_templates"></a>Korzystanie z prostych szablonów tablic, list i map

Aby użyć szablonów kolekcji proste, należy wiedzieć, jakiego rodzaju danych można przechowywać w tych kolekcjach i jakie parametry do użycia w deklaracjach kolekcji.

### <a name="simple-array-and-list-usage"></a><a name="_core_simple_array_and_list_usage"></a>Proste użycie tablicy i listy

Proste klasy tablicy i listy, [CArray](../mfc/reference/carray-class.md) i [CList](../mfc/reference/clist-class.md), przyjmują dwa parametry: *TYPE* i `ARG_TYPE`. Te klasy mogą przechowywać dowolny typ danych, który można określić w *parametrze TYPE:*

- Podstawowe typy danych języka C++, takie jak **int**, **char**i **float**

- Struktury i klasy języka C++

- Inne typy zdefiniowane

Dla wygody i wydajności można użyć *parametru ARG_TYPE,* aby określić typ argumentów funkcji. Zazwyczaj należy określić *ARG_TYPE* jako odwołanie do typu, który został nazwany w *parametrze TYPE.* Przykład:

[!code-cpp[NVC_MFCCollections#1](../mfc/codesnippet/cpp/template-based-classes_1.cpp)]

Pierwszy przykład deklaruje kolekcję `myArray`tablic, która zawiera **int**s. Drugi przykład deklaruje kolekcję `myList`listy, `CPerson` , która przechowuje obiekty. Niektóre funkcje członkowskie klas kolekcji wziąć argumenty, których typ jest określony przez *ARG_TYPE* parametr szablonu. Na przykład `Add` funkcja elementu `CArray` członkowskiego klasy przyjmuje *argument ARG_TYPE:*

[!code-cpp[NVC_MFCCollections#2](../mfc/codesnippet/cpp/template-based-classes_2.cpp)]

### <a name="simple-map-usage"></a><a name="_core_simple_map_usage"></a>Proste użycie mapy

Prosta klasa mapy, [CMap](../mfc/reference/cmap-class.md), przyjmuje cztery parametry: *KEY*, *ARG_KEY*, *VALUE*i *ARG_VALUE*. Podobnie jak klasy tablicy i listy, klasy mapy mogą przechowywać dowolny typ danych. W przeciwieństwie do tablic i list, które indeksują i porządkują dane, które przechowują, mapy kojarzą klucze i wartości: uzyskujesz dostęp do wartości przechowywanej na mapie, określając skojarzony klucz wartości. Parametr *KEY* określa typ danych kluczy używanych do uzyskiwania dostępu do danych przechowywanych na mapie. Jeśli *typem KEY* jest struktura lub klasa, *parametr ARG_KEY* jest zazwyczaj odwołaniem do typu określonego w *key*. Parametr *WARTOŚĆ* określa typ elementów przechowywanych na mapie. Jeśli typem *ARG_VALUE* jest struktura lub klasa, *parametr ARG_VALUE* jest zazwyczaj odwołaniem do typu określonego w *wartości*. Przykład:

[!code-cpp[NVC_MFCCollections#3](../mfc/codesnippet/cpp/template-based-classes_3.cpp)]

Pierwszy przykład `MY_STRUCT` przechowuje wartości, uzyskuje do nich dostęp `MY_STRUCT` za pomocą kluczy **int** i zwraca dostęp do elementów przez odwołanie. Drugi przykład `CPerson` przechowuje wartości, `CString` uzyskuje do nich dostęp za pomocą kluczy i zwraca odwołania do elementów, do których dostęp. Ten przykład może reprezentować prostą książkę adresową, w której wyszukujesz osoby według nazwiska.

Ponieważ parametr *KEY* jest `CString` typu i *parametr KEY_TYPE* jest `LPCSTR`typu, klucze są przechowywane na `CString` mapie jako elementy typu, ale są odwoływane w funkcjach, takich jak `SetAt` za pośrednictwem wskaźników typu `LPCSTR`. Przykład:

[!code-cpp[NVC_MFCCollections#4](../mfc/codesnippet/cpp/template-based-classes_4.cpp)]

## <a name="using-typed-pointer-collection-templates"></a><a name="_core_using_typed.2d.pointer_collection_templates"></a>Korzystanie z szablonów kolekcji typed-pointer

Aby użyć szablonów kolekcji wpisanych wskaźników, musisz wiedzieć, jakie rodzaje danych można przechowywać w tych kolekcjach i jakie parametry mają być używane w deklaracjach kolekcji.

### <a name="typed-pointer-array-and-list-usage"></a><a name="_core_typed.2d.pointer_array_and_list_usage"></a>Typed-Pointer Array i użycie listy

Klasy tablicy i listy wpisanych wskaźników, [CTypedPtrArray](../mfc/reference/ctypedptrarray-class.md) i [CTypedPtrList,](../mfc/reference/ctypedptrlist-class.md)przyjmują dwa parametry: *BASE_CLASS* i *TYP*. Te klasy mogą przechowywać dowolny typ danych, który można określić w *TYPE* parametru. Pochodzą one z jednej z klas kolekcji nontemplate, która przechowuje wskaźniki; tę klasę podstawową można określić w *BASE_CLASS*. W przypadku tablic należy `CObArray` `CPtrArray`użyć jednego lub . W przypadku list `CObList` użyj `CPtrList`jednego lub .

W efekcie podczas deklarowania kolekcji `CObList`na podstawie, powiedzmy, nowa klasa nie tylko dziedziczy członków swojej klasy podstawowej, ale również deklaruje szereg dodatkowych funkcji elementów członkowskich bezpiecznych dla typu i operatorów, które pomagają zapewnić bezpieczeństwo typu przez hermetyzowanie wywołań do elementów członkowskich klasy podstawowej. Te hermetacje zarządzają wszystkie niezbędne konwersji typu. Przykład:

[!code-cpp[NVC_MFCCollections#5](../mfc/codesnippet/cpp/template-based-classes_5.cpp)]

W pierwszym przykładzie deklaruje tablicę `myArray`wpisywany `CObArray`wskaźnik, wywodzącą się z . Tablica przechowuje i `CPerson` zwraca wskaźniki `CPerson` do obiektów (gdzie jest klasą pochodną `CObject`). Można wywołać `CObArray` dowolną funkcję elementu członkowskiego lub można `GetAt` `ElementAt` wywołać nowy typ bezpieczne i funkcje lub użyć operatora typu bezpieczne **[ ].**

Drugi przykład deklaruje listę wpisanych `myList`wskaźników, `CPtrList`wywodzącą się z pliku . Lista przechowuje i zwraca `MY_STRUCT` wskaźniki do obiektów. Klasa oparta `CPtrList` na jest używana do przechowywania wskaźników `CObject`do obiektów, które nie pochodzą od . `CTypedPtrList`posiada szereg funkcji elementów członkowskich `GetHead` `GetTail`bezpiecznych dla typu: `RemoveHead`, , , `RemoveTail` `GetNext`, , `GetPrev`, i `GetAt`.

### <a name="typed-pointer-map-usage"></a><a name="_core_typed.2d.pointer_map_usage"></a>Użycie mapy typu wskaźnik

Klasa mapy wpisywany wskaźnik, [CTypedPtrMap](../mfc/reference/ctypedptrmap-class.md), przyjmuje trzy parametry: *BASE_CLASS*, *KEY*i *VALUE*. Parametr *BASE_CLASS* określa klasę, z której ma pochodzić nowa `CMapPtrToWord` `CMapPtrToPtr`klasa: `CMapWordToPtr`, , `CMapStringToOb` `CMapStringToPtr`, , i tak dalej. *KEY* jest analogiczny `CMap`do *keyw* : Określa typ klucza używanego do wyszukiwania. *WARTOŚĆ* jest *analogiczna* `CMap`do wartości w : Określa typ obiektu przechowywanego na mapie. Przykład:

[!code-cpp[NVC_MFCCollections#6](../mfc/codesnippet/cpp/template-based-classes_6.cpp)]

Pierwszym przykładem jest mapa `CMapPtrToPtr` oparta `CString` na — używa klawiszy mapowanych do wskaźników do `MY_STRUCT`. Można wyszukać zapisany wskaźnik, wywołując `Lookup` funkcję bezpiecznego typu elementu członkowskiego. Operator [ **]** służy do wyszukiwania zapisanego wskaźnika i dodawania go, jeśli nie został znaleziony. Możesz iterować mapę za pomocą `GetNextAssoc` funkcji bezpiecznego typu. Można również wywołać inne `CMapPtrToPtr`funkcje członkowskie klasy .

Drugi przykład to mapa `CMapStringToOb` oparta na — używa kluczy ciągów mapowanych do przechowywanych wskaźników do `CMyObject` obiektów. Można użyć tych samych elementów członkowskich typu, które opisano w `CMapStringToOb`poprzednim akapicie, lub można wywołać członków klasy .

> [!NOTE]
> Jeśli określisz **klasę** lub typ **struktury** dla parametru *VALUE,* a nie wskaźnik lub odwołanie do typu, klasa lub struktura musi mieć konstruktora kopii.

Aby uzyskać więcej informacji, zobacz [Jak zrobić kolekcję bezpieczną](../mfc/how-to-make-a-type-safe-collection.md)dla typu .

## <a name="see-also"></a>Zobacz też

[Kolekcje](../mfc/collections.md)
