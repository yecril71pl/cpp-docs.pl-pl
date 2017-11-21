---
title: "Implementowanie kolekcję C++ Standard biblioteki | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: ICollectionOnSTLImpl interface
ms.assetid: 6d49f819-1957-4813-b074-3f12c494d8ca
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 21ca1d07a39950c5d5de83ed6e3a09c12c775d4d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="implementing-a-c-standard-library-based-collection"></a>Implementowanie kolekcję C++ Standard biblioteki
Udostępnia ATL `ICollectionOnSTLImpl` interfejs umożliwia szybkie rozpoczęcie interfejsy kolekcji na podstawie standardowa biblioteka C++ na obiektów. Aby zrozumieć, jak działa ta klasa, będzie działać przez prosty przykład (poniżej), który korzysta z tej klasy do zaimplementowania kolekcji tylko do odczytu, przeznaczony dla klientów automatyzacji.  
  
 Przykładowy kod jest z [próbki ATLCollections](../visual-cpp-samples.md).  
  
 Aby wykonać tę procedurę, użytkownik będzie:  
  
-   [Generowanie nowego obiektu proste](#vccongenerating_an_object).  
  
-   [Przeprowadź edycję pliku IDL](#vcconedit_the_idl) dla wygenerowanego interfejsu.  
  
-   [Tworzenie definicji typów pięć](#vcconstorage_and_exposure_typedefs) opisujący sposób elementy kolekcji są przechowywane i jak mają być widoczne dla klientów za pośrednictwem interfejsów COM.  
  
-   [Utwórz dwie definicje typów kopii zasad klasy](#vcconcopy_classes).  
  
-   [Tworzenie definicji typów w implementacji modułu wyliczającego i kolekcji](#vcconenumeration_and_collection).  
  
-   [Edytuj kod C++ generowane przez kreatora, aby użyć typedef kolekcji](#vcconedit_the_generated_code).  
  
-   [Dodaj kod, aby wypełnić kolekcji](#vcconpopulate_the_collection).  
  
##  <a name="vccongenerating_an_object"></a>Generowanie nowego obiektu proste  
 Utwórz nowy projekt, zapewniając, że jest wyczyszczone pole atrybutów, w obszarze Ustawienia aplikacji. Okno dialogowe Dodawanie klasy ATL i prosty obiekt Kreatora dodawania aby wygenerować prosty obiekt o nazwie `Words`. Upewnij się, że dwa interfejs o nazwie `IWords` jest generowany. Obiekty wygenerowanej klasy będzie używany do reprezentowania kolekcji wyrazów (to znaczy ciągi).  
  
##  <a name="vcconedit_the_idl"></a>Edytowanie pliku IDL  
 Teraz, otwórz plik IDL i Dodaj trzy właściwości, należy włączyć `IWords` w interfejsie kolekcji tylko do odczytu, jak pokazano poniżej:  
  
 [!code-cpp[NVC_ATL_COM#24](../atl/codesnippet/cpp/implementing-an-stl-based-collection_1.idl)]  
  
 Jest to standardowy formularz interfejs kolekcji tylko do odczytu z klientów automatyzacji pamiętać. Numerowane komentarzy w tej definicji interfejsu odpowiadają uwagi poniżej:  
  
1.  Interfejsy kolekcji są zazwyczaj dwa, ponieważ uzyskuje dostęp do klientów automatyzacji `_NewEnum` właściwości za pośrednictwem **IDispatch::Invoke**. Jednak automatyzacji mogą uzyskać dostęp klienci pozostałe metody za pomocą vtable, dlatego podwójne interfejsy są preferowane dispinterfaces.  
  
2.  Jeśli interfejs podwójny lub dispinterface nie zostanie rozszerzony w czasie wykonywania (oznacza to, że nie będzie zapewniać dodatkowe metody lub właściwości za pośrednictwem **IDispatch::Invoke**), należy zastosować **nonextensible —** atrybutu Definicja. Ten atrybut umożliwia klientów automatyzacji do przeprowadzenia weryfikacji pełnego kodu w czasie kompilacji. W takim przypadku można rozszerzyć nie interfejsu.  
  
3.  Poprawny identyfikator DISPID jest ważne, jeśli chcesz, aby klienci automatyzacji, aby można było używać tej właściwości. (Należy pamiętać, że istnieje tylko jeden znak podkreślenia w **DISPID_NEWENUM**.)  
  
4.  Możesz podać wartości jako DISPID o **elementu** właściwości. Jednak **elementu** zwykle wykorzystuje **DISPID_VALUE** dokonanie domyślnej właściwości kolekcji. Dzięki temu klienci automatyzacji do odwoływania się do właściwości bez jawnie nadawanie nazw.  
  
5.  Typ danych używany dla wartości zwracanej z **elementu** właściwość jest typu przechowywana w kolekcji, o ile dotyczy to klientów modelu COM. Interfejs zwraca ciągów, więc należy stosować standardowy typ ciągu COM `BSTR`. Można przechowywać dane w innym formacie wewnętrznie jako pojawi się wkrótce.  
  
6.  Wartość używaną dla DISPID o **liczba** jest całkowicie dowolne właściwości. Nie ma żadnych standardowych DISPID dla tej właściwości.  
  
##  <a name="vcconstorage_and_exposure_typedefs"></a>Tworzenie definicji typów dla magazynu i zagrożeń  
 Po zdefiniowaniu interfejs kolekcji należy zdecydować, sposób przechowywania danych i jak mają być widoczne dane za pomocą modułu wyliczającego.  
  
 Odpowiedzi na te pytania można podać w postaci liczby definicje typów, które można dodać u góry pliku nagłówka dla nowo utworzonej klasy:  
  
 [!code-cpp[NVC_ATL_COM#25](../atl/codesnippet/cpp/implementing-an-stl-based-collection_2.h)]  
  
 W takim przypadku będą przechowywane dane jako **std::vector** z **std::string**s. **STD::Vector** jest klasą kontenera standardowa biblioteka C++, który zachowuje się jak tablicy. **STD::String** jest klasa ciąg Biblioteka Standard C++. Te klasy ułatwiają pracę z kolekcji ciągów.  
  
 Ponieważ niezbędne do pomyślnego zakończenia tego interfejsu jest obsługa języka Visual Basic, moduł wyliczający zwrócony przez `_NewEnum` właściwości musi obsługiwać **interfejsu IEnumVARIANT** interfejsu. Jest to interfejs tylko moduł wyliczający zrozumiałe dla języka Visual Basic.  
  
##  <a name="vcconcopy_classes"></a>Tworzenie definicji typów dla klas zasad kopii  
 Definicje typów, utworzony wykonanej do tej pory zawierają wszystkie informacje, które należy utworzyć dodatkowe elementy TypeDef dla klasy kopiowania, które będą używane przez moduł wyliczający i kolekcji:  
  
 [!code-cpp[NVC_ATL_COM#26](../atl/codesnippet/cpp/implementing-an-stl-based-collection_3.h)]  
  
 W tym przykładzie, można użyć niestandardowego `GenericCopy` klas zdefiniowanych w VCUE_Copy.h i VCUE_CopyString.h z [ATLCollections](../visual-cpp-samples.md) próbki. Ta klasa służy w innym kodzie, ale może być konieczne zdefiniowanie dalszych specjalizacjach `GenericCopy` do obsługi typów danych używanych w własne kolekcje. Aby uzyskać więcej informacji, zobacz [klasy zasad kopii ATL](../atl/atl-copy-policy-classes.md).  
  
##  <a name="vcconenumeration_and_collection"></a>Tworzenie definicji typów dla wyliczenia i kolekcji  
 Teraz wszystkie parametry szablonu konieczne specialize `CComEnumOnSTL` i `ICollectionOnSTLImpl` dostarczono klas w takiej sytuacji w formularzu definicje typów. Aby ułatwić korzystanie z specjalizacji, Utwórz dwie definicje więcej typów w sposób przedstawiony poniżej:  
  
 [!code-cpp[NVC_ATL_COM#27](../atl/codesnippet/cpp/implementing-an-stl-based-collection_4.h)]  
  
 Teraz `CollectionType` jest synonimem specjalizacji `ICollectionOnSTLImpl` implementującej `IWords` interfejsu zdefiniowanego wcześniej i udostępnia obsługiwane przez moduł wyliczający **interfejsu IEnumVARIANT**.  
  
##  <a name="vcconedit_the_generated_code"></a>Edytowanie kodu generowane przez kreatora  
 Teraz musi pochodzić `CWords` z implementacji interfejsu reprezentowany przez `CollectionType` typedef zamiast `IWords`, jak pokazano poniżej:  
  
 [!code-cpp[NVC_ATL_COM#28](../atl/codesnippet/cpp/implementing-an-stl-based-collection_5.h)]  
  
##  <a name="vcconpopulate_the_collection"></a>Dodawanie kodu do wypełniania kolekcji  
 Jedyną operacją, której jest wypełnić wektora z danymi. W tym prostym przykładzie kilka słów można dodać do kolekcji w konstruktorze klasy:  
  
 [!code-cpp[NVC_ATL_COM#29](../atl/codesnippet/cpp/implementing-an-stl-based-collection_6.h)]  
  
 Teraz możesz przetestować kod z dowolnego klienta.  
  
## <a name="see-also"></a>Zobacz też  
 [Kolekcje i wyliczenia](../atl/atl-collections-and-enumerators.md)   
 [Przykładowe ATLCollections](../visual-cpp-samples.md)   
 [Klasy zasad kopii ATL](../atl/atl-copy-policy-classes.md)

