---
title: Klasy atrybutów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++], class attributes
- class attributes
ms.assetid: fad04ea1-d8ff-46d4-bb42-2b4500a6ab60
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5b0057fa97805c093df7cac126e87f9af0a98a73
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42611896"
---
# <a name="class-attributes"></a>Atrybuty klasy

Następujące atrybuty dotyczą [klasy](../cpp/class-cpp.md) słowa kluczowego języka C++.

|Atrybut|Opis|
|---------------|-----------------|
|[aggregatable](../windows/aggregatable.md)|Wskazuje, że klasa obsługuje agregację.|
|[aggregates](../windows/aggregates.md)|Wskazuje, że formant agreguje klasy docelowej.|
|[appobject](../windows/appobject.md)|Identyfikuje coclass jako obiekt aplikacji, który jest skojarzony z aplikacją pełną .exe i wskazuje, że funkcje i właściwości z koklas, globalnie dostępną w tej bibliotece typów.|
|[przypadek](../windows/case-cpp.md)|Używane z [switch_type —](../windows/switch-type.md) atrybutu w Unii.|
|[coclass](../windows/coclass.md)|Tworzy formant ActiveX.|
|[com_interface_entry —](../windows/com-interface-entry-cpp.md)|Dodaje wpis interfejsu do mapy COM.|
|[control](../windows/control.md)|Określa, że typ zdefiniowany przez użytkownika kontrolki.|
|[custom](../windows/custom-cpp.md)|Umożliwia zdefiniowanie własnego atrybutu.|
|[db_command](../windows/db-command.md)|Tworzy polecenie OLE DB.|
|[db_param](../windows/db-param.md)|Zmienna określonego elementu członkowskiego jest skojarzona z parametrów wejściowych lub wyjściowych, a rozgranicza zmiennej.|
|[db_source](../windows/db-source.md)|Tworzy połączenie ze źródłem danych.|
|[db_table](../windows/db-table.md)|Zostanie otwarty tabeli OLE DB.|
|[default](../windows/default-cpp.md)|Wskazuje, że niestandardowe lub zdefiniowane w obrębie klasy coclass dispinterface reprezentuje domyślny interfejs programowania.|
|[defaultvtable](../windows/defaultvtable.md)|Definiuje interfejs jako domyślny interfejs vtable kontrolki.|
|[event_receiver](../windows/event-receiver.md)|Tworzy odbiorca zdarzenia.|
|[event_source](../windows/event-source.md)|Tworzy źródła zdarzenia.|
|[helpcontext](../windows/helpcontext.md)|Określa identyfikator kontekstu, który pozwala użytkownikowi oglądać informacje o tym elemencie w **pomocy** pliku.|
|[helpfile](../windows/helpfile.md)|Określa nazwę pliku pomocy dla biblioteki typów.|
|[helpstringcontext](../windows/helpstringcontext.md)|Określa identyfikator tematu pomocy w pliku hlp lub chm.|
|[helpstring](../windows/helpstring.md)|Określa ciąg znaków, który jest używany do opisania elementu, do której jest stosowany.|
|[hidden](../windows/hidden.md)|Wskazuje, czy element istnieje, ale nie powinien być wyświetlany w przeglądarce zorientowanej na użytkownika.|
|[Implementuje](../windows/implements-cpp.md)|Określa interfejsach wysyłki, które muszą być składowymi typu klasy coclass IDL.|
|[implements_category](../windows/implements-category.md)|Określa kategorii składników zaimplementowane dla klasy.|
|[Moduł](../windows/module-cpp.md)|Określa blok biblioteki w pliku .idl.|
|[noncreatable](../windows/noncreatable.md)|Definiuje obiekt, który nie może być utworzone samodzielnie.|
|[progid](../windows/progid.md)|Określa identyfikator ProgID kontrolki.|
|[registration_script](../windows/registration-script.md)|Wykonuje skrypt określoną rejestrację.|
|[requestedit](../windows/requestedit.md)|Wskazuje, że właściwość obsługuje `OnRequestEdit` powiadomień.|
|[source](../windows/source-cpp.md)|Określa interfejsy źródła kontrolki punktów połączenia w klasie. Właściwość lub metodę `source` atrybut wskazuje, że elementu członkowskiego zwraca obiekt lub `VARIANT` oznacza to źródło zdarzenia.|
|[support_error_info](../windows/support-error-info.md)|Obsługuje raportowanie błędów dla obiektu docelowego.|
|[Wątkowość](../windows/threading-cpp.md)|Określa model wątkowości dla formantu.|
|[uuid](../windows/uuid-cpp-attributes.md)|Określa unikatowy identyfikator dla klasy lub interfejsu.|
|[Wersja](../windows/version-cpp.md)|Identyfikuje określoną wersję spośród wielu wersji klasy.|
|[vi_progid](../windows/vi-progid.md)|Określa formularza niezależny od wersji identyfikatora ProgID.|

## <a name="see-also"></a>Zobacz też

[Atrybuty w zależności od zastosowania](../windows/attributes-by-usage.md)