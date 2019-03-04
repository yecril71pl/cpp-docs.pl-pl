---
title: Implementowanie kolekcję C++ Standard Library
ms.date: 11/04/2016
helpviewer_keywords:
- ICollectionOnSTLImpl interface
ms.assetid: 6d49f819-1957-4813-b074-3f12c494d8ca
ms.openlocfilehash: 90583f34c9e9fb500bb48fdbd3c1a17d343d865f
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57292929"
---
# <a name="implementing-a-c-standard-library-based-collection"></a>Implementowanie kolekcję C++ Standard Library

ATL udostępnia `ICollectionOnSTLImpl` interfejs umożliwia szybkie implementowanie interfejsów kolekcji opartej na standardowej biblioteki języka C++ na obiekty. Aby zrozumieć, jak działa ta klasa, będzie działać, za pośrednictwem stanowi prosty przykład (poniżej) korzysta z tej klasy do zaimplementowania występowaniu klientów automatyzacji kolekcji tylko do odczytu.

Przykładowy kod pochodzi z [przykładowe ATLCollections](../visual-cpp-samples.md).

Aby wykonać tę procedurę, wykonasz następujące czynności:

- [Generowanie nowego prostego obiektu](#vccongenerating_an_object).

- [Edytuj plik IDL](#vcconedit_the_idl) dla wygenerowanego interfejsu.

- [Tworzenie definicji pięć typów](#vcconstorage_and_exposure_typedefs) opisujące, jak elementy kolekcji są przechowywane i jak będzie ona widoczna dla klientów za pośrednictwem interfejsów COM.

- [Utwórz dwie definicje typów związanym z kopiowaniem klasy zasad](#vcconcopy_classes).

- [Tworzenie definicji typów dla wdrożenia modułu wyliczającego i kolekcji](#vcconenumeration_and_collection).

- [Edytuj kod C++ generowane przez kreatora, aby użyć — zbierania typedef](#vcconedit_the_generated_code).

- [Dodaj kod, aby wypełnić kolekcję](#vcconpopulate_the_collection).

##  <a name="vccongenerating_an_object"></a> Generowanie nowego prostego obiektu

Utwórz nowy projekt, zapewniając, że jest wyczyszczone pole atrybutów, w obszarze Ustawienia aplikacji. Okno dialogowe Dodawanie klasy ATL i prostego obiektu Kreatora dodawania do generowania prostego obiektu o nazwie `Words`. Upewnij się, że wywoływana podwójnego interfejsu `IWords` jest generowany. Obiekty wygenerowanej klasy będzie służyć do reprezentowania zbiór słów (czyli ciągów).

##  <a name="vcconedit_the_idl"></a> Edytowanie pliku IDL

Teraz Otwórz plik IDL i Dodaj trzy właściwości, należy włączyć `IWords` w interfejsie kolekcji tylko do odczytu, jak pokazano poniżej:

[!code-cpp[NVC_ATL_COM#24](../atl/codesnippet/cpp/implementing-an-stl-based-collection_1.idl)]

Jest to standardowy formularz interfejs kolekcji tylko do odczytu, zaprojektowana z klientami usługi Automation należy pamiętać. Ponumerowane komentarze w tej definicji interfejsu odpowiadać na komentarze poniżej:

1. Interfejsów kolekcji są zazwyczaj dwa, ponieważ uzyskuje dostęp do klientów automatyzacji `_NewEnum` właściwości, za pośrednictwem `IDispatch::Invoke`. Jednak klienci automatyzacji można uzyskiwać dostęp do pozostałych metod za pośrednictwem vtable, tak podwójna interfejsy są preferowane w porównaniu do dispinterfaces.

1. Jeśli podwójnego interfejsu lub dispinterface nie zostanie rozszerzony w czasie wykonywania (oznacza to, że nie będzie zapewniać dodatkowe metody lub właściwości, za pośrednictwem `IDispatch::Invoke`), należy zastosować **nonextensible** atrybutu do swojej definicji. Ten atrybut umożliwia klientom automatyzacji do przeprowadzenia weryfikacji pełnego kodu w czasie kompilacji. W takim przypadku można rozszerzyć nie interfejsu.

1. Prawidłowy identyfikator DISPID jest ważne, jeśli chcesz, aby klienci automatyzacji, aby można było używać tej właściwości. (Zwróć uwagę, że istnieje tylko jeden znak podkreślenia w DISPID_NEWENUM).

1. Możesz podać dowolną wartość jako identyfikator DISPID z `Item` właściwości. Jednak `Item` zazwyczaj używa się to domyślna właściwość kolekcji DISPID_VALUE. Dzięki temu klienci automatyzacji do odwoływania się do właściwości bez jawnie nadawania mu nazwy.

1. Typ danych używany dla wartości zwracanej z `Item` właściwość jest typ elementu, przechowywane w kolekcji, o ile dotyczy to klientów modelu COM. Interfejs zwraca ciągi, więc zaleca się użycie standardowego typu string COM, BSTR. Można przechowywać dane w innym formacie wewnętrznie jako pojawi się wkrótce.

1. Wartość identyfikator DISPID z `Count` właściwość jest całkowicie dowolnego. Nie ma żadnych standardowych DISPID dla tej właściwości.

##  <a name="vcconstorage_and_exposure_typedefs"></a> Tworzenie definicji typów dla magazynu i zagrożeń

Po zdefiniowaniu interfejs kolekcji należy zdecydować, jak będą przechowywane dane i jak ujawnianie danych za pośrednictwem modułu wyliczającego.

Odpowiedzi na te pytania można podać w postaci liczby definicji typów, które można dodać w górnej części pliku nagłówka dla nowo utworzonej klasie:

[!code-cpp[NVC_ATL_COM#25](../atl/codesnippet/cpp/implementing-an-stl-based-collection_2.h)]

W takim przypadku będą przechowywane dane jako **std::vector** z **std::string**s. **STD::Vector** jest klasą kontenera standardowej biblioteki języka C++, który zachowuje się jak tablica zarządzana. **STD::String** jest klasą ciągów biblioteki standardowej języka C++. W ramach tych zajęć ułatwiają do pracy z kolekcji ciągów.

Obsługa języka Visual Basic jest istotne, aby wskazywał Powodzenie, tego interfejsu, moduł wyliczający zwrócony przez `_NewEnum` właściwość musi obsługiwać `IEnumVARIANT` interfejsu. Jest to interfejs tylko moduł wyliczający zrozumiała dla języka Visual Basic.

##  <a name="vcconcopy_classes"></a> Tworzenie definicji typów dla klasy zasad kopii

Definicje typów, które do tej pory utworzono zawierają wszystkie informacje potrzebne do tworzenia dodatkowych definicje typów dla klas kopiowania, które będą używane przez moduł wyliczający i kolekcji:

[!code-cpp[NVC_ATL_COM#26](../atl/codesnippet/cpp/implementing-an-stl-based-collection_3.h)]

W tym przykładzie można użyć niestandardowego `GenericCopy` klasy zdefiniowanej w VCUE_Copy.h i VCUE_CopyString.h z [ATLCollections](../visual-cpp-samples.md) próbki. Możesz użyć tej klasy w innym kodzie, ale może być konieczne dalsze zdefiniuj specjalizacje `GenericCopy` do obsługi typów danych używanych w własne kolekcje. Aby uzyskać więcej informacji, zobacz [klasy zasad kopii ATL](../atl/atl-copy-policy-classes.md).

##  <a name="vcconenumeration_and_collection"></a> Tworzenie definicji typów dla wyliczenia i kolekcji

Teraz wszystkie parametry szablonu konieczne specialize `CComEnumOnSTL` i `ICollectionOnSTLImpl` dostarczono klas na potrzeby tej sytuacji, w postaci definicje typów. Aby uprościć używanie specjalizacji, należy utworzyć dwa więcej typedefy, jak pokazano poniżej:

[!code-cpp[NVC_ATL_COM#27](../atl/codesnippet/cpp/implementing-an-stl-based-collection_4.h)]

Teraz `CollectionType` jest synonimem dla specjalizacji `ICollectionOnSTLImpl` implementującej `IWords` interfejsu wcześniej zdefiniowaną i dostarcza moduł wyliczający obsługiwanych przez `IEnumVARIANT`.

##  <a name="vcconedit_the_generated_code"></a> Edytowanie kodu generowane przez kreatora

Teraz należy wywieść `CWords` od implementacji interfejsu, reprezentowane przez `CollectionType` typedef zamiast `IWords`, jak pokazano poniżej:

[!code-cpp[NVC_ATL_COM#28](../atl/codesnippet/cpp/implementing-an-stl-based-collection_5.h)]

##  <a name="vcconpopulate_the_collection"></a> Dodawanie kodu do wypełnienia kolekcji

Jest jedynym elementem, który pozostaje do wypełnienia wektora z danymi. W tym prostym przykładzie można dodać kilka słów do kolekcji w konstruktorze klasy:

[!code-cpp[NVC_ATL_COM#29](../atl/codesnippet/cpp/implementing-an-stl-based-collection_6.h)]

Teraz możesz przetestować kod przy użyciu wybranego klienta.

## <a name="see-also"></a>Zobacz także

[Kolekcje i wyliczenia](../atl/atl-collections-and-enumerators.md)<br/>
[ATLCollections Sample](../visual-cpp-samples.md)<br/>
[Klasy zasad kopii ATL](../atl/atl-copy-policy-classes.md)
