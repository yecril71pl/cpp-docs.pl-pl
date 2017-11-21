---
title: "Element TypeDef, Enum, Unii i struct — atrybuty | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- union attributes
- attributes [C++], reference topics
- struct attributes
- typedef attributes
- enum attributes
ms.assetid: f8a4fe94-dc02-4aed-bc31-3e500d42f4c7
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9bba47c5c0ea12ae7c1ae4f57adc24b58166ded8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="typedef-enum-union-and-struct-attributes"></a>Atrybuty Typedef, Enum, Union oraz Struct
Następujące atrybuty dotyczą [typedef](http://msdn.microsoft.com/en-us/cc96cf26-ba93-4179-951e-695d1f5fdcf1), [struktury](../cpp/struct-cpp.md), i [wyliczenia](../cpp/enumerations-cpp.md) słowa kluczowe języka C++.  
  
### <a name="typedef"></a>— klasa typedef  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|[Case](../windows/case-cpp.md)|Używane z [switch_type —](../windows/switch-type.md) atrybutu w **Unii**.|  
|[niestandardowe](../windows/custom-cpp.md)|Umożliwia zdefiniowanie własnego atrybutu.|  
|[Eksportuj](../windows/export.md)|Powoduje, że struktura danych mają być umieszczone w pliku .idl.|  
|[first_is —](../windows/first-is.md)|Określa indeks pierwszego elementu tablicy ma zostać przesłany.|  
|[helpcontext](../windows/helpcontext.md)|Określa identyfikator kontekstu, która pozwala użytkownikowi oglądać informacje o tym elemencie w pliku pomocy.|  
|[HelpFile](../windows/helpfile.md)|Ustawia nazwę pliku pomocy dla biblioteki typów.|  
|[HelpString —](../windows/helpstring.md)|Określa ciąg znaków używany do opisania elementu, którego dotyczy.|  
|[library_block —](../windows/library-block.md)|Umieszcza konstrukcję wewnątrz bloku biblioteki pliku .idl.|  
|[PTR](../windows/ptr.md)|Określa wskaźnik jako pełne wskaźnika.|  
|[publiczny](../windows/public-cpp-attributes.md)|Zapewnia, że typem typedef przejdzie do biblioteki typów nawet wtedy, gdy go nie odwołuje się w pliku .idl.|  
|[REF](../windows/ref-cpp.md)|Identyfikuje wskaźnik odwołania.|  
|[switch_is —](../windows/switch-is.md)|Określa wyrażenie lub identyfikator działający jako discriminant Unii, który wybiera element członkowski typu union.|  
|[switch_type —](../windows/switch-type.md)|Określa typ zmiennej używanej jako discriminant Unii.|  
|[unikatowe](../windows/unique-cpp.md)|Określa unikatowy wskaźnika.|  
|[wire_marshal —](../windows/wire-marshal.md)|Określa typ danych, który będzie używany do przesłania zamiast typu dane specyficzne dla aplikacji.|  
  
### <a name="enum"></a>enum  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|[niestandardowe](../windows/custom-cpp.md)|Umożliwia zdefiniowanie własnego atrybutu.|  
|[Eksportuj](../windows/export.md)|Powoduje, że struktura danych mają być umieszczone w pliku .idl.|  
|[Identyfikator UUID](../windows/uuid-cpp-attributes.md)|Określa unikatowy identyfikator dla klasy ani interfejsu.|  
|[v1_enum —](../windows/v1-enum.md)|Określa, że przekazywane na określony typ wyliczeniowy jako jednostki 32-bitowe zamiast domyślnego 16-bitowych.|  
  
### <a name="union"></a>unia  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|[niestandardowe](../windows/custom-cpp.md)|Umożliwia zdefiniowanie własnego atrybutu.|  
|[Eksportuj](../windows/export.md)|Powoduje, że struktura danych mają być umieszczone w pliku .idl.|  
|[first_is —](../windows/first-is.md)|Określa indeks pierwszego elementu tablicy ma zostać przesłany.|  
|[last_is —](../windows/last-is.md)|Określa indeks przekazywanych ostatnim elemencie tablicy.|  
|[length_is —](../windows/length-is.md)|Określa liczbę elementów tablicy ma zostać przesłany.|  
|[max_is —](../windows/max-is.md)|Określa maksymalną wartość indeksu tablicy prawidłowe.|  
|[size_is](../windows/size-is.md)|Określa rozmiar pamięci przydzielona dla wskaźników o rozmiarze o rozmiarze wskaźniki do wskaźników o rozmiarze i jedno - lub tablice wielowymiarowe.|  
|[unikatowe](../windows/unique-cpp.md)|Określa unikatowy wskaźnika.|  
|[Identyfikator UUID](../windows/uuid-cpp-attributes.md)|Określa unikatowy identyfikator dla klasy ani interfejsu.|  
  
### <a name="nonencapsulated-union"></a>Nonencapsulated Unii  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|[ms_union —](../windows/ms-union.md)|Określa wyrównanie reprezentację danych sieci nonencapsulated Unii.|  
|[no_injected_text](../windows/no-injected-text.md)|Zabezpiecza kompilator przed wstrzyknięcie kodu w wyniku użycia atrybutu.|  
  
### <a name="struct"></a>struktura   
  
|Atrybut|Opis|  
|---------------|-----------------|  
|[agregowaniu](../windows/aggregatable.md)|Wskazuje, że klasa obsługuje agregacji.|  
|[wartości zagregowane](../windows/aggregates.md)|Wskazuje, czy formant agreguje klasy docelowej.|  
|[appobject —](../windows/appobject.md)|Identyfikuje coclass jako obiekt aplikacji, który jest skojarzony z aplikacją pełne .exe i wskazuje, że właściwości klasy coclass i funkcje są ogólnie dostępna w tej bibliotece typu.|  
|[Klasa coclass](../windows/coclass.md)|Tworzy kontrolkę ActiveX.|  
|[com_interface_entry —](../windows/com-interface-entry-cpp.md)|Dodaje wpis interfejs do mapy COM.|  
|[Formant](../windows/control.md)|Określa, że typ zdefiniowany przez użytkownika jest formantu.|  
|[niestandardowe](../windows/custom-cpp.md)|Umożliwia zdefiniowanie własnego atrybutu.|  
|[db_column —](../windows/db-column.md)|Wiąże określonej kolumny zestawu wierszy.|  
|[db_command —](../windows/db-command.md)|Tworzy polecenia OLE DB.|  
|[db_param —](../windows/db-param.md)|Kojarzy zmiennej określonego elementu członkowskiego z parametrem wejściowych lub wyjściowych i rozgranicza zmiennej.|  
|[db_source —](../windows/db-source.md)|Tworzy połączenie ze źródłem danych.|  
|[db_table —](../windows/db-table.md)|Otwiera tabeli OLE DB.|  
|[domyślne](../windows/default-cpp.md)|Wskazuje, że niestandardowe lub dispinterface zdefiniowane w obrębie klasy coclass reprezentuje domyślny interfejs programowania.|  
|[defaultvtable](../windows/defaultvtable.md)|Definiuje interfejsu jako interfejsu domyślnego vtable dla formantu.|  
|[event_receiver](../windows/event-receiver.md)|Tworzy odbiorca zdarzenia.|  
|[event_source —](../windows/event-source.md)|Tworzy źródła zdarzenia.|  
|[Eksportuj](../windows/export.md)|Powoduje, że struktura danych mają być umieszczone w pliku .idl.|  
|[first_is —](../windows/first-is.md)|Określa indeks pierwszego elementu tablicy ma zostać przesłany.|  
|[ukryte](../windows/hidden.md)|Wskazuje, czy element istnieje, ale nie powinien być wyświetlany w przeglądarce zorientowanej na użytkownika.|  
|[implements_category —](../windows/implements-category.md)|Określa kategorii składników zaimplementowane dla klasy.|  
|[last_is —](../windows/last-is.md)|Określa indeks przekazywanych ostatnim elemencie tablicy.|  
|[length_is —](../windows/length-is.md)|Określa liczbę elementów tablicy ma zostać przesłany.|  
|[max_is —](../windows/max-is.md)|Określa maksymalną wartość indeksu tablicy prawidłowe.|  
|[requires_category —](../windows/requires-category.md)|Określa wymagany składnik kategorii klasy docelowej.|  
|[size_is](../windows/size-is.md)|Określa rozmiar pamięci przydzielona dla wskaźników o rozmiarze o rozmiarze wskaźniki do wskaźników o rozmiarze i jedno - lub tablice wielowymiarowe.|  
|[źródło](../windows/source-cpp.md)|W klasie określa interfejsów źródłowego obiektu COM dla punkty połączenia. W właściwości lub metody oznacza, że element członkowski zwraca obiekt lub Typ VARIANT, który jest źródłem zdarzeń.|  
|[wątkowość](../windows/threading-cpp.md)|Określa model wątkowości dla obiekt COM.|  
|[unikatowe](../windows/unique-cpp.md)|Określa unikatowy wskaźnika.|  
|[Identyfikator UUID](../windows/uuid-cpp-attributes.md)|Określa unikatowy identyfikator dla klasy ani interfejsu.|  
|[Wersja](../windows/version-cpp.md)|Identyfikuje określoną wersją wśród wielu wersji klasy.|  
|[vi_progid —](../windows/vi-progid.md)|Określa niezależny od wersji formularza identyfikatora ProgID.|  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty w zależności od użycia](../windows/attributes-by-usage.md)