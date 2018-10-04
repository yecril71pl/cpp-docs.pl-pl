---
title: Klasy atrybutów (C++ COM) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++/CLI], class attributes
ms.assetid: fad04ea1-d8ff-46d4-bb42-2b4500a6ab60
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a727bcf53a11e98ffd7e037037452c6bbdc4fe8a
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2018
ms.locfileid: "48789628"
---
# <a name="class-attributes"></a>Atrybuty klasy

Następujące atrybuty dotyczą [klasy](../../cpp/class-cpp.md) słowa kluczowego języka C++.

|Atrybut|Opis|
|---------------|-----------------|
|[aggregatable](aggregatable.md)|Wskazuje, że klasa obsługuje agregację.|
|[aggregates](aggregates.md)|Wskazuje, że formant agreguje klasy docelowej.|
|[appobject](appobject.md)|Identyfikuje coclass jako obiekt aplikacji, który jest skojarzony z aplikacją pełną .exe i wskazuje, że funkcje i właściwości z koklas, globalnie dostępną w tej bibliotece typów.|
|[przypadek](case-cpp.md)|Używane z [switch_type —](switch-type.md) atrybutu w Unii.|
|[coclass](coclass.md)|Tworzy formant ActiveX.|
|[com_interface_entry —](com-interface-entry-cpp.md)|Dodaje wpis interfejsu do mapy COM.|
|[control](control.md)|Określa, że typ zdefiniowany przez użytkownika kontrolki.|
|[custom](custom-cpp.md)|Umożliwia zdefiniowanie własnego atrybutu.|
|[db_command](db-command.md)|Tworzy polecenie OLE DB.|
|[db_param](db-param.md)|Zmienna określonego elementu członkowskiego jest skojarzona z parametrów wejściowych lub wyjściowych, a rozgranicza zmiennej.|
|[db_source](db-source.md)|Tworzy połączenie ze źródłem danych.|
|[db_table](db-table.md)|Zostanie otwarty tabeli OLE DB.|
|[default](default-cpp.md)|Wskazuje, że niestandardowe lub zdefiniowane w obrębie klasy coclass dispinterface reprezentuje domyślny interfejs programowania.|
|[defaultvtable](defaultvtable.md)|Definiuje interfejs jako domyślny interfejs vtable kontrolki.|
|[event_receiver](event-receiver.md)|Tworzy odbiorca zdarzenia.|
|[event_source](event-source.md)|Tworzy źródła zdarzenia.|
|[helpcontext](helpcontext.md)|Określa identyfikator kontekstu, który pozwala użytkownikowi oglądać informacje o tym elemencie w **pomocy** pliku.|
|[helpfile](helpfile.md)|Określa nazwę pliku pomocy dla biblioteki typów.|
|[helpstringcontext](helpstringcontext.md)|Określa identyfikator tematu pomocy w pliku hlp lub chm.|
|[helpstring](helpstring.md)|Określa ciąg znaków, który jest używany do opisania elementu, do której jest stosowany.|
|[hidden](hidden.md)|Wskazuje, czy element istnieje, ale nie powinien być wyświetlany w przeglądarce zorientowanej na użytkownika.|
|[Implementuje](implements-cpp.md)|Określa interfejsach wysyłki, które muszą być składowymi typu klasy coclass IDL.|
|[implements_category](implements-category.md)|Określa kategorii składników zaimplementowane dla klasy.|
|[Moduł](module-cpp.md)|Określa blok biblioteki w pliku .idl.|
|[noncreatable](noncreatable.md)|Definiuje obiekt, który nie może być utworzone samodzielnie.|
|[progid](progid.md)|Określa identyfikator ProgID kontrolki.|
|[registration_script](registration-script.md)|Wykonuje skrypt określoną rejestrację.|
|[requestedit](requestedit.md)|Wskazuje, że właściwość obsługuje `OnRequestEdit` powiadomień.|
|[source](source-cpp.md)|Określa interfejsy źródła kontrolki punktów połączenia w klasie. Właściwość lub metodę `source` atrybut wskazuje, że elementu członkowskiego zwraca obiekt lub `VARIANT` oznacza to źródło zdarzenia.|
|[support_error_info](support-error-info.md)|Obsługuje raportowanie błędów dla obiektu docelowego.|
|[Wątkowość](threading-cpp.md)|Określa model wątkowości dla formantu.|
|[uuid](uuid-cpp-attributes.md)|Określa unikatowy identyfikator dla klasy lub interfejsu.|
|[Wersja](version-cpp.md)|Identyfikuje określoną wersję spośród wielu wersji klasy.|
|[vi_progid](vi-progid.md)|Określa formularza niezależny od wersji identyfikatora ProgID.|

## <a name="see-also"></a>Zobacz też

[Atrybuty w zależności od zastosowania](attributes-by-usage.md)