---
title: 'Serializacja: ustawianie klasy jako możliwej do serializacji'
ms.date: 11/04/2016
helpviewer_keywords:
- serializable class [MFC]
- DECLARE_SERIAL macro [MFC]
- default constructor [MFC]
- VERSIONABLE_SCHEMA macro [MFC]
- classes [MFC], derived
- IMPLEMENT_SERIAL macro [MFC]
- no-arguments constructor [MFC]
- Serialize method, overriding
- defaults [MFC], constructor
- CObject class [MFC], deriving serializable classes
- constructors [MFC], defining with no arguments
- serialization [MFC], serializable classes
- no default constructor
ms.assetid: 59a14d32-1cc8-4275-9829-99639beee27c
ms.openlocfilehash: 9648bd4f516a5f174534336b1ca3b42bb51ca0c4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372703"
---
# <a name="serialization-making-a-serializable-class"></a>Serializacja: ustawianie klasy jako możliwej do serializacji

Aby klasa była serializowalna, wymagane jest pięć głównych kroków. Są one wymienione poniżej i wyjaśnione w następujących sekcjach:

1. [Wyprowadzanie klasy z CObject](#_core_deriving_your_class_from_cobject) (lub z `CObject`klasy pochodzącej z ).

1. [Zastępowanie funkcji element członkowski Serialize](#_core_overriding_the_serialize_member_function).

1. [Za pomocą makra DECLARE_SERIAL](#_core_using_the_declare_serial_macro) w deklaracji klasy.

1. [Definiowanie konstruktora, który nie ma żadnych argumentów](#_core_defining_a_constructor_with_no_arguments).

1. [Korzystanie z makra IMPLEMENT_SERIAL w pliku implementacji](#_core_using_the_implement_serial_macro_in_the_implementation_file) dla klasy.

Jeśli wywołasz `Serialize` bezpośrednio, a nie za pośrednictwem >> i << operatorów [CArchive,](../mfc/reference/carchive-class.md)ostatnie trzy kroki nie są wymagane do serializacji.

## <a name="deriving-your-class-from-cobject"></a><a name="_core_deriving_your_class_from_cobject"></a>Wyprowadzanie klasy z CObject

Podstawowy protokół serializacji i funkcje `CObject` są zdefiniowane w klasie. Poprzez wyprowadzenie `CObject` klasy z (lub `CObject`z klasy pochodnej ), `CPerson`jak pokazano w poniższej deklaracji klasy, `CObject`uzyskujesz dostęp do protokołu serializacji i funkcjonalności .

## <a name="overriding-the-serialize-member-function"></a><a name="_core_overriding_the_serialize_member_function"></a>Zastępowanie funkcji element członkowski Serializuj

Funkcja `Serialize` elementu członkowskiego, która `CObject` jest zdefiniowana w klasie, jest odpowiedzialny za faktycznie serializacji danych niezbędnych do przechwytywania bieżącego stanu obiektu. Funkcja `Serialize` ma `CArchive` argument, który używa do odczytu i zapisu danych obiektu. [CArchive](../mfc/reference/carchive-class.md) obiekt ma funkcję `IsStoring`elementu członkowskiego, `Serialize` który wskazuje, czy jest przechowywanie (zapisywanie danych) lub ładowania (odczyt danych). `IsStoring` Korzystając z wyników jako przewodnika, należy wstawić dane `CArchive` obiektu do obiektu za**<** pomocą operatora wstawiania**>>**( ) lub wyodrębnić dane z operatorem ekstrakcji ( ).

Należy wziąć pod uwagę `CObject` klasę, która pochodzi od i `CString` ma dwie nowe zmienne członkowskie, typów i **WORD**. Następujący fragment deklaracji klasy pokazuje nowe zmienne członkowskie i `Serialize` deklarację dla funkcji nadrzędnego elementu członkowskiego:

[!code-cpp[NVC_MFCSerialization#1](../mfc/codesnippet/cpp/serialization-making-a-serializable-class_1.h)]

#### <a name="to-override-the-serialize-member-function"></a>Aby zastąpić funkcję element członkowski Serializuj

1. Wywołanie wersji klasy `Serialize` podstawowej, aby upewnić się, że dziedziczona część obiektu jest serializowana.

1. Wstaw lub wyodrębnij zmienne członkowskie specyficzne dla danej klasy.

   Operatory wstawiania i wyodrębniania współdziałają z klasy archiwum do odczytu i zapisu danych. W poniższym przykładzie `Serialize` pokazano, jak zaimplementować dla `CPerson` klasy zadeklarowanej powyżej:

   [!code-cpp[NVC_MFCSerialization#2](../mfc/codesnippet/cpp/serialization-making-a-serializable-class_2.cpp)]

Można również użyć [CArchive::Read](../mfc/reference/carchive-class.md#read) i [CArchive::Write](../mfc/reference/carchive-class.md#write) funkcji członkowskich do odczytu i zapisu dużych ilości danych bez typu.

## <a name="using-the-declare_serial-macro"></a><a name="_core_using_the_declare_serial_macro"></a>Korzystanie z DECLARE_SERIAL makra

Makro DECLARE_SERIAL jest wymagane w deklaracji klas, które będą obsługiwać serializacji, jak pokazano poniżej:

[!code-cpp[NVC_MFCSerialization#3](../mfc/codesnippet/cpp/serialization-making-a-serializable-class_3.h)]

## <a name="defining-a-constructor-with-no-arguments"></a><a name="_core_defining_a_constructor_with_no_arguments"></a>Definiowanie konstruktora bez argumentów

MFC wymaga domyślnego konstruktora, gdy ponownie tworzy obiekty, ponieważ są one deserializowane (ładowane z dysku). Proces deserializacji wypełni wszystkie zmienne członkowskie wartościami wymaganymi do ponownego utworzenia obiektu.

Ten konstruktor może być zadeklarowany jako publiczny, chroniony lub prywatny. Jeśli uczynisz go chronionym lub prywatnym, upewnij się, że będzie używany tylko przez funkcje serializacji. Konstruktor musi umieścić obiekt w stanie, który umożliwia usunięcie go w razie potrzeby.

> [!NOTE]
> Jeśli zapomnisz zdefiniować konstruktora bez argumentów w klasie, która używa makr DECLARE_SERIAL i IMPLEMENT_SERIAL, otrzymasz ostrzeżenie kompilatora "nie ma domyślnego konstruktora dostępnego" w wierszu, w którym jest używane IMPLEMENT_SERIAL makra.

## <a name="using-the-implement_serial-macro-in-the-implementation-file"></a><a name="_core_using_the_implement_serial_macro_in_the_implementation_file"></a>Korzystanie z IMPLEMENT_SERIAL makra w pliku implementacji

Makro IMPLEMENT_SERIAL służy do definiowania różnych funkcji potrzebnych podczas uzyskiwania klasy `CObject`serializable z . To makro jest używane w pliku implementacji (. CPP) dla Twojej klasy. Pierwsze dwa argumenty makra to nazwa klasy i nazwa jej bezpośredniej klasy podstawowej.

Trzecim argumentem tego makra jest numer schematu. Numer schematu jest zasadniczo numer wersji dla obiektów klasy. Użyj liczby całkowitej większej lub równej 0 dla numeru schematu. (Nie należy mylić tego numeru schematu z terminologią bazy danych).

Kod serializacji MFC sprawdza numer schematu podczas odczytywania obiektów do pamięci. Jeśli numer schematu obiektu na dysku nie jest zgodny z numerem schematu klasy `CArchiveException`w pamięci, biblioteka zrzuci program , uniemożliwiając programowi odczytanie niepoprawnej wersji obiektu.

Jeśli chcesz, `Serialize` aby funkcja elementu członkowskiego mogła odczytywać wiele wersji — czyli plików napisanych różnymi wersjami aplikacji — możesz użyć wartości *VERSIONABLE_SCHEMA* jako argumentu do makra IMPLEMENT_SERIAL. Aby uzyskać informacje o użyciu `GetObjectSchema` i przykład, zobacz funkcję elementu członkowskiego klasy `CArchive`.

W poniższym przykładzie pokazano, jak używać `CPerson`IMPLEMENT_SERIAL dla klasy, `CObject`która pochodzi od:

[!code-cpp[NVC_MFCSerialization#4](../mfc/codesnippet/cpp/serialization-making-a-serializable-class_4.cpp)]

Po uzyskaniu klasy serializable można serializować obiekty klasy, jak omówiono w artykule [Serializacja: Serializacja obiektu](../mfc/serialization-serializing-an-object.md).

## <a name="see-also"></a>Zobacz też

[Serializacja](../mfc/serialization-in-mfc.md)
