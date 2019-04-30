---
title: Atrybuty metody (C++ COM)
ms.date: 10/02/2018
helpviewer_keywords:
- method attributes
- attributes [C++/CLI], reference topics
ms.assetid: b2313352-480d-488b-8c35-6242ffd3a549
ms.openlocfilehash: aa67d45dfc0fadd300caeaaeb8a7c25bb1c38bcb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62409178"
---
# <a name="method-attributes"></a>Atrybuty metody

Następujące atrybuty dotyczą metod w klasie, klasa coclass lub interfejs.

|Atrybut|Opis|
|---------------|-----------------|
|[bindable](bindable.md)|Wskazuje, że właściwość obsługuje powiązanie danych.|
|[call_as](call-as.md)|Włącza funkcję nonremotable mają być mapowane na funkcję zdalną.|
|[custom](custom-cpp.md)|Umożliwia zdefiniowanie własnego atrybutu.|
|[db_column](db-column.md)|Wiąże określonej kolumny zestawu wierszy.|
|[db_command](db-command.md)|Tworzy polecenie OLE DB.|
|[db_param](db-param.md)|Zmienna określonego elementu członkowskiego jest skojarzona z parametrów wejściowych lub wyjściowych, a rozgranicza zmiennej.|
|[db_source](db-source.md)|Tworzy połączenie ze źródłem danych.|
|[db_table](db-table.md)|Zostanie otwarty tabeli OLE DB.|
|[defaultbind](defaultbind.md)|Wskazuje pojedynczą, które można powiązać właściwość, która najlepiej reprezentuje obiekt.|
|[defaultcollelem](defaultcollelem.md)|Używane do optymalizacji kodu języka Visual Basic.|
|[displaybind](displaybind.md)|Wskazuje właściwość, która powinna być wyświetlana użytkownikowi jak możliwa do powiązania.|
|[helpcontext](helpcontext.md)|Określa identyfikator kontekstu, który pozwala użytkownikowi oglądać informacje o tym elemencie w **pomocy** pliku.|
|[helpfile](helpfile.md)|Ustawia nazwę **pomocy** pliku biblioteki typów.|
|[helpstring](helpstring.md)|Określa ciąg znaków, który jest używany do opisania elementu, do której jest stosowany.|
|[helpstringcontext](helpstringcontext.md)|Określa identyfikator tematu pomocy w pliku hlp lub chm.|
|[helpstringdll](helpstringdll.md)|Określa nazwę biblioteki DLL, aby wykonać wyszukiwanie ciągu dokumentu (lokalizacja).|
|[hidden](hidden.md)|Wskazuje, czy element istnieje, ale nie powinien być wyświetlany w przeglądarce zorientowanej na użytkownika.|
|[id](id.md)|Określa identyfikator DISPID dla funkcji członkowskiej (właściwość lub metodę w interfejsie lub dispinterface).|
|[immediatebind](immediatebind.md)|Wskazuje, że baza danych zostanie niezwłocznie powiadomiona o wszystkich zmianach właściwości obiektu powiązanych z danymi.|
|[in](in-cpp.md)|Wskazuje, że parametr zostanie przekazany z procedury wywołującej do procedury wywoływanej.|
|[local](local-cpp.md)|Umożliwia kompilatorowi MIDL jako generator nagłówka, gdy jest używana w nagłówku interfejsu. W przypadku użycia w poszczególnych funkcji, wyznacza lokalnej procedury, dla którego są generowane nie wycinki.|
|[nonbrowsable](nonbrowsable.md)|Wskazuje, czy składowej interfejsu nie powinien być wyświetlany w przeglądarce właściwości.|
|[propget](propget.md)|Określa funkcję metody dostępu właściwości.|
|[propput](propput.md)|Określa funkcję ustawienie właściwości.|
|[propputref](propputref.md)|Określa funkcję ustawienie właściwości, która używa odwołania, a nie wartość.|
|[ptr](ptr.md)|Określa wskaźnik jako pełna wskaźnika.|
|[range](range-cpp.md)|Określa zakres dopuszczalnych wartości dla argumentów lub pól, których wartości są ustawione w czasie wykonywania.|
|[requestedit](requestedit.md)|Wskazuje, że właściwość obsługuje `OnRequestEdit` powiadomień.|
|[restricted](restricted.md)|Określa, że jest członkiem moduł, interfejs lub dispinterface nie może być wywoływana arbitralnie.|
|[satype](satype.md)|Określa typ danych `SAFEARRAY` struktury.|
|[source](source-cpp.md)|Określa interfejsy źródła kontrolki punktów połączenia w klasie. Właściwość lub metodę `source` atrybut wskazuje, że elementu członkowskiego zwraca obiekt lub wariant, który jest źródłem zdarzeń.|
|[synchronize](synchronize.md)|Synchronizuje dostęp do metody docelowej.|
|[vararg](vararg.md)|Określa, że funkcja przyjmuje zmienną liczbę argumentów.|

## <a name="see-also"></a>Zobacz także

[Atrybuty w zależności od zastosowania](attributes-by-usage.md)