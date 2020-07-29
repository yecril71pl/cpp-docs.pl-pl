---
title: Alfabetyczny spis atrybutów
ms.custom: index-page
ms.date: 10/02/2018
ms.topic: conceptual
f1_keywords:
- vc.attributes
helpviewer_keywords:
- attributes [C++/CLI]
ms.assetid: fb2216ef-9fbd-44f4-afed-732aa99450e2
ms.openlocfilehash: ad9ecd1e3b3d4620b1f862fd1d5d70ef050da48d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215338"
---
# <a name="attributes-alphabetical-reference"></a>Alfabetyczny spis atrybutów

Następujące atrybuty są dostępne w kompilatorze języka Microsoft C++:

|Atrybut|Opis|
|---------------|-----------------|
|[aggregatable](aggregatable.md)|Wskazuje, że formant może być agregowany przez inną kontrolkę.|
|[Agreguje](aggregates.md)|Wskazuje, że formant agreguje klasę docelową.|
|[appobject](appobject.md)|Identyfikuje klasę coclass jako obiekt aplikacji, która jest skojarzona z aplikacją z pełnym rozszerzeniem EXE i wskazuje, że funkcje i właściwości klasy coclass są dostępne globalnie w tej bibliotece typów.|
|[async_uuid](async-uuid.md)|Określa identyfikator UUID, który kieruje kompilator MIDL do definiowania synchronicznych i asynchronicznych wersji interfejsu COM.|
|[przypisane](attribute.md)|Umożliwia utworzenie atrybutu niestandardowego.|
|[bindable](bindable.md)|Wskazuje, że właściwość obsługuje powiązanie danych.|
|[call_as](call-as.md)|Umożliwia zamapowanie funkcji niezdalnych na funkcję zdalną.|
|[spraw](case-cpp.md)|Używany z atrybutem [switch_type](switch-type.md) w Unii.|
|[coclass](coclass.md)|Tworzy obiekt COM, który może zaimplementować interfejs COM.|
|[com_interface_entry](com-interface-entry-cpp.md)|Dodaje wpis interfejsu do mapy COM.|
|[kontroli](control.md)|Określa, że typem zdefiniowanym przez użytkownika jest kontrolka.|
|[cpp_quote](cpp-quote.md)|Emituje określony ciąg bez znaków cudzysłowu do wygenerowanego pliku nagłówkowego.|
|[celnej](custom-cpp.md)|Umożliwia zdefiniowanie własnych atrybutów.|
|[db_accessor](db-accessor.md)|Tworzy powiązanie kolumn w zestawie wierszy i wiąże je z odpowiednimi mapami dostępu.|
|[db_column](db-column.md)|Wiąże określoną kolumnę z zestawem wierszy.|
|[db_command](db-command.md)|Wykonuje polecenie OLE DB.|
|[db_param](db-param.md)|Kojarzy określoną zmienną członkowską z parametrem wejściowym lub wyjściowym.|
|[db_source](db-source.md)|Tworzy i hermetyzuje połączenie za pomocą dostawcy ze źródłem danych.|
|[db_table](db-table.md)|Otwiera tabelę OLE DB.|
|[default](default-cpp.md)|Wskazuje, że niestandardowe lub dispinterface zdefiniowane w ramach klasy coclass reprezentuje domyślny interfejs programistyczny.|
|[defaultbind](defaultbind.md)|Wskazuje pojedynczą, możliwą do powiązania właściwość, która najlepiej reprezentuje obiekt.|
|[defaultcollelem](defaultcollelem.md)|Używane do optymalizacji kodu Visual Basic.|
|[defaultvalue](defaultvalue.md)|Umożliwia określenie wartości domyślnej dla wpisanego parametru opcjonalnego.|
|[defaultvtable](defaultvtable.md)|Definiuje interfejs jako domyślny interfejs tablicy metod dla kontrolki.|
|[dispinterface](dispinterface.md)|Umieszcza interfejs w pliku. idl jako interfejs wysyłania.|
|[displaybind](displaybind.md)|Wskazuje właściwość, która powinna być wyświetlana użytkownikowi jako możliwy do powiązania.|
|[dual](dual.md)|Umieszcza interfejs w pliku. idl jako podwójny interfejs.|
|[emitidl](emitidl.md)|Określa, czy wszystkie kolejne atrybuty IDL będą przetwarzane i umieszczane w wygenerowanym pliku IDL.|
|[Autotekstu](entry.md)|Określa wyeksportowaną funkcję lub stałą w module, identyfikując punkt wejścia w bibliotece DLL.|
|[event_receiver](event-receiver.md)|Tworzy odbiorcę zdarzeń.|
|[event_source](event-source.md)|Tworzy Źródło zdarzenia.|
|[wywozu](export.md)|Powoduje, że struktura danych zostanie umieszczona w pliku IDL.|
|[first_is](first-is.md)|Określa indeks pierwszego elementu tablicy, który ma zostać przesłany.|
|[helpcontext](helpcontext.md)|Określa identyfikator kontekstu, który umożliwia użytkownikowi wyświetlanie informacji o tym elemencie w pliku pomocy.|
|[helpfile](helpfile.md)|Ustawia nazwę pliku pomocy dla biblioteki typów.|
|[helpstring](helpstring.md)|Określa identyfikator tematu pomocy w pliku HLP lub chm.|
|[helpstringdll](helpstringdll.md)|Określa nazwę biblioteki DLL, która ma być używana do przeszukiwania ciągu dokumentu (lokalizacja).|
|[hidden](hidden.md)|Wskazuje, że element istnieje, ale nie powinien być wyświetlany w przeglądarce zorientowanej na użytkownika.|
|[id](id.md)|Określa identyfikator DISPID dla funkcji składowej (właściwości lub metody w interfejsie lub dispinterface).|
|[idl_module](idl-module.md)|Określa punkt wejścia w bibliotece DLL.|
|[idl_quote](idl-quote.md)|Umożliwia korzystanie z atrybutów lub konstrukcji IDL, które nie są obsługiwane w bieżącej wersji Visual C++.|
|[iid_is](iid-is.md)|Określa identyfikator IID interfejsu COM wskazywanego przez wskaźnik interfejsu.|
|[immediatebind](immediatebind.md)|Wskazuje, że baza danych zostanie natychmiast powiadomiona o wszystkich zmianach właściwości obiektu powiązanego z danymi.|
|[wprowadza](implements-cpp.md)|Określa interfejsy wysyłania, które są wymuszane jako elementy członkowskie klasy coclass IDL.|
|[implements_category](implements-category.md)|Określa kategorie zaimplementowanych składników dla klasy.|
|[zaimportować](import.md)|Określa inny plik IDL, ODL lub nagłówkowy zawierający definicje, które chcesz odwołać z głównego pliku. idl.|
|[importidl](importidl.md)|Wstawia określony plik IDL do wygenerowanego pliku IDL.|
|[importlib](importlib.md)|Sprawia, że typy, które zostały już skompilowane w innej bibliotece typów dostępne dla tworzonej biblioteki typów.|
|[in](in-cpp.md)|Wskazuje, że parametr ma być przekazywać z procedury wywołującej do procedury wywoływanej.|
|[być](include-cpp.md)|Określa co najmniej jeden plik nagłówka do uwzględnienia w wygenerowanym pliku IDL.|
|[includelib —](includelib-cpp.md)|Powoduje, że plik IDL lub h zostanie uwzględniony w wygenerowanym pliku IDL.|
|[last_is](last-is.md)|Określa indeks ostatniego elementu tablicy, który ma zostać przesłany.|
|[lcid](lcid.md)|Umożliwia przekazanie identyfikatora ustawień regionalnych do funkcji.|
|[length_is](length-is.md)|Określa liczbę elementów tablicy do przesłania.|
|[library_block](library-block.md)|Umieszcza konstrukcję w bloku biblioteki pliku IDL.|
|[licensed](licensed.md)|Wskazuje, że Klasa coclass, do której ma zastosowanie, jest licencjonowana i musi być utworzona przy użyciu `IClassFactory2` .|
|[LAN](local-cpp.md)|Umożliwia użycie kompilatora MIDL jako generatora nagłówka, gdy jest używany w nagłówku interfejsu. W przypadku użycia w pojedynczej funkcji określa procedurę lokalną, dla której nie są generowane żadne wycinki.|
|[max_is](max-is.md)|Określa maksymalną wartość prawidłowego indeksu tablicy.|
|[elementu](module-cpp.md)|Definiuje blok biblioteki w pliku IDL.|
|[ms_union](ms-union.md)|Kontroluje wyrównanie danych sieci do wyrównania niehermetyzowanych Unii.|
|[no_injected_text](no-injected-text.md)|Uniemożliwia kompilatorowi wstrzyknięcie kodu w wyniku użycia atrybutów.|
|[nonbrowsable](nonbrowsable.md)|Wskazuje, że element członkowski interfejsu nie powinien być wyświetlany w przeglądarce właściwości.|
|[noncreatable](noncreatable.md)|Definiuje obiekt, którego nie można utworzyć na podstawie samego siebie.|
|[nonextensible](nonextensible.md)|Określa, że `IDispatch` implementacja zawiera tylko właściwości i metody wymienione w opisie interfejsu i nie można go rozszerzyć z dodatkowymi elementami członkowskimi w czasie wykonywania.|
|[object](object-cpp.md)|Identyfikuje niestandardowy interfejs; synonim z atrybutem niestandardowym.|
|[odl](odl.md)|Identyfikuje interfejs jako interfejs ODL (Object Description Language).|
|[oleautomation](oleautomation.md)|Wskazuje, że interfejs jest zgodny z automatyzacją.|
|[obowiązkowe](optional-cpp.md)|Określa opcjonalny parametr funkcji składowej.|
|[określoną](out-cpp.md)|Identyfikuje parametry wskaźnika, które są zwracane z wywoływanej procedury do procedury wywołującej (z serwera do klienta).|
|[pointer_default](pointer-default.md)|Określa domyślny atrybut wskaźnika dla wszystkich wskaźników oprócz wskaźników najwyższego poziomu, które są wyświetlane na listach parametrów.|
|[pragma](pragma.md)|Emituje określony ciąg bez znaków cudzysłowu do wygenerowanego pliku IDL.|
|[progid](progid.md)|Określa identyfikator ProgID dla obiektu COM.|
|[propget](propget.md)|Określa funkcję metody dostępu do właściwości (Get).|
|[propput](propput.md)|Określa funkcję ustawienia właściwości.|
|[propputref](propputref.md)|Określa funkcję ustawienia właściwości, która używa odwołania zamiast wartości.|
|[ptr](ptr.md)|Wyznacza wskaźnik jako pełny wskaźnik.|
|[public](public-cpp-attributes.md)|Zapewnia, że element typedef przejdzie do biblioteki typów, nawet jeśli nie jest przywoływany w pliku. idl.|
|[zakresu](range-cpp.md)|Określa zakres dozwolonych wartości dla argumentów lub pól, których wartości są ustawiane w czasie wykonywania.|
|[rdx](rdx.md)|Tworzy lub modyfikuje klucz rejestru.|
|[readonly](readonly-cpp.md)|Zabrania przypisywania do zmiennej.|
|[ref](ref-cpp.md)|Identyfikuje wskaźnik odwołania.|
|[registration_script](registration-script.md)|Wykonuje określony skrypt rejestracyjny.|
|[requestedit](requestedit.md)|Wskazuje, że właściwość obsługuje `OnRequestEdit` powiadomienie.|
|[requires_category](requires-category.md)|Określa kategorie wymaganych składników dla klasy.|
|[podlega](restricted.md)|Określa, że biblioteka lub element członkowski modułu, interfejsu lub dispinterface nie może zostać wywołany arbitralnie.|
|[retval](retval.md)|Określa parametr, który odbiera wartość zwracaną przez element członkowski.|
|[satype](satype.md)|Określa typ danych `SAFEARRAY` .|
|[size_is](size-is.md)|Określa rozmiar pamięci przydzieloną dla wskaźników rozmiaru, wskaźniki rozmiaru do wskaźników rozmiaru i tablic pojedynczych lub wielowymiarowych.|
|[zewnętrz](source-cpp.md)|Wskazuje, że element członkowski klasy, właściwości lub metody jest źródłem zdarzeń.|
|[parametry](string-cpp.md)|Wskazuje, że tablica Jednowymiarowa **`char`** ,, **`wchar_t`** `byte` lub równoważna lub wskaźnik do takiej tablicy musi być traktowana jako ciąg.|
|[support_error_info](support-error-info.md)|Obsługuje raportowanie błędów dla obiektu docelowego.|
|[switch_is](switch-is.md)|Określa wyrażenie lub identyfikator działający jako discriminant Unii, który wybiera element członkowski Union.|
|[switch_type](switch-type.md)|Określa typ zmiennej używanej jako discriminant Unii.|
|[synchronize](synchronize.md)|Synchronizuje dostęp do metody.|
|[Threading](threading-cpp.md)|Określa model wątkowości dla obiektu COM.|
|[transmit_as](transmit-as.md)|Instruuje kompilator, aby skojarzyć przedstawiony typ, który obsługuje aplikacje klienta i serwera, z przesyłanym typem.|
|[uidefault](uidefault.md)|Wskazuje, że element członkowski informacji o typie jest domyślnym elementem członkowskim do wyświetlania w interfejsie użytkownika.|
|[unique](unique-cpp.md)|Określa unikatowy wskaźnik.|
|[usesgetlasterror](usesgetlasterror.md)|Instruuje obiekt wywołujący, że jeśli wystąpi błąd podczas wywoływania tej funkcji, wywołujący może następnie wywołać, `GetLastError` Aby pobrać kod błędu.|
|[uuid](uuid-cpp-attributes.md)|Określa unikatowy identyfikator klasy lub interfejsu.|
|[v1_enum](v1-enum.md)|Określa, że określony typ wyliczeniowy ma być przekazywany jako jednostka 32-bitowa, a nie wartość domyślna 16-bitowa.|
|[vararg](vararg.md)|Określa, że funkcja przyjmuje zmienną liczbę argumentów.|
|[Wersja](version-cpp.md)|Identyfikuje określoną wersję między wieloma wersjami interfejsu lub klasy.|
|[vi_progid](vi-progid.md)|Określa niezależną od wersji identyfikator ProgID.|
|[wire_marshal](wire-marshal.md)|Określa typ danych, który będzie używany do przesyłania zamiast typu danych specyficznego dla aplikacji.|

## <a name="see-also"></a>Zobacz także

[Atrybuty języka C++ dla modelu COM i platformy .NET](cpp-attributes-com-net.md)<br/>
[Atrybuty według grupy](attributes-by-group.md)<br/>
[Atrybuty według użycia](attributes-by-usage.md)
