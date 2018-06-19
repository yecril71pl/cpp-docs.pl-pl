---
title: 'Serializacja: Ustawianie klasy jako możliwy do serializacji | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4412e8db861ac522c0f1b1d7192bfbb83612d64c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33383419"
---
# <a name="serialization-making-a-serializable-class"></a>Serializacja: ustawianie klasy jako możliwej do serializacji
Pięć głównych kroków są wymagane dokonanie klasę serializacji. Są one wymienione poniżej i wyjaśnione w poniższych sekcjach:  
  
1.  [Wyprowadzanie klasy z obiektu CObject](#_core_deriving_your_class_from_cobject) (niektóre klasę pochodną lub z `CObject`).  
  
2.  [Zastępowanie funkcji Członkowskich serializacja](#_core_overriding_the_serialize_member_function).  
  
3.  [Przy użyciu declare_serial — makro](#_core_using_the_declare_serial_macro) w deklaracji klasy.  
  
4.  [Definiowanie konstruktora, który nie przyjmuje żadnych argumentów](#_core_defining_a_constructor_with_no_arguments).  
  
5.  [Przy użyciu implement_serial — makro w pliku implementacji](#_core_using_the_implement_serial_macro_in_the_implementation_file) dla klasy.  
  
 Jeśli należy wywołać `Serialize` bezpośrednio, a nie za pomocą >> i << operatorów [CArchive](../mfc/reference/carchive-class.md), ostatnie trzy kroki nie są wymagane do serializacji.  
  
##  <a name="_core_deriving_your_class_from_cobject"></a> Wyprowadzanie klasy z obiektu CObject  
 Protokół serializacji podstawowe i funkcje, które są zdefiniowane w `CObject` klasy. Przez wyprowadzanie klasy z `CObject` (lub z klasy pochodzącej od `CObject`), jak pokazano w poniższych deklaracja klasy `CPerson`, uzyskasz dostęp do serializacji protokołu i funkcjonalność `CObject`.  
  
##  <a name="_core_overriding_the_serialize_member_function"></a> Zastępowanie serializować funkcji członkowskiej  
 `Serialize` Funkcji członkowskiej, która jest zdefiniowana w `CObject` klasa, jest odpowiedzialny za faktycznie serializacji dane niezbędne do przechwytywania bieżącego stanu obiektu. `Serialize` Funkcja ma `CArchive` argument używaną do odczytywania i zapisywania danych obiektu. [CArchive](../mfc/reference/carchive-class.md) obiekt ma funkcją członkowską `IsStoring`, która wskazuje, czy `Serialize` jest przechowywanie (zapisywania danych) lub ładowania (Odczyt danych). Przy użyciu wyniki `IsStoring` jako przewodnik, albo wstawiania danych do obiektu w `CArchive` obiektu z operatorem wstawiania (**<\<**) lub wyodrębniania danych z operatorów wyodrębniania ( **>>**).  
  
 Należy wziąć pod uwagę klasę, która jest pochodną `CObject` i ma dwie nowe zmienne Członkowskie, typów `CString` i **WORD**. Poniższy fragment deklaracji klasy zawiera nowy element członkowski zmiennych i deklaracja przesłoniętych `Serialize` funkcji członkowskiej:  
  
 [!code-cpp[NVC_MFCSerialization#1](../mfc/codesnippet/cpp/serialization-making-a-serializable-class_1.h)]  
  
#### <a name="to-override-the-serialize-member-function"></a>Aby zastąpić serializacja funkcji członkowskiej  
  
1.  Wywołaj wersja klasy podstawowej `Serialize` aby upewnić się, że serializowany jest dziedziczone część obiektu.  
  
2.  Wstawianie lub Wyodrębnij zmienne Członkowskie specyficzne dla klasy.  
  
     Z operatorów wstawiania i wyodrębniania interakcji z klasy archiwum do odczytywania i zapisywania danych. Poniższy przykład przedstawia sposób wykonania `Serialize` dla `CPerson` klasy zadeklarowany powyżej:  
  
     [!code-cpp[NVC_MFCSerialization#2](../mfc/codesnippet/cpp/serialization-making-a-serializable-class_2.cpp)]  
  
 Można również użyć [CArchive::Read](../mfc/reference/carchive-class.md#read) i [CArchive::Write](../mfc/reference/carchive-class.md#write) funkcji elementów członkowskich do odczytywania i zapisywania dużych ilości danych bez typu.  
  
##  <a name="_core_using_the_declare_serial_macro"></a> Przy użyciu declare_serial — makro  
 `DECLARE_SERIAL` Makro jest wymagany w deklaracji klasy, które będą obsługiwać serializacji, jak pokazano poniżej:  
  
 [!code-cpp[NVC_MFCSerialization#3](../mfc/codesnippet/cpp/serialization-making-a-serializable-class_3.h)]  
  
##  <a name="_core_defining_a_constructor_with_no_arguments"></a> Definiowanie konstruktora bez argumentów  
 Gdy ponownie program tworzy obiektów, ponieważ są one rozszeregować (ładowanych z dysku), MFC wymaga konstruktora domyślnego. Proces deserializacji wypełni wszystkie zmienne Członkowskie przy użyciu wartości wymagane ponownie utworzyć obiekt.  
  
 Ten konstruktor może być deklarowana publicznych, chronionych lub prywatnych. Jeśli będzie to chronionych lub prywatnych, pomocy, upewnij się, że będzie tylko służyć za pomocą funkcji serializacji. Konstruktor umieścić obiekt w stanie, który umożliwi można usunąć, jeśli to konieczne.  
  
> [!NOTE]
>  Jeśli zapomnisz do definiowania konstruktora bez argumentów w klasie, która używa `DECLARE_SERIAL` i `IMPLEMENT_SERIAL` makra, zostanie wyświetlone ostrzeżenie kompilatora "Brak domyślnego konstruktora dostępne" w wierszu gdzie `IMPLEMENT_SERIAL` makro jest używane.  
  
##  <a name="_core_using_the_implement_serial_macro_in_the_implementation_file"></a> W pliku implementacji przy użyciu implement_serial — makro  
 `IMPLEMENT_SERIAL` Makro jest używane do definiowania różnych funkcji wymagane podczas serializacji klasa wyprowadzona z `CObject`. Używanie tego makra w pliku implementacji (. CPP) dla klasy. Pierwsze dwa argumenty makra są nazwę klasy i nazwę swojej klasy podstawowej bezpośrednim.  
  
 Trzeci argument to makro jest liczbą schematu. Liczba schematu jest zasadniczo numer wersji dla obiektów klasy. Użyj liczba całkowita większa lub równa 0, dla liczby schematu. (Nie należy mylić numer ten schemat terminologii bazy danych.)  
  
 Kod serializacji MFC sprawdza numer schematu podczas odczytywania obiektów do pamięci. Jeśli numer schematu obiektu na dysku odpowiada numerowi schematu klasy w pamięci, zgłosi biblioteki `CArchiveException`, uniemożliwia odczytywania obiektu nieprawidłową wersję programu.  
  
 Jeśli chcesz z `Serialize` funkcji członkowskiej, aby można było odczytać wielu wersji — oznacza to, że pliki zapisywane z różnymi wersjami aplikacji — można użyć wartości **versionable_schema —** jako argument `IMPLEMENT_SERIAL` makra. Informacje o użyciu i przykładem, zobacz `GetObjectSchema` funkcji członkowskiej klasy `CArchive`.  
  
 Poniższy przykład przedstawia użycie `IMPLEMENT_SERIAL` dla klasy, `CPerson`, która jest pochodną `CObject`:  
  
 [!code-cpp[NVC_MFCSerialization#4](../mfc/codesnippet/cpp/serialization-making-a-serializable-class_4.cpp)]  
  
 Po utworzeniu klasy możliwej do serializacji, może serializować obiektów klasy, zgodnie z opisem w artykule [serializacja: serializacja obiektu](../mfc/serialization-serializing-an-object.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Serializacja](../mfc/serialization-in-mfc.md)

