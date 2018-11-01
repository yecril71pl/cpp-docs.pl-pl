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
ms.openlocfilehash: 8bd64e1c5efd1f80f43cb3460719326f30d5416c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50557862"
---
# <a name="template-based-classes"></a>Klasy oparte na szablonach

W tym artykule opisano klasy kolekcji oparte na szablonach bezpieczny w MFC w wersji 3.0 lub nowszej. Tworzenie bezpiecznej kolekcji przy użyciu tych szablonów jest bardziej wygodne i pomaga zapewnić bezpieczeństwo typów bardziej efektywne niż używanie klas kolekcji nie są oparte na szablonach.

MFC powoduje wstępne definiowanie dwie kategorie kolekcje oparte na szablonach:

- [Proste array, list i klasy map](#_core_using_simple_array.2c_.list.2c_.and_map_templates)

   `CArray`, `CList`, `CMap`

- [Tablic, list i map wskaźniki typizowane](#_core_using_typed.2d.pointer_collection_templates)

   `CTypedPtrArray`, `CTypedPtrList`, `CTypedPtrMap`

Klasy kolekcji proste są uzyskiwane z klasy `CObject`, dlatego dziedziczą serializacji, dynamiczne tworzenie i inne właściwości `CObject`. Klasy kolekcji typizowanych wskaźników wymaga określenia klasy pochodzić od — która musi być jedna z kolekcji wskaźnika nieszablonu wstępnie zdefiniowane przez MFC, takich jak `CPtrList` lub `CPtrArray`. Nowej klasie kolekcji dziedziczy z określonej klasy bazowej, a funkcje składowych klasy nowe zhermetyzowany wywołania do składowych klasy bazowej są używane do wymuszania bezpieczeństwo typów.

Aby uzyskać więcej informacji na temat szablonów języka C++, zobacz [szablony](../cpp/templates-cpp.md) w *C++ Language Reference*.

##  <a name="_core_using_simple_array.2c_.list.2c_.and_map_templates"></a> Za pomocą prostej tablicy, listy i szablony mapy

Za pomocą szablonów prostych kolekcji, musisz wiedzieć, jakiego rodzaju dane można przechowywać w tych kolekcjach i podać parametry do użycia w deklaracjach Twojej kolekcji.

###  <a name="_core_simple_array_and_list_usage"></a> Tablica proste i listy, obciążenie

Prostej tablicy i lista klas [CArray](../mfc/reference/carray-class.md) i [CList](../mfc/reference/clist-class.md), przyjmują dwa parametry: *typu* i `ARG_TYPE`. Te klasy można przechowywać dowolny typ danych, które jest określane w *typu* parametru:

- Typy danych podstawowych języka C++, takie jak **int**, **char**, i **float**

- Klasy i struktury języka C++

- Innych typów zdefiniowanych przez użytkownika

Dla wygody i wydajność, można użyć *ARG_TYPE* parametru, aby określić typ argumentów funkcji. Zazwyczaj można określić *ARG_TYPE* jako odwołanie do typu, nosi nazwę w *typu* parametru. Na przykład:

[!code-cpp[NVC_MFCCollections#1](../mfc/codesnippet/cpp/template-based-classes_1.cpp)]

Pierwszy przykład deklaruje tablicę kolekcji, `myArray`, który zawiera **int**s. Drugi przykład deklaruje kolekcję listy `myList`, który przechowuje `CPerson` obiektów. Niektóre funkcje Członkowskie klas kolekcji zająć argumentów, którego typ jest określony przez *ARG_TYPE* parametru szablonu. Na przykład `Add` funkcji składowej klasy typu `CArray` przyjmuje *ARG_TYPE* argumentu:

[!code-cpp[NVC_MFCCollections#2](../mfc/codesnippet/cpp/template-based-classes_2.cpp)]

###  <a name="_core_simple_map_usage"></a> Użycie proste mapy

Klasa proste mapy [CMap](../mfc/reference/cmap-class.md), przyjmuje cztery parametry: *klucz*, *ARG_KEY*, *wartość*, i *ARG_VALUE*. Jak tablicy i listy klasy klasy map może przechowywać dowolny typ danych. W odróżnieniu od tablicami i listami, które indeksu i kolejność danych są przechowywane, map kojarzenie kluczy i wartości: możesz uzyskać dostęp do wartości przechowywanego w mapie, określając wartość skojarzonego klucza. *Klucz* parametr określa typ danych, klucze używane do dostępu do danych przechowywanych w mapie. Jeśli typ *klucz* struktury lub klasy, *ARG_KEY* parametr jest zazwyczaj odwołanie do typu określonego w *klucz*. *Wartość* parametr określa typ elementów przechowywany w mapie. Jeśli typ *ARG_VALUE* struktury lub klasy, *ARG_VALUE* parametr jest zazwyczaj odwołanie do typu określonego w *wartość*. Na przykład:

[!code-cpp[NVC_MFCCollections#3](../mfc/codesnippet/cpp/template-based-classes_3.cpp)]

Pierwszy przykład magazynów `MY_STRUCT` wartości, uzyskuje dostęp do nich przez **int** kluczy i zwraca dostępne `MY_STRUCT` elementów według odwołania. Drugi przykład magazynów `CPerson` wartości, uzyskuje dostęp do nich przez `CString` kluczy, a następnie zwraca odwołania do używanych elementów. W tym przykładzie może reprezentować proste książki adresowej programu, w którym można wyszukać osób według nazwiska.

Ponieważ *klucz* parametr jest typu `CString` i *KEY_TYPE* parametr jest typu `LPCSTR`, klucze są przechowywane w mapie jako elementy typu `CString` , ale są przywoływane w funkcje takie jak `SetAt` za pomocą wskaźników typu `LPCSTR`. Na przykład:

[!code-cpp[NVC_MFCCollections#4](../mfc/codesnippet/cpp/template-based-classes_4.cpp)]

##  <a name="_core_using_typed.2d.pointer_collection_templates"></a> Za pomocą szablonów kolekcji kontrolą typów wskaźnika

Za pomocą szablonów kolekcji wpisane wskaźnika, musisz wiedzieć, jakiego rodzaju dane można przechowywać w tych kolekcjach i podać parametry do użycia w deklaracjach Twojej kolekcji.

###  <a name="_core_typed.2d.pointer_array_and_list_usage"></a> Wpisane wskaźnika tablicy i listy, obciążenie

Wpisane wskaźnika tablicy i lista klas [CTypedPtrArray](../mfc/reference/ctypedptrarray-class.md) i [CTypedPtrList](../mfc/reference/ctypedptrlist-class.md), przyjmują dwa parametry: *element $base_class* i *typu*. Te klasy można przechowywać dowolny typ danych, które jest określane w *typu* parametru. Wywodzą się z jednej z klas kolekcji nieszablonu, które przechowuje wskaźniki; Określ tej klasy podstawowej w *element $base_class*. Dla tablic, użyj `CObArray` lub `CPtrArray`. W przypadku list, użyj `CObList` lub `CPtrList`.

W efekcie powiedzieć deklarując kolekcję na podstawie `CObList`, Nowa klasa dziedziczy nie tylko elementy członkowskie klasy bazowej, ale także program deklaruje szereg dodatkowych członków bezpieczne funkcje i operatory, które pomagają zapewnić bezpieczeństwo typów poprzez hermetyzację wywołania do składowych klasy bazowej. Te encapsulations Zarządzanie wszystkich konwersji typu niezbędne. Na przykład:

[!code-cpp[NVC_MFCCollections#5](../mfc/codesnippet/cpp/template-based-classes_5.cpp)]

Pierwszy przykład deklaruje tablicę wpisane wskaźnika `myArray`, pochodzącej z `CObArray`. Tablica przechowuje i zwraca wskaźniki do `CPerson` obiektów (gdzie `CPerson` jest klasa jest pochodną `CObject`). Może wywoływać dowolną `CObArray` funkcja elementu członkowskiego lub wywołując nowe bezpieczny `GetAt` i `ElementAt` funkcje lub Użyj bezpiecznego typu **[** operatora.

Drugi przykład deklaruje listę wpisane wskaźnika `myList`, pochodzącej z `CPtrList`. Listy są przechowywane i zwraca wskaźniki do `MY_STRUCT` obiektów. Na podstawie klasy `CPtrList` służy do przechowywania wskaźników do obiektów nie pochodzi od `CObject`. `CTypedPtrList` zawiera liczbę elementów członkowskich bezpieczny: `GetHead`, `GetTail`, `RemoveHead`, `RemoveTail`, `GetNext`, `GetPrev`, i `GetAt`.

###  <a name="_core_typed.2d.pointer_map_usage"></a> Użycie wskaźnika wpisane mapy

Klasa wpisana wskaźnika map [CTypedPtrMap](../mfc/reference/ctypedptrmap-class.md), przyjmuje trzy parametry: *element $base_class*, *klucz*, i *wartość*. *Element $base_class* parametr określa klasę, z których mają być pochodzić nowa klasa: `CMapPtrToWord`, `CMapPtrToPtr`, `CMapStringToPtr`, `CMapWordToPtr`, `CMapStringToOb`i tak dalej. *KLUCZ* jest odpowiednikiem *klucz* w `CMap`: Określa typ klucza, używany do wyszukiwania. *WARTOŚĆ* jest odpowiednikiem *wartość* w `CMap`: Określa typ obiektu, przechowywany w mapie. Na przykład:

[!code-cpp[NVC_MFCCollections#6](../mfc/codesnippet/cpp/template-based-classes_6.cpp)]

Pierwszy przykład jest mapy na podstawie `CMapPtrToPtr` — używa ona `CString` klucze mapowane do wskaźników do `MY_STRUCT`. Możesz wyszukać przechowywany wskaźnik, wywołując bezpieczne `Lookup` funkcja elementu członkowskiego. Możesz użyć **[** operator, aby wyszukać przechowywany wskaźnik i dodać go, jeśli nie znajdzie. I można wykonać iterację mapy przy użyciu bezpiecznego typu `GetNextAssoc` funkcji. Można również wywołać inny członek funkcje klasy `CMapPtrToPtr`.

Drugi przykład jest mapy na podstawie `CMapStringToOb` — korzysta z kluczy ciągu mapowane do przechowywanej wskaźników do `CMyObject` obiektów. Możesz użyć tych samych bezpiecznegop typu elementów członkowskich opisane w poprzednim akapicie lub może wywołać składowe klasy `CMapStringToOb`.

> [!NOTE]
>  Jeśli określisz **klasy** lub **struktury** wpisz *wartość* parametru, a nie wskaźnik lub odwołanie do typu, klasę lub strukturę musi mieć konstruktora kopiującego.

Aby uzyskać więcej informacji, zobacz [jak tworzenie kolekcji bezpieczny](../mfc/how-to-make-a-type-safe-collection.md).

## <a name="see-also"></a>Zobacz też

[Kolekcje](../mfc/collections.md)

