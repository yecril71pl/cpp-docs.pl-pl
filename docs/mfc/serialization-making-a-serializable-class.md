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
ms.openlocfilehash: aa9a7f6cb1cb28c701e3954cad27e60cf9f7df4f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50486973"
---
# <a name="serialization-making-a-serializable-class"></a>Serializacja: ustawianie klasy jako możliwej do serializacji

Pięć głównych kroków wymaganych do wybierz klasę serializacji. Są one wymienione poniżej i wyjaśnione w poniższych sekcjach:

1. [Wyprowadzanie klasy z obiektu CObject](#_core_deriving_your_class_from_cobject) (niektóre klasę pochodną lub z `CObject`).

1. [Zastępowanie funkcji Członkowskich serializacja](#_core_overriding_the_serialize_member_function).

1. [Za pomocą DECLARE_SERIAL — makro](#_core_using_the_declare_serial_macro) w deklaracji klasy.

1. [Definiowanie konstruktora, który nie przyjmuje żadnych argumentów](#_core_defining_a_constructor_with_no_arguments).

1. [W pliku implementacji przy użyciu IMPLEMENT_SERIAL — makro](#_core_using_the_implement_serial_macro_in_the_implementation_file) dla swojej klasy.

Jeśli wywołasz `Serialize` bezpośrednio, a nie za pomocą >> i << Operatorzy [CArchive](../mfc/reference/carchive-class.md), ostatnie trzy kroki nie są wymagane do serializacji.

##  <a name="_core_deriving_your_class_from_cobject"></a> Wyprowadzanie klasy z obiektu CObject

Serializacja podstawowa protokołu i funkcje, które są zdefiniowane w `CObject` klasy. Przez wyprowadzanie klasy z `CObject` (lub z klasy pochodzącej od `CObject`), jak pokazano w poniższej deklaracji klasy `CPerson`, możesz uzyskać dostęp do serializacji protokołu i funkcjonalność `CObject`.

##  <a name="_core_overriding_the_serialize_member_function"></a> Zastępowanie serializacji funkcji składowej

`Serialize` Funkcja elementu członkowskiego, która jest zdefiniowana w `CObject` klasy, jest odpowiedzialny za faktycznie serializacji dane niezbędne do przechwycenia stanu bieżącego obiektu. `Serialize` Funkcja ma `CArchive` argument, który używa do odczytywania i zapisywania danych obiektu. [CArchive](../mfc/reference/carchive-class.md) obiekt posiada funkcję członkowską `IsStoring`, która wskazuje, czy `Serialize` jest zapisywania (zapisywania danych) i ładowania (odczytywanie danych). Za pomocą wyników `IsStoring` jako przewodnika, albo wstawiania danych do obiektu w `CArchive` obiektu za pomocą operatora wstawiania (**<\<**) lub wyodrębniania danych z operatorów wyodrębniania ( **>>**).

Rozważ klasę, która jest pochodną `CObject` i ma dwa nowe zmiennych składowych typów `CString` i **WORD**. Poniższy fragment deklaracji klasy zawiera nowy element członkowski, zmienne i deklaracji pod kątem zastąpione `Serialize` funkcja elementu członkowskiego:

[!code-cpp[NVC_MFCSerialization#1](../mfc/codesnippet/cpp/serialization-making-a-serializable-class_1.h)]

#### <a name="to-override-the-serialize-member-function"></a>Aby zastąpić serializacja funkcji składowej

1. Wywołaj klasę bazową wersję `Serialize` aby upewnić się, że dziedziczone część obiektu jest serializowana.

1. Wstaw lub Wyodrębnij zmienne Członkowskie specyficzne dla swojej klasy.

   Operatory wstawienia i wydobycia wchodzić w interakcje z klasą archiwum do odczytu i zapisu danych. Poniższy przykład pokazuje, jak zaimplementować `Serialize` dla `CPerson` klasy zadeklarowanej powyżej:

   [!code-cpp[NVC_MFCSerialization#2](../mfc/codesnippet/cpp/serialization-making-a-serializable-class_2.cpp)]

Można również użyć [CArchive::Read](../mfc/reference/carchive-class.md#read) i [CArchive::Write](../mfc/reference/carchive-class.md#write) funkcji elementów członkowskich, aby odczytywać i zapisywać duże ilości danych bez typu.

##  <a name="_core_using_the_declare_serial_macro"></a> Za pomocą DECLARE_SERIAL — makro

DECLARE_SERIAL — makro jest wymagane w deklaracji klasy, które będą obsługiwać serializacji, jak pokazano poniżej:

[!code-cpp[NVC_MFCSerialization#3](../mfc/codesnippet/cpp/serialization-making-a-serializable-class_3.h)]

##  <a name="_core_defining_a_constructor_with_no_arguments"></a> Definiowanie konstruktora bez argumentów

MFC wymaga konstruktora domyślnego, gdy ponownie program tworzy obiekty jako są deserializacji (załadowany z dysku). Proces deserializacji wypełni wszystkie zmienne Członkowskie z wartościami, trzeba ponownie utworzyć obiekt.

Ten konstruktor może być zadeklarowana w publicznych, chronionych lub prywatnych. Jeśli chroniona lub prywatne, pomoc, upewnij się, że jej będą używane tylko przez funkcje serializacji. Konstruktor umieścić obiekt w stanie, który pozwala na usunięcie, jeśli to konieczne.

> [!NOTE]
>  Jeśli nie pamiętasz zdefiniować konstruktor bez argumentów w klasie, która używa DECLARE_SERIAL i IMPLEMENT_SERIAL makra, zostanie wyświetlone ostrzeżenie kompilatora "bez konstruktora domyślnego dostępne" w wierszu, w których jest używana funkcja IMPLEMENT_SERIAL — makro.

##  <a name="_core_using_the_implement_serial_macro_in_the_implementation_file"></a> W pliku implementacji przy użyciu IMPLEMENT_SERIAL — makro

IMPLEMENT_SERIAL — makro jest używane do definiowania różnych funkcji, na potrzeby gdy klasa wyprowadzona z możliwych do serializacji z `CObject`. Użyj tego makra w pliku implementacji (. CPP) dla swojej klasy. Pierwsze dwa argumenty do makra są nazwę klasy i nazwę klasy bazowej natychmiastowe.

Trzeci argument to makro jest liczbą schematu. Liczba schematu jest zasadniczo numer wersji dla obiektów klasy. Liczba całkowita większa lub równa 0 na użytek numer schematu. (Nie pomyl numer ten schemat terminologii bazy danych).

Kod serializacji MFC sprawdza, ile schematu przy odczycie obiektów do pamięci. Jeśli numer schematu obiektu na dysku nie jest zgodna z liczbą schematu, klasy w pamięci, biblioteka zgłosi `CArchiveException`, uniemożliwia odczytywanie nieprawidłową wersję obiektu programu.

Jeśli chcesz, aby Twoje `Serialize` funkcja elementu członkowskiego, aby można było odczytać wielu wersji — oznacza to, że pliki napisanych z użyciem różnych wersji aplikacji — można użyć wartości *VERSIONABLE_SCHEMA* jako argument do IMPLEMENT_SERIAL makra. Aby uzyskać informacje dotyczące użycia i obejrzeć przykład, zobacz `GetObjectSchema` funkcji składowej klasy typu `CArchive`.

Poniższy przykład pokazuje, jak używać IMPLEMENT_SERIAL dla klasy `CPerson`, która jest pochodną `CObject`:

[!code-cpp[NVC_MFCSerialization#4](../mfc/codesnippet/cpp/serialization-making-a-serializable-class_4.cpp)]

Po utworzeniu klasy serializacji, serializacji obiektów klasy, zgodnie z opisem w artykule [serializacja: serializacja obiektu](../mfc/serialization-serializing-an-object.md).

## <a name="see-also"></a>Zobacz też

[Serializacja](../mfc/serialization-in-mfc.md)

