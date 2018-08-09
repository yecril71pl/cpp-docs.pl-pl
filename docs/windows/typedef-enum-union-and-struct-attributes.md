---
title: Element TypeDef, Enum, Union i struct — atrybuty | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- union attributes
- attributes [C++], reference topics
- struct attributes
- typedef attributes
- enum attributes
ms.assetid: f8a4fe94-dc02-4aed-bc31-3e500d42f4c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2e4e8ad94e96c6bfc45102f1c970476c484d756f
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39649126"
---
# <a name="typedef-enum-union-and-struct-attributes"></a>Atrybuty Typedef, Enum, Union oraz Struct
Następujące atrybuty dotyczą [typedef](http://msdn.microsoft.com/cc96cf26-ba93-4179-951e-695d1f5fdcf1), [struktury](../cpp/struct-cpp.md), i [wyliczenia](../cpp/enumerations-cpp.md) słów kluczowych języka C++.  
  
### <a name="typedef"></a>— klasa typedef  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|[przypadek](../windows/case-cpp.md)|Używane z [switch_type —](../windows/switch-type.md) atrybutu w **Unii**.|  
|[custom](../windows/custom-cpp.md)|Umożliwia zdefiniowanie własnego atrybutu.|  
|[export](../windows/export.md)|Powoduje to struktura danych, należy umieścić w pliku .idl.|  
|[first_is](../windows/first-is.md)|Określa indeks pierwszego elementu tablicy mają być przekazywane.|  
|[helpcontext](../windows/helpcontext.md)|Określa identyfikator kontekstu, który pozwala użytkownikowi oglądać informacje o tym elemencie w pliku pomocy.|  
|[helpfile](../windows/helpfile.md)|Określa nazwę pliku pomocy dla biblioteki typów.|  
|[helpstring](../windows/helpstring.md)|Określa ciąg znaków, który jest używany do opisania elementu, do której jest stosowany.|  
|[library_block](../windows/library-block.md)|Umieszcza konstrukcję wewnątrz bloku biblioteki pliku .idl.|  
|[ptr](../windows/ptr.md)|Określa wskaźnik jako pełna wskaźnika.|  
|[public](../windows/public-cpp-attributes.md)|Zapewnia, że typedef zostaną umieszczone w biblioteki typów, nawet wtedy, gdy go nie odwołuje się w pliku .idl.|  
|[ref](../windows/ref-cpp.md)|Określa odwołanie do wskaźnika.|  
|[switch_is](../windows/switch-is.md)|Określa wyrażenie lub identyfikator działający jako discriminant Unii, który wybiera składowa typu Unii.|  
|[switch_type](../windows/switch-type.md)|Określa typ zmiennej używanej jako discriminant Unii.|  
|[unique](../windows/unique-cpp.md)|Określa unikatowy wskaźnik.|  
|[wire_marshal](../windows/wire-marshal.md)|Określa typ danych, który będzie używany do przekazywania zamiast typu danych specyficznych dla aplikacji.|  
  
### <a name="enum"></a>enum  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|[custom](../windows/custom-cpp.md)|Umożliwia zdefiniowanie własnego atrybutu.|  
|[export](../windows/export.md)|Powoduje to struktura danych, należy umieścić w pliku .idl.|  
|[uuid](../windows/uuid-cpp-attributes.md)|Określa unikatowy identyfikator dla klasy lub interfejsu.|  
|[v1_enum](../windows/v1-enum.md)|Określa, że przekazywane określonego typu wyliczenia jako jednostki 32-bitowych zamiast domyślnego 16-bitowych.|  
  
### <a name="union"></a>unia  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|[custom](../windows/custom-cpp.md)|Umożliwia zdefiniowanie własnego atrybutu.|  
|[export](../windows/export.md)|Powoduje to struktura danych, należy umieścić w pliku .idl.|  
|[first_is](../windows/first-is.md)|Określa indeks pierwszego elementu tablicy mają być przekazywane.|  
|[last_is](../windows/last-is.md)|Określa indeks ostatniego elementu tablicy mają być przekazywane.|  
|[length_is](../windows/length-is.md)|Określa liczbę elementów tablicy, które mają być przekazywane.|  
|[max_is](../windows/max-is.md)|Określa maksymalną wartość indeksu prawidłową tablicą.|  
|[size_is](../windows/size-is.md)|Określa rozmiar pamięci przydzielonej dla wskaźników o rozmiarze, wielkości wskaźniki do wskaźników o rozmiarze i jedno - lub tablic wielowymiarowych.|  
|[unique](../windows/unique-cpp.md)|Określa unikatowy wskaźnik.|  
|[uuid](../windows/uuid-cpp-attributes.md)|Określa unikatowy identyfikator dla klasy lub interfejsu.|  
  
### <a name="nonencapsulated-union"></a>Nonencapsulated Unii  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|[ms_union](../windows/ms-union.md)|Steruje wyrównaniem reprezentacji danych sieci nonencapsulated Unii.|  
|[no_injected_text](../windows/no-injected-text.md)|Zabezpiecza kompilator przed wprowadzanie kodu w wyniku użycia atrybutu.|  
  
### <a name="struct"></a>struktura   
  
|Atrybut|Opis|  
|---------------|-----------------|  
|[aggregatable](../windows/aggregatable.md)|Wskazuje, że klasa obsługuje agregację.|  
|[aggregates](../windows/aggregates.md)|Wskazuje, że formant agreguje klasy docelowej.|  
|[appobject](../windows/appobject.md)|Identyfikuje coclass jako obiekt aplikacji, który jest skojarzony z aplikacją pełną .exe i wskazuje, że funkcje i właściwości z koklas, globalnie dostępną w tej bibliotece typów.|  
|[coclass](../windows/coclass.md)|Tworzy formant ActiveX.|  
|[com_interface_entry —](../windows/com-interface-entry-cpp.md)|Dodaje wpis interfejsu do mapy COM.|  
|[control](../windows/control.md)|Określa, że typ zdefiniowany przez użytkownika kontrolki.|  
|[custom](../windows/custom-cpp.md)|Umożliwia zdefiniowanie własnego atrybutu.|  
|[db_column](../windows/db-column.md)|Wiąże określonej kolumny zestawu wierszy.|  
|[db_command](../windows/db-command.md)|Tworzy polecenie OLE DB.|  
|[db_param](../windows/db-param.md)|Zmienna określonego elementu członkowskiego jest skojarzona z parametrów wejściowych lub wyjściowych, a rozgranicza zmiennej.|  
|[db_source](../windows/db-source.md)|Tworzy połączenie ze źródłem danych.|  
|[db_table](../windows/db-table.md)|Zostanie otwarty tabeli OLE DB.|  
|[default](../windows/default-cpp.md)|Wskazuje, że niestandardowe lub zdefiniowane w obrębie klasy coclass dispinterface reprezentuje domyślny interfejs programowania.|  
|[defaultvtable](../windows/defaultvtable.md)|Definiuje interfejs jako domyślny interfejs vtable kontrolki.|  
|[event_receiver](../windows/event-receiver.md)|Tworzy odbiorca zdarzenia.|  
|[event_source](../windows/event-source.md)|Tworzy źródła zdarzenia.|  
|[export](../windows/export.md)|Powoduje to struktura danych, należy umieścić w pliku .idl.|  
|[first_is](../windows/first-is.md)|Określa indeks pierwszego elementu tablicy mają być przekazywane.|  
|[hidden](../windows/hidden.md)|Wskazuje, czy element istnieje, ale nie powinien być wyświetlany w przeglądarce zorientowanej na użytkownika.|  
|[implements_category](../windows/implements-category.md)|Określa kategorii składników zaimplementowane dla klasy.|  
|[last_is](../windows/last-is.md)|Określa indeks ostatniego elementu tablicy mają być przekazywane.|  
|[length_is](../windows/length-is.md)|Określa liczbę elementów tablicy, które mają być przekazywane.|  
|[max_is](../windows/max-is.md)|Określa maksymalną wartość indeksu prawidłową tablicą.|  
|[requires_category](../windows/requires-category.md)|Określa kategorie wymaganego składnika klasy docelowej.|  
|[size_is](../windows/size-is.md)|Określa rozmiar pamięci przydzielonej dla wskaźników o rozmiarze, wielkości wskaźniki do wskaźników o rozmiarze i jedno - lub tablic wielowymiarowych.|  
|[source](../windows/source-cpp.md)|W klasie określa interfejsy źródła obiektu COM dla punktów połączenia. W właściwości lub metody oznacza, że elementu członkowskiego zwraca obiekt lub wariant, który jest źródłem zdarzeń.|  
|[Wątkowość](../windows/threading-cpp.md)|Określa model wątkowości dla obiektu COM.|  
|[unique](../windows/unique-cpp.md)|Określa unikatowy wskaźnik.|  
|[uuid](../windows/uuid-cpp-attributes.md)|Określa unikatowy identyfikator dla klasy lub interfejsu.|  
|[Wersja](../windows/version-cpp.md)|Identyfikuje określoną wersję spośród wielu wersji klasy.|  
|[vi_progid](../windows/vi-progid.md)|Określa formularza niezależny od wersji identyfikatora ProgID.|  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty w zależności od zastosowania](../windows/attributes-by-usage.md)