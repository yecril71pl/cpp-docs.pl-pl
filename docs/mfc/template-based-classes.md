---
title: Klasy oparte na szablonach | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 68d44a66f328465f2c59fb361f9bb6b2a76efa82
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33385477"
---
# <a name="template-based-classes"></a>Klasy oparte na szablonach
W tym artykule opisano klasy bezpiecznej kolekcji na podstawie szablonu w wersji 3.0 i nowszych MFC. Tworzenie bezpiecznej kolekcji za pomocą tych szablonów jest bardziej wygodne i pomaga zapewnić bezpieczeństwo typów efektywniej niż używanie klasy kolekcji nie są oparte na szablonach.  
  
 MFC powoduje wstępne definiowanie dwie kategorie kolekcje oparte na szablonach:  
  
-   [Proste tablic, list i klasy map](#_core_using_simple_array.2c_.list.2c_.and_map_templates)  
  
     `CArray`, `CList`, `CMap`  
  
-   [Tablic, list i map wskaźniki typizowane](#_core_using_typed.2d.pointer_collection_templates)  
  
     `CTypedPtrArray`, `CTypedPtrList`, `CTypedPtrMap`  
  
 Klasy kolekcji proste są uzyskiwane z klasy `CObject`, dlatego dziedziczą serializacji, tworzenie dynamicznych i inne właściwości `CObject`. Klasy kolekcji typizowaną wskaźnika wymaga określenia klasa pochodzi od — które muszą być kolekcji wskaźnika nieszablonu wstępnie zdefiniowane przez MFC, takich jak `CPtrList` lub `CPtrArray`. Nowej klasy kolekcji dziedziczy od określonej klasy podstawowej, a funkcje Członkowskie nowa klasa hermetyzowany wywołania do elementów członkowskich klasy podstawowej są używane do wymuszania bezpieczeństwa typu.  
  
 Aby uzyskać więcej informacji na temat szablonów języka C++, zobacz [szablony](../cpp/templates-cpp.md) w *dokumentacja języka C++*.  
  
##  <a name="_core_using_simple_array.2c_.list.2c_.and_map_templates"></a> Przy użyciu prostego tablicy, listy i szablony mapy  
 Aby użyć prostych kolekcji szablonów, należy wiedzieć, jakiego rodzaju dane można przechowywać w tych kolekcjach jakich parametrów do użycia w deklaracji z kolekcji.  
  
###  <a name="_core_simple_array_and_list_usage"></a> Tablica proste i użycie listy  
 Tablica proste i lista klas [carray —](../mfc/reference/carray-class.md) i [clist —](../mfc/reference/clist-class.md), mieć dwa parametry: *typu* i `ARG_TYPE`. Te klasy można przechowywać dowolny typ danych, które należy określić w *typu* parametru:  
  
-   Typy danych języka C++ podstawowych, takich jak `int`, `char`, i **liczb zmiennoprzecinkowych**  
  
-   Klasy i struktury języka C++  
  
-   Inne typy zdefiniowane przez użytkownika  
  
 Dla wygody i wydajności, można użyć `ARG_TYPE` parametr, aby określić typy argumentów funkcji. Zazwyczaj określić `ARG_TYPE` jako odwołanie do typu wymienionych w *typu* parametru. Na przykład:  
  
 [!code-cpp[NVC_MFCCollections#1](../mfc/codesnippet/cpp/template-based-classes_1.cpp)]  
  
 Pierwszym przykładzie deklaruje kolekcji tablicy `myArray`, który zawiera `int`s. Drugi przykład deklaruje kolekcji list `myList`, który przechowuje `CPerson` obiektów. Niektóre funkcje Członkowskie klas kolekcji przyjmują argumentów, którego typ jest określony przez `ARG_TYPE` parametru szablonu. Na przykład **Dodaj** funkcji członkowskiej klasy `CArray` przyjmuje `ARG_TYPE` argumentu:  
  
 [!code-cpp[NVC_MFCCollections#2](../mfc/codesnippet/cpp/template-based-classes_2.cpp)]  
  
###  <a name="_core_simple_map_usage"></a> Użycie prostego mapy  
 Klasa prostych mapy [CMap](../mfc/reference/cmap-class.md), przyjmuje cztery parametry: *klucza*, `ARG_KEY`, *wartość*, i `ARG_VALUE`. Jak tablicy i listy klas klasy map umożliwia przechowywanie dowolnego typu danych. W odróżnieniu od tablicami i listami, które indeksu i kolejność ich magazyn danych, mapy kojarzenie kluczy i wartości: dostępu wartością przechowywaną w mapowaniu, określając wartość skojarzony klucz. *Klucza* parametr określa typ danych kluczy umożliwiają dostęp do danych przechowywanych na mapie. Jeśli typ *klucza* struktury lub klasy, `ARG_KEY` parametr jest zazwyczaj odwołanie do typu określonego w *klucza*. *Wartość* parametr określa typ elementy przechowywane w planie. Jeśli typ `ARG_VALUE` struktury lub klasy, `ARG_VALUE` parametr jest zazwyczaj odwołanie do typu określonego w *wartość*. Na przykład:  
  
 [!code-cpp[NVC_MFCCollections#3](../mfc/codesnippet/cpp/template-based-classes_3.cpp)]  
  
 Pierwszy magazynów przykład `MY_STRUCT` wartości, uzyskuje dostęp do nich przez `int` kluczy i zwraca dostęp `MY_STRUCT` elementów przez odwołanie. Drugi przykład magazynów `CPerson` wartości, uzyskuje dostęp do nich przez `CString` kluczy i zwraca odwołania do elementów używanych. W tym przykładzie może reprezentować książki adresowej proste, w którym można wyszukać osoby przez nazwisko.  
  
 Ponieważ *klucza* parametr jest typu `CString` i *KEY_TYPE* parametr jest typu `LPCSTR`, że klucze są przechowywane w mapie jako elementy typu `CString` , ale odwołuje się Funkcje, takie jak `SetAt` za pośrednictwem wskaźników typu `LPCSTR`. Na przykład:  
  
 [!code-cpp[NVC_MFCCollections#4](../mfc/codesnippet/cpp/template-based-classes_4.cpp)]  
  
##  <a name="_core_using_typed.2d.pointer_collection_templates"></a> Za pomocą szablonów kolekcji wskaźnik Typizowany  
 Aby użyć szablonów wskaźnik typizowany kolekcji, musisz wiedzieć, jakiego rodzaju dane można przechowywać w tych kolekcjach i jakich parametrów do użycia w deklaracji z kolekcji.  
  
###  <a name="_core_typed.2d.pointer_array_and_list_usage"></a> Wskaźnik typizowany tablicy i użycie listy  
 Wskaźnik typizowany tablicy i lista klas [ctypedptrarray —](../mfc/reference/ctypedptrarray-class.md) i [ctypedptrlist —](../mfc/reference/ctypedptrlist-class.md), mieć dwa parametry: `BASE_CLASS` i *typu*. Te klasy można przechowywać dowolny typ danych, które należy określić w *typu* parametru. Pochodzą z jednego z nieszablonu klasy kolekcji, które przechowuje wskaźników; Określ tej klasy podstawowej w `BASE_CLASS`. Dla tablic, użyj `CObArray` lub `CPtrArray`. Dla listy, użyj `CObList` lub `CPtrList`.  
  
 W efekcie przy deklarowaniu kolekcję na podstawie powiedzieć `CObList`, Nowa klasa dziedziczy nie tylko elementy członkowskie klasy podstawowej, ale także program deklaruje liczbę dodatkowych członków bezpieczne funkcje i operatory, które pomaga zapewnić bezpieczeństwo typów hermetyzując wywołania do elementów członkowskich klasy podstawowej. Te encapsulations Zarządzanie wszystkie niezbędne typ konwersji. Na przykład:  
  
 [!code-cpp[NVC_MFCCollections#5](../mfc/codesnippet/cpp/template-based-classes_5.cpp)]  
  
 Pierwszym przykładzie deklaruje tablicę wskaźnik typizowany `myArray`, pochodną `CObArray`. Tablica przechowuje i zwraca wskaźniki do `CPerson` obiektów (gdzie `CPerson` jest klasa pochodna od `CObject`). Można wywołać żadnego `CObArray` funkcji członkowskiej, lub można wywołać nowe bezpieczne `GetAt` i `ElementAt` funkcje lub użyj bezpieczne **[]** operatora.  
  
 Drugi przykład deklaruje listę wskaźnik typizowany `myList`, pochodną `CPtrList`. Listy są przechowywane i zwraca wskaźniki do `MY_STRUCT` obiektów. Na podstawie klasy `CPtrList` służy do przechowywania wskaźników do obiektów nie pochodzi od `CObject`. `CTypedPtrList` zawiera szereg funkcji Członkowskich bezpieczny: `GetHead`, `GetTail`, `RemoveHead`, `RemoveTail`, `GetNext`, `GetPrev`, i `GetAt`.  
  
###  <a name="_core_typed.2d.pointer_map_usage"></a> Wskaźnik typizowany mapy użycia  
 Klasy map wskaźnik typizowany [ctypedptrmap —](../mfc/reference/ctypedptrmap-class.md), przyjmuje trzy parametry: `BASE_CLASS`, *klucza*, i *wartość*. `BASE_CLASS` Parametr określa klasę, z którego ma pochodzić nową klasę: `CMapPtrToWord`, `CMapPtrToPtr`, `CMapStringToPtr`, `CMapWordToPtr`, `CMapStringToOb`i tak dalej. *KLUCZ* jest odpowiednikiem *klucza* w `CMap`: Określa typ klucz służący do wyszukiwania. *WARTOŚĆ* jest odpowiednikiem *wartość* w `CMap`: Określa typ obiektu przechowywane na mapie. Na przykład:  
  
 [!code-cpp[NVC_MFCCollections#6](../mfc/codesnippet/cpp/template-based-classes_6.cpp)]  
  
 Pierwszym przykładzie jest mapa na podstawie **CMapPtrToPt**r — używa `CString` klucze zamapowane do wskaźników do `MY_STRUCT`. Można wyszukiwać przechowywanych wskaźnika, wywołując bezpieczny `Lookup` funkcję elementu członkowskiego. Można użyć **[** operatora, aby odszukać przechowywanych wskaźnik i dodaj go, jeśli nie znajdzie. I można wykonać iterację mapy, przy użyciu bezpieczne `GetNextAssoc` funkcji. Możesz także wywołać innego członka funkcje klasy `CMapPtrToPtr`.  
  
 Drugi przykład jest mapa na podstawie **CMapStringToO**b — używa kluczy będących ciągami zamapowane do składowanej wskaźników do `CMyObject` obiektów. Można użyć tych samych elementów członkowskich bezpieczne opisane w poprzednim akapicie lub elementy członkowskie klasy można wywołać `CMapStringToOb`.  
  
> [!NOTE]
>  Jeśli określisz **klasy** lub `struct` wpisz *wartość* parametr, a nie wskaźnik lub odwołanie do tego typu, klasę lub strukturę musi mieć konstruktora kopiowania.  
  
 Aby uzyskać więcej informacji, zobacz [porady: tworzenie bezpiecznej kolekcji](../mfc/how-to-make-a-type-safe-collection.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Kolekcje](../mfc/collections.md)

