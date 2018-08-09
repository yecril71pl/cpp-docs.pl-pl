---
title: Atrybuty metody | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- method attributes
- attributes [C++], reference topics
ms.assetid: b2313352-480d-488b-8c35-6242ffd3a549
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fd5f7bb72e1107fe561acef4d6cc3f3ecb87ed59
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2018
ms.locfileid: "40016859"
---
# <a name="method-attributes"></a>Atrybuty metody
Następujące atrybuty dotyczą metod w klasie, klasa coclass lub interfejs.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|[bindable](../windows/bindable.md)|Wskazuje, że właściwość obsługuje powiązanie danych.|  
|[call_as](../windows/call-as.md)|Włącza funkcję nonremotable mają być mapowane na funkcję zdalną.|  
|[custom](../windows/custom-cpp.md)|Umożliwia zdefiniowanie własnego atrybutu.|  
|[db_column](../windows/db-column.md)|Wiąże określonej kolumny zestawu wierszy.|  
|[db_command](../windows/db-command.md)|Tworzy polecenie OLE DB.|  
|[db_param](../windows/db-param.md)|Zmienna określonego elementu członkowskiego jest skojarzona z parametrów wejściowych lub wyjściowych, a rozgranicza zmiennej.|  
|[db_source](../windows/db-source.md)|Tworzy połączenie ze źródłem danych.|  
|[db_table](../windows/db-table.md)|Zostanie otwarty tabeli OLE DB.|  
|[defaultbind](../windows/defaultbind.md)|Wskazuje pojedynczą, które można powiązać właściwość, która najlepiej reprezentuje obiekt.|  
|[defaultcollelem](../windows/defaultcollelem.md)|Używane do optymalizacji kodu języka Visual Basic.|  
|[displaybind](../windows/displaybind.md)|Wskazuje właściwość, która powinna być wyświetlana użytkownikowi jak możliwa do powiązania.|  
|[helpcontext](../windows/helpcontext.md)|Określa identyfikator kontekstu, który pozwala użytkownikowi oglądać informacje o tym elemencie w **pomocy** pliku.|  
|[helpfile](../windows/helpfile.md)|Ustawia nazwę **pomocy** pliku biblioteki typów.|  
|[helpstring](../windows/helpstring.md)|Określa ciąg znaków, który jest używany do opisania elementu, do której jest stosowany.|  
|[helpstringcontext](../windows/helpstringcontext.md)|Określa identyfikator tematu pomocy w pliku hlp lub chm.|  
|[helpstringdll](../windows/helpstringdll.md)|Określa nazwę biblioteki DLL, aby wykonać wyszukiwanie ciągu dokumentu (lokalizacja).|  
|[hidden](../windows/hidden.md)|Wskazuje, czy element istnieje, ale nie powinien być wyświetlany w przeglądarce zorientowanej na użytkownika.|  
|[id](../windows/id.md)|Określa identyfikator DISPID dla funkcji członkowskiej (właściwość lub metodę w interfejsie lub dispinterface).|  
|[immediatebind](../windows/immediatebind.md)|Wskazuje, że baza danych zostanie niezwłocznie powiadomiona o wszystkich zmianach właściwości obiektu powiązanych z danymi.|  
|[in](../windows/in-cpp.md)|Wskazuje, że parametr zostanie przekazany z procedury wywołującej do procedury wywoływanej.|  
|[lokalne](../windows/local-cpp.md)|Umożliwia kompilatorowi MIDL jako generator nagłówka, gdy jest używana w nagłówku interfejsu. W przypadku użycia w poszczególnych funkcji, wyznacza lokalnej procedury, dla którego są generowane nie wycinki.|  
|[nonbrowsable](../windows/nonbrowsable.md)|Wskazuje, czy składowej interfejsu nie powinien być wyświetlany w przeglądarce właściwości.|  
|[propget](../windows/propget.md)|Określa funkcję metody dostępu właściwości.|  
|[propput](../windows/propput.md)|Określa funkcję ustawienie właściwości.|  
|[propputref](../windows/propputref.md)|Określa funkcję ustawienie właściwości, która używa odwołania, a nie wartość.|  
|[ptr](../windows/ptr.md)|Określa wskaźnik jako pełna wskaźnika.|  
|[Zakres](../windows/range-cpp.md)|Określa zakres dopuszczalnych wartości dla argumentów lub pól, których wartości są ustawione w czasie wykonywania.|  
|[requestedit](../windows/requestedit.md)|Wskazuje, że właściwość obsługuje `OnRequestEdit` powiadomień.|  
|[restricted](../windows/restricted.md)|Określa, że jest członkiem moduł, interfejs lub dispinterface nie może być wywoływana arbitralnie.|  
|[satype](../windows/satype.md)|Określa typ danych `SAFEARRAY` struktury.|  
|[source](../windows/source-cpp.md)|Określa interfejsy źródła kontrolki punktów połączenia w klasie. Właściwość lub metodę `source` atrybut wskazuje, że elementu członkowskiego zwraca obiekt lub wariant, który jest źródłem zdarzeń.|  
|[synchronize](../windows/synchronize.md)|Synchronizuje dostęp do metody docelowej.|  
|[vararg](../windows/vararg.md)|Określa, że funkcja przyjmuje zmienną liczbę argumentów.|  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty w zależności od zastosowania](../windows/attributes-by-usage.md)