---
title: Atrybuty IDL (C++ COM)
ms.date: 10/02/2018
helpviewer_keywords:
- attributes [C++/CLI], reference topics
- IDL attributes
- .idl files [C++], attributes
- IDL files [C++], attributes
- .idl files [C++]
ms.assetid: 04c596f4-c97b-4952-8053-316678b1d0b6
ms.openlocfilehash: a699e327eec056bbb36747840990bb9c7ccc259b
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59039513"
---
# <a name="idl-attributes"></a>atrybuty IDL

Tradycyjnie utrzymywanie pliku .idl oznacza, że do:

- Należy zapoznać się z struktury i składni pliku .idl, aby można było go zmodyfikować.

- Polegaj na służy Kreator, który będzie można zmodyfikować niektóre aspekty pliku .idl.

Teraz można zmodyfikować pliku .idl z w obrębie pliku kodu źródłowego przy użyciu programu Visual C++ IDL atrybutów. W wielu przypadkach atrybuty Visual C++ IDL mają taką samą nazwę jak atrybutów w MIDL. Gdy nazwy atrybutu Visual C++ IDL oraz atrybut MIDL są takie same, oznacza to, że umieszczenie atrybutu Visual C++ w pliku kodu źródłowego spowoduje w pliku .idl, który zawiera jego atrybut MIDL rozwojowa. Jednak atrybut Visual C++ IDL nie mogą zawierać wszystkie funkcje atrybutu MIDL.

Gdy nie są używane wraz z [atrybuty COM](com-attributes.md), atrybuty IDL pozwalają zdefiniować interfejsów. Podczas kompilowania kodu źródłowego atrybuty są używane do definiowania pliku .idl wygenerowany. W przypadku użycia za pomocą atrybutów COM w projekcie ATL, niektóre IDL atrybuty, takie jak `coclass`, że kod dodany do projektu.

Należy pamiętać, że [idl_quote —](idl-quote.md) pozwalają używać konstrukcji MIDL, które nie są obsługiwane w bieżącej wersji programu Visual C++. Ta i inne atrybuty, takie jak [importlib](importlib.md) i [includelib —](includelib-cpp.md) ułatwiają do korzystania z istniejących plików .idl w bieżącym projekcie Visual C++.

|Atrybut|Opis|
|---------------|-----------------|
|[aggregatable](aggregatable.md)|Wskazuje, że formant może być agregowany przez inny formant.|
|[appobject](appobject.md)|Identyfikuje coclass jako obiekt aplikacji, która jest skojarzona z pełnej aplikacji EXE i wskazuje, że funkcje i właściwości z koklas, globalnie dostępną w tej bibliotece typów.|
|[async_uuid](async-uuid.md)|Określa identyfikator UUID, który określa, że kompilator MIDL, aby zdefiniować synchroniczne i asynchroniczne wersje interfejsu COM.|
|[bindable](bindable.md)|Wskazuje, że właściwość obsługuje powiązanie danych.|
|[call_as](call-as.md)|Włącza funkcję nonremotable mają być mapowane na funkcję zdalną.|
|[case](case-cpp.md)|Używane z [switch_type —](switch-type.md) atrybutu w Unii.|
|[coclass](coclass.md)|Umieszcza klasy definicji do pliku .idl jako klasy coclass.|
|[ — formant](control.md)|Określa, że typ zdefiniowany przez użytkownika kontrolki.|
|[cpp_quote](cpp-quote.md)|Generuje określony ciąg bez znaków cudzysłowu do wygenerowanego pliku nagłówka.|
|[defaultbind](defaultbind.md)|Wskazuje pojedynczą, które można powiązać właściwość, która najlepiej reprezentuje obiekt.|
|[defaultcollelem](defaultcollelem.md)|Używane do optymalizacji kodu języka Visual Basic.|
|[defaultvalue](defaultvalue.md)|Umożliwia określenie wartości domyślnej dla typizowany parametr opcjonalny.|
|[default](default-cpp.md)|Wskazuje, że niestandardowe lub zdefiniowane w obrębie klasy coclass dispinterface reprezentuje domyślny interfejs programowania.|
|[defaultvtable](defaultvtable.md)|Definiuje interfejs jako domyślny interfejs vtable kontrolki.|
|[dispinterface](dispinterface.md)|Przełącza interfejsu w pliku .idl, jako interfejs ekspedycji.|
|[displaybind](displaybind.md)|Wskazuje właściwość, która powinna być wyświetlana użytkownikowi jak możliwa do powiązania.|
|[dual](dual.md)|Przełącza interfejsu w pliku .idl, jako podwójnego interfejsu.|
|[entry](entry.md)|Określa eksportowanych funkcji lub stałą w module, określając punkt wejścia w DLL.|
|[first_is](first-is.md)|Określa indeks pierwszego elementu tablicy mają być przekazywane.|
|[helpcontext](helpcontext.md)|Określa identyfikator kontekstu, który pozwala użytkownikowi oglądać informacje o tym elemencie w pliku pomocy.|
|[helpfile](helpfile.md)|Określa nazwę pliku pomocy dla biblioteki typów.|
|[helpstringcontext](helpstringcontext.md)|Określa identyfikator tematu pomocy w pliku hlp lub chm.|
|[helpstringdll](helpstringdll.md)|Określa nazwę biblioteki DLL, aby wykonać wyszukiwanie ciągu dokumentu (lokalizacja).|
|[helpstring](helpstring.md)|Określa ciąg znaków, który jest używany do opisania elementu, do której jest stosowany.|
|[hidden](hidden.md)|Wskazuje, czy element istnieje, ale nie powinien być wyświetlany w przeglądarce zorientowanej na użytkownika.|
|[idl_module](idl-module.md)|Określa punkt wejścia w bibliotece DLL.|
|[idl_quote](idl-quote.md)|Pozwala na używanie atrybutów lub IDL konstrukcji, które nie są obsługiwane w bieżącej wersji programu Visual C++.|
|[identyfikator](id.md)|Określa identyfikator DISPID dla funkcji członkowskiej (właściwość lub metodę w interfejsie lub dispinterface).|
|[iid_is](iid-is.md)|Określa identyfikator IID interfejsu COM, wskazywana przez wskaźnik interfejsu.|
|[immediatebind](immediatebind.md)|Wskazuje, że baza danych zostanie niezwłocznie powiadomiona o wszystkich zmianach właściwości obiektu powiązanych z danymi.|
|[importlib](importlib.md)|Sprawia, że typy, które już zostały skompilowane do do biblioteki typów, trwa tworzenie innej biblioteki typów.|
|[import](import.md)|Określa innego pliku .idl, .odl — lub nagłówek zawierający definicje, w których ma dotyczyć odwołanie z pliku .idl głównego.|
|[include](include-cpp.md)|Określa jeden lub więcej plików nagłówka do uwzględnienia w pliku .idl wygenerowany.|
|[includelib](includelib-cpp.md)|Powoduje, że pliku .idl lub .h, mają zostać uwzględnione w pliku .idl wygenerowany.|
|[in](in-cpp.md)|Wskazuje, że parametr zostanie przekazany z procedury wywołującej do procedury wywoływanej.|
|[last_is](last-is.md)|Określa indeks ostatniego elementu tablicy mają być przekazywane.|
|[lcid](lcid.md)|Służy do przekazywania identyfikator ustawień regionalnych do funkcji.|
|[length_is](length-is.md)|Określa liczbę elementów tablicy, które mają być przekazywane.|
|[licensed](licensed.md)|Wskazuje, że klasa coclass, do której jest stosowany jest licencjonowana i muszą być tworzone przy użyciu `IClassFactory2`.|
|[local](local-cpp.md)|Umożliwia kompilatorowi MIDL jako generator nagłówka, gdy jest używana w nagłówku interfejsu. W przypadku użycia w poszczególnych funkcji, wyznacza lokalnej procedury, dla którego są generowane nie wycinki.|
|[max_is](max-is.md)|Określa maksymalną wartość indeksu prawidłową tablicą.|
|[moduł](module-cpp.md)|Określa blok biblioteki w pliku .idl.|
|[ms_union](ms-union.md)|Steruje wyrównaniem reprezentacji danych sieci nonencapsulated Unii.|
|[no_injected_text](no-injected-text.md)|Zabezpiecza kompilator przed wprowadzanie kodu w wyniku użycia atrybutu.|
|[nonbrowsable](nonbrowsable.md)|Wskazuje, czy składowej interfejsu nie powinien być wyświetlany w przeglądarce właściwości.|
|[noncreatable](noncreatable.md)|Definiuje obiekt, który nie może być utworzone samodzielnie.|
|[nonextensible](nonextensible.md)|Określa, że `IDispatch` wdrożenia zawiera tylko właściwości i metod wymienionych w opisie interfejsu i nie można rozszerzyć za pomocą dodatkowe elementy członkowskie w czasie wykonywania.|
|[object](object-cpp.md)|Określa niestandardowy interfejs; równoznaczny z atrybutu niestandardowego.|
|[odl](odl.md)|Identyfikuje interfejs jako interfejs język opisu obiektów (ODL).|
|[oleautomation](oleautomation.md)|Wskazuje, że interfejs jest zgodna z usługą Automation.|
|[optional](optional-cpp.md)|Określa opcjonalny parametr dla funkcji członkowskiej.|
|[out](out-cpp.md)|Określa parametry wskaźnika, które zostaną zwrócone z procedury wywoływanej do procedury wywołującej (z serwera do klienta).|
|[pointer_default](pointer-default.md)|Określa domyślny atrybut wskaźnik dla wszystkich wskaźników, z wyjątkiem wskaźniki najwyższego poziomu, które pojawiają się listami parametrów.|
|[pragma](pragma.md)|Generuje określony ciąg bez znaków cudzysłowu do pliku .idl wygenerowany.|
|[progid](progid.md)|Określa identyfikator ProgID dla obiektu COM.|
|[propget](propget.md)|Określa funkcję właściwość metody dostępu (get).|
|[propputref](propputref.md)|Określa funkcję ustawienie właściwości, która używa odwołania, a nie wartość.|
|[propput](propput.md)|Określa funkcję ustawienie właściwości.|
|[ptr](ptr.md)|Określa wskaźnik jako pełna wskaźnika.|
|[public](public-cpp-attributes.md)|Zapewnia, że typedef zostaną umieszczone w biblioteki typów, nawet wtedy, gdy go nie odwołuje się w pliku .idl.|
|[range](range-cpp.md)|Określa zakres dopuszczalnych wartości dla argumentów lub pól, których wartości są ustawione w czasie wykonywania.|
|[readonly](readonly-cpp.md)|Zabrania przypisania do zmiennej.|
|[ref](ref-cpp.md)|Określa odwołanie do wskaźnika.|
|[requestedit](requestedit.md)|Wskazuje, że właściwość obsługuje `OnRequestEdit` powiadomień.|
|[restricted](restricted.md)|Określa, że biblioteka lub członek modułu, interfejs lub dispinterface nie może być wywoływana arbitralnie.|
|[retval](retval.md)|Określa parametr, który otrzymuje wartość zwrotną z elementu członkowskiego.|
|[size_is](size-is.md)|Określa rozmiar pamięci przydzielonej dla wskaźników o rozmiarze, wielkości wskaźniki do wskaźników o rozmiarze i jedno - lub tablic wielowymiarowych.|
|[source](source-cpp.md)|Wskazuje, że jest członkiem klasy, właściwość lub metoda jest źródłem zdarzeń.|
|[string](string-cpp.md)|Oznacza to, że jednowymiarowy **char**, **wchar_t**, `byte`, lub równoważne tablicy lub wskaźnika do takiej tablicy muszą być traktowane jako ciąg.|
|[switch_is](switch-is.md)|Określa wyrażenie lub identyfikator działający jako discriminant Unii, który wybiera składowa typu Unii.|
|[switch_type](switch-type.md)|Określa typ zmiennej używanej jako discriminant Unii.|
|[transmit_as](transmit-as.md)|Instruuje kompilator, aby skojarzyć typem prezentowane kompilowania aplikacji, które klient i serwer, z typem przesyłane.|
|[uidefault](uidefault.md)|Wskazuje, że składowa informacji typu jest domyślny element członkowski do wyświetlania w interfejsie użytkownika.|
|[unique](unique-cpp.md)|Określa unikatowy wskaźnik.|
|[usesgetlasterror](usesgetlasterror.md)|Informuje obiekt wywołujący, że jeśli występuje błąd podczas wywoływania tej funkcji, obiekt wywołujący może wywoływać `GetLastError` można pobrać kod błędu.|
|[uuid](uuid-cpp-attributes.md)|Określa unikatowy identyfikator dla klasy lub interfejsu.|
|[v1_enum](v1-enum.md)|Określa, że przekazywane określonego typu wyliczenia jako jednostki 32-bitowych zamiast domyślnego 16-bitowych.|
|[vararg](vararg.md)|Określa, że funkcja przyjmuje zmienną liczbę argumentów.|
|[vi_progid](vi-progid.md)|Określa formularza niezależny od wersji identyfikatora ProgID.|
|[wire_marshal](wire-marshal.md)|Określa typ danych, który będzie używany do przekazywania zamiast typu danych specyficznych dla aplikacji.|

## <a name="see-also"></a>Zobacz także

[Atrybuty według grup](attributes-by-group.md)
