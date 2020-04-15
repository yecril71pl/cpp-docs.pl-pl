---
title: Implementowanie kolekcji opartej na standardowej bibliotece języka C++
ms.date: 11/04/2016
helpviewer_keywords:
- ICollectionOnSTLImpl interface
ms.assetid: 6d49f819-1957-4813-b074-3f12c494d8ca
ms.openlocfilehash: e80ce5e7bbc6b9c6be1615dad1ea43c18e03eb55
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319444"
---
# <a name="implementing-a-c-standard-library-based-collection"></a>Implementowanie kolekcji opartej na standardowej bibliotece języka C++

ATL udostępnia `ICollectionOnSTLImpl` interfejs, aby umożliwić szybkie zaimplementowanie interfejsów kolekcji opartych na bibliotece standardowej języka C++ na obiektach. Aby zrozumieć, jak działa ta klasa, będzie działać za pomocą prostego przykładu (poniżej), który używa tej klasy do zaimplementowania kolekcji tylko do odczytu przeznaczone dla klientów automatyzacji.

Przykładowy kod pochodzi z [próbki ATLCollections](../overview/visual-cpp-samples.md).

Aby wykonać tę procedurę, należy:

- [Wygeneruj nowy obiekt prosty](#vccongenerating_an_object).

- [Edytuj plik IDL](#vcconedit_the_idl) dla wygenerowanego interfejsu.

- [Utwórz pięć typedefs opisujące,](#vcconstorage_and_exposure_typedefs) jak elementy kolekcji są przechowywane i jak będą one udostępniane klientom za pośrednictwem interfejsów COM.

- [Utwórz dwie definicje dla klas zasad kopiowania](#vcconcopy_classes).

- [Tworzenie typedefs dla wyliczacza i implementacji kolekcji](#vcconenumeration_and_collection).

- [Edytuj wygenerowany przez kreatora kod C++, aby użyć typedef kolekcji](#vcconedit_the_generated_code).

- [Dodaj kod, aby wypełnić kolekcję](#vcconpopulate_the_collection).

## <a name="generating-a-new-simple-object"></a><a name="vccongenerating_an_object"></a>Generowanie nowego obiektu prostego

Utwórz nowy projekt, upewniając się, że pole Atrybuty w obszarze Ustawienia aplikacji jest wyczyszczone. Użyj okna dialogowego Atl Add Class i Dodaj Kreatora obiektów prostych, aby wygenerować prosty obiekt o nazwie `Words`. Upewnij się, że `IWords` generowany jest podwójny interfejs. Obiekty wygenerowanej klasy będą używane do reprezentowania kolekcji słów (czyli ciągów).

## <a name="editing-the-idl-file"></a><a name="vcconedit_the_idl"></a>Edytowanie pliku IDL

Teraz otwórz plik IDL i dodaj trzy właściwości `IWords` niezbędne do przekształcenia się w interfejs kolekcji tylko do odczytu, jak pokazano poniżej:

[!code-cpp[NVC_ATL_COM#24](../atl/codesnippet/cpp/implementing-an-stl-based-collection_1.idl)]

Jest to standardowy formularz dla interfejsu kolekcji tylko do odczytu zaprojektowany z myślą o klientach automatyzacji. Ponumerowane komentarze w tej definicji interfejsu odpowiadają poniższym uwagom:

1. Interfejsy kolekcji są zwykle podwójne, `_NewEnum` ponieważ `IDispatch::Invoke`klienci automatyzacji uzyskuje dostęp do właściwości za pośrednictwem . Jednak klienci automatyzacji mogą uzyskać dostęp do pozostałych metod za pośrednictwem vtable, więc dwa interfejsy są lepsze niż dispinterfaces.

1. Jeśli podwójny interfejs lub dispinterface nie zostanie przedłużony w czasie wykonywania (oznacza to, `IDispatch::Invoke`że nie zapewni dodatkowych metod lub właściwości za pośrednictwem), należy zastosować **nonextensible** atrybut do definicji. Ten atrybut umożliwia klientom automatyzacji wykonywanie pełnej weryfikacji kodu w czasie kompilacji. W takim przypadku interfejs nie powinien być rozszerzony.

1. Poprawny identyfikator DISPID jest ważne, jeśli chcesz, aby klienci automatyzacji mogli korzystać z tej właściwości. (Należy zauważyć, że w DISPID_NEWENUM jest tylko jeden podkreślenie).

1. Można podać dowolną wartość jako DISPID `Item` właściwości. Jednak `Item` zazwyczaj używa DISPID_VALUE, aby uczynić go domyślną właściwością kolekcji. Dzięki temu klienci automatyzacji odwoływać się do właściwości bez nazewnictwa go jawnie.

1. Typ danych używany dla wartości `Item` zwracanej właściwości jest typem elementu przechowywanego w kolekcji, jeśli chodzi o klientów COM. Interfejs zwraca ciągi, więc należy użyć standardowego typu ciągu COM, BSTR. Dane można przechowywać wewnętrznie w innym formacie, jak zobaczysz wkrótce.

1. Wartość używana dla DISPID `Count` właściwości jest całkowicie dowolny. Nie ma standardowego dispid dla tej właściwości.

## <a name="creating-typedefs-for-storage-and-exposure"></a><a name="vcconstorage_and_exposure_typedefs"></a>Tworzenie typedefs dla pamięci masowej i ekspozycji

Po zdefiniowaniu interfejsu kolekcji należy zdecydować, jak dane będą przechowywane i jak dane będą udostępniane za pośrednictwem modułu wyliczacza.

Odpowiedzi na te pytania można udzielić w postaci wielu typedefs, które można dodać w górnej części pliku nagłówka dla nowo utworzonej klasy:

[!code-cpp[NVC_ATL_COM#25](../atl/codesnippet/cpp/implementing-an-stl-based-collection_2.h)]

W takim przypadku dane będą przechowywane jako **std::vector** **std::string**s. **std::vector** jest klasą kontenera biblioteki standardowej języka C++, która zachowuje się jak tablica zarządzana. **std::string** jest klasą ciągu biblioteki standardowej języka C++. Te klasy ułatwiają pracę z kolekcją ciągów.

Ponieważ obsługa języka Visual Basic jest niezbędna do powodzenia tego `_NewEnum` interfejsu, moduł `IEnumVARIANT` wyliczający zwrócony przez właściwość musi obsługiwać interfejs. Jest to jedyny interfejs modułu wyliczacza zrozumiały dla języka Visual Basic.

## <a name="creating-typedefs-for-copy-policy-classes"></a><a name="vcconcopy_classes"></a>Tworzenie typedefs dla klas zasad kopiowania

Typedefs utworzone do tej pory zapewniają wszystkie informacje potrzebne do tworzenia dalszych typedefs dla klas kopiowania, które będą używane przez wyliczanie i kolekcji:

[!code-cpp[NVC_ATL_COM#26](../atl/codesnippet/cpp/implementing-an-stl-based-collection_3.h)]

W tym przykładzie można `GenericCopy` użyć klasy niestandardowej zdefiniowanej w VCUE_Copy.h i VCUE_CopyString.h z próbki [ATLCollections.](../overview/visual-cpp-samples.md) Tej klasy można użyć w innym kodzie, ale może `GenericCopy` być konieczne zdefiniowanie dalszych specjalizacji do obsługi typów danych używanych w własnych kolekcjach. Aby uzyskać więcej informacji, zobacz [ATL Copy Policy Classes](../atl/atl-copy-policy-classes.md).

## <a name="creating-typedefs-for-enumeration-and-collection"></a><a name="vcconenumeration_and_collection"></a>Tworzenie typedefs dla wyliczenia i kolekcji

Teraz wszystkie parametry szablonu `CComEnumOnSTL` niezbędne `ICollectionOnSTLImpl` do specjalizacji i klasy dla tej sytuacji zostały dostarczone w postaci typedefs. Aby uprościć stosowanie specjalizacji, należy utworzyć jeszcze dwa typedefs, jak pokazano poniżej:

[!code-cpp[NVC_ATL_COM#27](../atl/codesnippet/cpp/implementing-an-stl-based-collection_4.h)]

Teraz `CollectionType` jest synonimem `ICollectionOnSTLImpl` specjalizacji, która `IWords` implementuje interfejs zdefiniowany wcześniej i `IEnumVARIANT`zapewnia moduł wyliczacza, który obsługuje .

## <a name="editing-the-wizard-generated-code"></a><a name="vcconedit_the_generated_code"></a>Edytowanie kodu wygenerowanego przez kreatora

Teraz należy wyprowadzić `CWords` z implementacji interfejsu `CollectionType` reprezentowane `IWords`przez typedef, a nie , jak pokazano poniżej:

[!code-cpp[NVC_ATL_COM#28](../atl/codesnippet/cpp/implementing-an-stl-based-collection_5.h)]

## <a name="adding-code-to-populate-the-collection"></a><a name="vcconpopulate_the_collection"></a>Dodawanie kodu do wypełniania kolekcji

Jedyną rzeczą, która pozostaje jest wypełnić wektora z danymi. W tym prostym przykładzie można dodać kilka słów do kolekcji w konstruktorze dla klasy:

[!code-cpp[NVC_ATL_COM#29](../atl/codesnippet/cpp/implementing-an-stl-based-collection_6.h)]

Teraz możesz przetestować kod z wybranym klientem.

## <a name="see-also"></a>Zobacz też

[Kolekcje i wyliczacze](../atl/atl-collections-and-enumerators.md)<br/>
[AtlCollections Przykład](../overview/visual-cpp-samples.md)<br/>
[Klasy zasad kopiowania ATL](../atl/atl-copy-policy-classes.md)
