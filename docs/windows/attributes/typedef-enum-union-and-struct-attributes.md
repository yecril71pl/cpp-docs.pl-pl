---
title: TypeDef, Enum, Union i struct — atrybuty (C++ COM)
ms.date: 10/02/2018
helpviewer_keywords:
- union attributes
- attributes [C++/CLI], reference topics
ms.assetid: f8a4fe94-dc02-4aed-bc31-3e500d42f4c7
ms.openlocfilehash: 289935c3651535b5f935624dc33246fbe83a4ceb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50631065"
---
# <a name="typedef-enum-union-and-struct-attributes"></a>Atrybuty Typedef, Enum, Union oraz Struct

Następujące atrybuty dotyczą [typedef](../../cpp/aliases-and-typedefs-cpp.md), [struktury](../../cpp/struct-cpp.md), i [wyliczenia](../../cpp/enumerations-cpp.md) słów kluczowych języka C++.

### <a name="typedef"></a>— klasa typedef

|Atrybut|Opis|
|---------------|-----------------|
|[case](case-cpp.md)|Używane z [switch_type —](switch-type.md) atrybutu w **Unii**.|
|[custom](custom-cpp.md)|Umożliwia zdefiniowanie własnego atrybutu.|
|[export](export.md)|Powoduje to struktura danych, należy umieścić w pliku .idl.|
|[first_is](first-is.md)|Określa indeks pierwszego elementu tablicy mają być przekazywane.|
|[helpcontext](helpcontext.md)|Określa identyfikator kontekstu, który pozwala użytkownikowi oglądać informacje o tym elemencie w pliku pomocy.|
|[helpfile](helpfile.md)|Określa nazwę pliku pomocy dla biblioteki typów.|
|[helpstring](helpstring.md)|Określa ciąg znaków, który jest używany do opisania elementu, do której jest stosowany.|
|[library_block](library-block.md)|Umieszcza konstrukcję wewnątrz bloku biblioteki pliku .idl.|
|[ptr](ptr.md)|Określa wskaźnik jako pełna wskaźnika.|
|[public](public-cpp-attributes.md)|Zapewnia, że typedef zostaną umieszczone w biblioteki typów, nawet wtedy, gdy go nie odwołuje się w pliku .idl.|
|[ref](ref-cpp.md)|Określa odwołanie do wskaźnika.|
|[switch_is](switch-is.md)|Określa wyrażenie lub identyfikator działający jako discriminant Unii, który wybiera składowa typu Unii.|
|[switch_type](switch-type.md)|Określa typ zmiennej używanej jako discriminant Unii.|
|[unique](unique-cpp.md)|Określa unikatowy wskaźnik.|
|[wire_marshal](wire-marshal.md)|Określa typ danych, który będzie używany do przekazywania zamiast typu danych specyficznych dla aplikacji.|

### <a name="enum"></a>enum

|Atrybut|Opis|
|---------------|-----------------|
|[custom](custom-cpp.md)|Umożliwia zdefiniowanie własnego atrybutu.|
|[export](export.md)|Powoduje to struktura danych, należy umieścić w pliku .idl.|
|[uuid](uuid-cpp-attributes.md)|Określa unikatowy identyfikator dla klasy lub interfejsu.|
|[v1_enum](v1-enum.md)|Określa, że przekazywane określonego typu wyliczenia jako jednostki 32-bitowych zamiast domyślnego 16-bitowych.|

### <a name="union"></a>unia

|Atrybut|Opis|
|---------------|-----------------|
|[custom](custom-cpp.md)|Umożliwia zdefiniowanie własnego atrybutu.|
|[export](export.md)|Powoduje to struktura danych, należy umieścić w pliku .idl.|
|[first_is](first-is.md)|Określa indeks pierwszego elementu tablicy mają być przekazywane.|
|[last_is](last-is.md)|Określa indeks ostatniego elementu tablicy mają być przekazywane.|
|[length_is](length-is.md)|Określa liczbę elementów tablicy, które mają być przekazywane.|
|[max_is](max-is.md)|Określa maksymalną wartość indeksu prawidłową tablicą.|
|[size_is](size-is.md)|Określa rozmiar pamięci przydzielonej dla wskaźników o rozmiarze, wielkości wskaźniki do wskaźników o rozmiarze i jedno - lub tablic wielowymiarowych.|
|[unique](unique-cpp.md)|Określa unikatowy wskaźnik.|
|[uuid](uuid-cpp-attributes.md)|Określa unikatowy identyfikator dla klasy lub interfejsu.|

### <a name="nonencapsulated-union"></a>Nonencapsulated Unii

|Atrybut|Opis|
|---------------|-----------------|
|[ms_union](ms-union.md)|Steruje wyrównaniem reprezentacji danych sieci nonencapsulated Unii.|
|[no_injected_text](no-injected-text.md)|Zabezpiecza kompilator przed wprowadzanie kodu w wyniku użycia atrybutu.|

### <a name="struct"></a>struktura 

|Atrybut|Opis|
|---------------|-----------------|
|[aggregatable](aggregatable.md)|Wskazuje, że klasa obsługuje agregację.|
|[aggregates](aggregates.md)|Wskazuje, że formant agreguje klasy docelowej.|
|[appobject](appobject.md)|Identyfikuje coclass jako obiekt aplikacji, który jest skojarzony z aplikacją pełną .exe i wskazuje, że funkcje i właściwości z koklas, globalnie dostępną w tej bibliotece typów.|
|[coclass](coclass.md)|Tworzy formant ActiveX.|
|[com_interface_entry](com-interface-entry-cpp.md)|Dodaje wpis interfejsu do mapy COM.|
|[control](control.md)|Określa, że typ zdefiniowany przez użytkownika kontrolki.|
|[custom](custom-cpp.md)|Umożliwia zdefiniowanie własnego atrybutu.|
|[db_column](db-column.md)|Wiąże określonej kolumny zestawu wierszy.|
|[db_command](db-command.md)|Tworzy polecenie OLE DB.|
|[db_param](db-param.md)|Zmienna określonego elementu członkowskiego jest skojarzona z parametrów wejściowych lub wyjściowych, a rozgranicza zmiennej.|
|[db_source](db-source.md)|Tworzy połączenie ze źródłem danych.|
|[db_table](db-table.md)|Zostanie otwarty tabeli OLE DB.|
|[default](default-cpp.md)|Wskazuje, że niestandardowe lub zdefiniowane w obrębie klasy coclass dispinterface reprezentuje domyślny interfejs programowania.|
|[defaultvtable](defaultvtable.md)|Definiuje interfejs jako domyślny interfejs vtable kontrolki.|
|[event_receiver](event-receiver.md)|Tworzy odbiorca zdarzenia.|
|[event_source](event-source.md)|Tworzy źródła zdarzenia.|
|[export](export.md)|Powoduje to struktura danych, należy umieścić w pliku .idl.|
|[first_is](first-is.md)|Określa indeks pierwszego elementu tablicy mają być przekazywane.|
|[hidden](hidden.md)|Wskazuje, czy element istnieje, ale nie powinien być wyświetlany w przeglądarce zorientowanej na użytkownika.|
|[implements_category](implements-category.md)|Określa kategorii składników zaimplementowane dla klasy.|
|[last_is](last-is.md)|Określa indeks ostatniego elementu tablicy mają być przekazywane.|
|[length_is](length-is.md)|Określa liczbę elementów tablicy, które mają być przekazywane.|
|[max_is](max-is.md)|Określa maksymalną wartość indeksu prawidłową tablicą.|
|[requires_category](requires-category.md)|Określa kategorie wymaganego składnika klasy docelowej.|
|[size_is](size-is.md)|Określa rozmiar pamięci przydzielonej dla wskaźników o rozmiarze, wielkości wskaźniki do wskaźników o rozmiarze i jedno - lub tablic wielowymiarowych.|
|[source](source-cpp.md)|W klasie określa interfejsy źródła obiektu COM dla punktów połączenia. W właściwości lub metody oznacza, że elementu członkowskiego zwraca obiekt lub wariant, który jest źródłem zdarzeń.|
|[threading](threading-cpp.md)|Określa model wątkowości dla obiektu COM.|
|[unique](unique-cpp.md)|Określa unikatowy wskaźnik.|
|[uuid](uuid-cpp-attributes.md)|Określa unikatowy identyfikator dla klasy lub interfejsu.|
|[version](version-cpp.md)|Identyfikuje określoną wersję spośród wielu wersji klasy.|
|[vi_progid](vi-progid.md)|Określa formularza niezależny od wersji identyfikatora ProgID.|

## <a name="see-also"></a>Zobacz też

[Atrybuty w zależności od zastosowania](attributes-by-usage.md)