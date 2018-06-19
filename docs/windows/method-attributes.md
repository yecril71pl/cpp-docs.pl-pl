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
ms.openlocfilehash: 9d2efe55058ab2ace7530afee7255b2ba08377b0
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33879825"
---
# <a name="method-attributes"></a>Atrybuty metody
Następujące atrybuty dotyczą metody w klasie, coclass lub interfejs.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|[bindable](../windows/bindable.md)|Wskazuje, że właściwość obsługuje powiązanie danych.|  
|[call_as](../windows/call-as.md)|Włącza funkcję nonremotable, która ma być zamapowany na funkcję zdalną.|  
|[custom](../windows/custom-cpp.md)|Umożliwia zdefiniowanie własnego atrybutu.|  
|[db_column](../windows/db-column.md)|Wiąże określonej kolumny zestawu wierszy.|  
|[db_command](../windows/db-command.md)|Tworzy polecenia OLE DB.|  
|[db_param](../windows/db-param.md)|Kojarzy zmiennej określonego elementu członkowskiego z parametrem wejściowych lub wyjściowych i rozgranicza zmiennej.|  
|[db_source](../windows/db-source.md)|Tworzy połączenie ze źródłem danych.|  
|[db_table](../windows/db-table.md)|Otwiera tabeli OLE DB.|  
|[defaultbind](../windows/defaultbind.md)|Wskazuje pojedynczą, które można powiązać właściwość, która najlepiej reprezentuje obiekt.|  
|[defaultcollelem](../windows/defaultcollelem.md)|Używane do optymalizacji kodu języka Visual Basic.|  
|[displaybind](../windows/displaybind.md)|Wskazuje właściwość, która powinna być wyświetlana użytkownikowi jak możliwa do powiązania.|  
|[helpcontext](../windows/helpcontext.md)|Określa identyfikator kontekstu, która pozwala użytkownikowi oglądać informacje o tym elemencie w pliku pomocy.|  
|[helpfile](../windows/helpfile.md)|Ustawia nazwę pliku pomocy dla biblioteki typów.|  
|[helpstring](../windows/helpstring.md)|Określa ciąg znaków używany do opisania elementu, którego dotyczy.|  
|[helpstringcontext](../windows/helpstringcontext.md)|Określa identyfikator tematu pomocy w formacie pliku .hlp lub .chm.|  
|[helpstringdll](../windows/helpstringdll.md)|Określa nazwę biblioteki DLL, aby wykonać wyszukiwanie ciągu dokumentu (lokalizacja).|  
|[hidden](../windows/hidden.md)|Wskazuje, czy element istnieje, ale nie powinien być wyświetlany w przeglądarce zorientowanej na użytkownika.|  
|[id](../windows/id.md)|Określa identyfikator DISPID dla funkcji członkowskiej (właściwości lub metody, w interfejsie lub dispinterface).|  
|[immediatebind](../windows/immediatebind.md)|Wskazuje, że bazy danych zostanie niezwłocznie powiadomiona o wszystkich zmianach właściwości obiektu powiązanego z danymi.|  
|[in](../windows/in-cpp.md)|Wskazuje, że parametr zostanie przekazany z procedury wywołującej do procedury wywoływanej.|  
|[lokalne](../windows/local-cpp.md)|Umożliwia przy użyciu kompilatora MIDL jako generator nagłówka w nagłówku interfejsu. W przypadku poszczególnych funkcji wyznacza procedury lokalnym, dla których są generowane nie klas zastępczych.|  
|[nonbrowsable](../windows/nonbrowsable.md)|Wskazuje, że element członkowski interfejsu nie powinien być wyświetlany w przeglądarce właściwości.|  
|[propget](../windows/propget.md)|Określa funkcja dostępu właściwości.|  
|[propput](../windows/propput.md)|Określa funkcję ustawienie właściwości.|  
|[propputref](../windows/propputref.md)|Określa ustawienie właściwości funkcję, która korzysta z odwołaniem zamiast wartości.|  
|[ptr](../windows/ptr.md)|Określa wskaźnik jako pełne wskaźnika.|  
|[Zakres](../windows/range-cpp.md)|Określa zakresu wartości dozwoloną dla argumentów lub pól, których wartości są ustawione w czasie wykonywania.|  
|[requestedit](../windows/requestedit.md)|Wskazuje, że właściwość obsługuje **OnRequestEdit** powiadomień.|  
|[restricted](../windows/restricted.md)|Określa, czy członek modułu, interfejsem lub dispinterface nie może być wywoływana arbitralnie.|  
|[satype](../windows/satype.md)|Określa typ danych **SAFEARRAY** struktury.|  
|[source](../windows/source-cpp.md)|Określa formantu interfejsów źródłowych punktów połączenia w klasie. Właściwości lub metody **źródła** atrybut wskazuje, że element członkowski zwraca obiekt lub Typ VARIANT, który jest źródłem zdarzeń.|  
|[synchronize](../windows/synchronize.md)|Synchronizuje dostęp do metody docelowej.|  
|[vararg](../windows/vararg.md)|Określa, że funkcja zostać zmienną liczbę argumentów.|  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty w zależności od zastosowania](../windows/attributes-by-usage.md)