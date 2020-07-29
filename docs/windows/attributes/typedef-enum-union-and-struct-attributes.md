---
title: Atrybuty typedef, enum, Union i struct (C++ COM)
ms.date: 10/02/2018
helpviewer_keywords:
- union attributes
- attributes [C++/CLI], reference topics
ms.assetid: f8a4fe94-dc02-4aed-bc31-3e500d42f4c7
ms.openlocfilehash: 5e9eccd5e4464e92757d6dd78dd0f5187372ea3e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222111"
---
# <a name="typedef-enum-union-and-struct-attributes"></a>Atrybuty Typedef, Enum, Union oraz Struct

Następujące atrybuty mają zastosowanie do słów kluczowych [typedef](../../cpp/aliases-and-typedefs-cpp.md), [struct](../../cpp/struct-cpp.md)i [enum](../../cpp/enumerations-cpp.md) języka C++.

### <a name="typedef"></a> — klasa typedef

|Atrybut|Opis|
|---------------|-----------------|
|[spraw](case-cpp.md)|Używany z atrybutem [switch_type](switch-type.md) w **`union`** .|
|[celnej](custom-cpp.md)|Umożliwia zdefiniowanie własnego atrybutu.|
|[wywozu](export.md)|Powoduje, że struktura danych zostanie umieszczona w pliku IDL.|
|[first_is](first-is.md)|Określa indeks pierwszego elementu tablicy, który ma zostać przesłany.|
|[helpcontext](helpcontext.md)|Określa identyfikator kontekstu, który umożliwia użytkownikowi wyświetlanie informacji o tym elemencie w pliku pomocy.|
|[helpfile](helpfile.md)|Ustawia nazwę pliku pomocy dla biblioteki typów.|
|[helpstring](helpstring.md)|Określa ciąg znaków, który jest używany do opisania elementu, do którego ma zastosowanie.|
|[library_block](library-block.md)|Umieszcza konstrukcję w bloku biblioteki pliku IDL.|
|[ptr](ptr.md)|Wyznacza wskaźnik jako pełny wskaźnik.|
|[public](public-cpp-attributes.md)|Zapewnia, że element typedef przejdzie do biblioteki typów, nawet jeśli nie jest przywoływany w pliku. idl.|
|[ref](ref-cpp.md)|Identyfikuje wskaźnik odwołania.|
|[switch_is](switch-is.md)|Określa wyrażenie lub identyfikator działający jako discriminant Unii, który wybiera element członkowski Union.|
|[switch_type](switch-type.md)|Określa typ zmiennej używanej jako discriminant Unii.|
|[unique](unique-cpp.md)|Określa unikatowy wskaźnik.|
|[wire_marshal](wire-marshal.md)|Określa typ danych, który będzie używany do przesyłania zamiast typu danych specyficznego dla aplikacji.|

### <a name="enum"></a>enum

|Atrybut|Opis|
|---------------|-----------------|
|[celnej](custom-cpp.md)|Umożliwia zdefiniowanie własnego atrybutu.|
|[wywozu](export.md)|Powoduje, że struktura danych zostanie umieszczona w pliku IDL.|
|[uuid](uuid-cpp-attributes.md)|Określa unikatowy identyfikator klasy lub interfejsu.|
|[v1_enum](v1-enum.md)|Określa, że określony typ wyliczeniowy ma być przekazywany jako jednostka 32-bitowa, a nie wartość domyślna 16-bitowa.|

### <a name="union"></a>unia

|Atrybut|Opis|
|---------------|-----------------|
|[celnej](custom-cpp.md)|Umożliwia zdefiniowanie własnego atrybutu.|
|[wywozu](export.md)|Powoduje, że struktura danych zostanie umieszczona w pliku IDL.|
|[first_is](first-is.md)|Określa indeks pierwszego elementu tablicy, który ma zostać przesłany.|
|[last_is](last-is.md)|Określa indeks ostatniego elementu tablicy, który ma zostać przesłany.|
|[length_is](length-is.md)|Określa liczbę elementów tablicy do przesłania.|
|[max_is](max-is.md)|Określa maksymalną wartość prawidłowego indeksu tablicy.|
|[size_is](size-is.md)|Określa rozmiar pamięci przydzieloną dla wskaźników rozmiaru, wskaźniki rozmiaru do wskaźników rozmiaru i tablic pojedynczych lub wielowymiarowych.|
|[unique](unique-cpp.md)|Określa unikatowy wskaźnik.|
|[uuid](uuid-cpp-attributes.md)|Określa unikatowy identyfikator klasy lub interfejsu.|

### <a name="nonencapsulated-union"></a>Niehermetyzowany związek

|Atrybut|Opis|
|---------------|-----------------|
|[ms_union](ms-union.md)|Kontroluje wyrównanie danych sieci do wyrównania niehermetyzowanych Unii.|
|[no_injected_text](no-injected-text.md)|Uniemożliwia kompilatorowi wstrzyknięcie kodu w wyniku użycia atrybutów.|

### <a name="struct"></a>struktura

|Atrybut|Opis|
|---------------|-----------------|
|[aggregatable](aggregatable.md)|Wskazuje, że Klasa obsługuje agregację.|
|[Agreguje](aggregates.md)|Wskazuje, że formant agreguje klasę docelową.|
|[appobject](appobject.md)|Identyfikuje klasy coclass jako obiekt aplikacji, który jest skojarzony z pełną aplikacją. exe i wskazuje, że funkcje i właściwości klasy coclass są dostępne globalnie w tej bibliotece typów.|
|[coclass](coclass.md)|Tworzy kontrolkę ActiveX.|
|[com_interface_entry](com-interface-entry-cpp.md)|Dodaje wpis interfejsu do mapy COM.|
|[kontroli](control.md)|Określa, że typem zdefiniowanym przez użytkownika jest kontrolka.|
|[celnej](custom-cpp.md)|Umożliwia zdefiniowanie własnego atrybutu.|
|[db_column](db-column.md)|Wiąże określoną kolumnę z zestawem wierszy.|
|[db_command](db-command.md)|Tworzy polecenie OLE DB.|
|[db_param](db-param.md)|Kojarzy określoną zmienną członkowską z parametrem wejściowym lub wyjściowym i ogranicza zmienną.|
|[db_source](db-source.md)|Tworzy połączenie ze źródłem danych.|
|[db_table](db-table.md)|Otwiera tabelę OLE DB.|
|[default](default-cpp.md)|Wskazuje, że niestandardowe lub dispinterface zdefiniowane w ramach klasy coclass reprezentuje domyślny interfejs programistyczny.|
|[defaultvtable](defaultvtable.md)|Definiuje interfejs jako domyślny interfejs tablicy metod dla kontrolki.|
|[event_receiver](event-receiver.md)|Tworzy odbiorcę zdarzeń.|
|[event_source](event-source.md)|Tworzy Źródło zdarzenia.|
|[wywozu](export.md)|Powoduje, że struktura danych zostanie umieszczona w pliku IDL.|
|[first_is](first-is.md)|Określa indeks pierwszego elementu tablicy, który ma zostać przesłany.|
|[hidden](hidden.md)|Wskazuje, że element istnieje, ale nie powinien być wyświetlany w przeglądarce zorientowanej na użytkownika.|
|[implements_category](implements-category.md)|Określa kategorie zaimplementowanych składników dla klasy.|
|[last_is](last-is.md)|Określa indeks ostatniego elementu tablicy, który ma zostać przesłany.|
|[length_is](length-is.md)|Określa liczbę elementów tablicy do przesłania.|
|[max_is](max-is.md)|Określa maksymalną wartość prawidłowego indeksu tablicy.|
|[requires_category](requires-category.md)|Określa kategorie wymaganych składników klasy docelowej.|
|[size_is](size-is.md)|Określa rozmiar pamięci przydzieloną dla wskaźników rozmiaru, wskaźniki rozmiaru do wskaźników rozmiaru i tablic pojedynczych lub wielowymiarowych.|
|[zewnętrz](source-cpp.md)|Na klasie Określa interfejsy źródłowe obiektu COM dla punktów połączenia. Na właściwości lub metodzie wskazuje, że element członkowski zwraca obiekt lub wariant, który jest źródłem zdarzeń.|
|[Threading](threading-cpp.md)|Określa model wątkowości dla obiektu COM.|
|[unique](unique-cpp.md)|Określa unikatowy wskaźnik.|
|[uuid](uuid-cpp-attributes.md)|Określa unikatowy identyfikator klasy lub interfejsu.|
|[Wersja](version-cpp.md)|Identyfikuje konkretną wersję w wielu wersjach klasy.|
|[vi_progid](vi-progid.md)|Określa niezależną od wersji identyfikator ProgID.|

## <a name="see-also"></a>Zobacz także

[Atrybuty według użycia](attributes-by-usage.md)
