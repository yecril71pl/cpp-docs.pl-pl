---
title: Atrybuty IDL | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- attributes [C++], reference topics
- IDL attributes
- .idl files, attributes
- IDL files, attributes
- .idl files
ms.assetid: 04c596f4-c97b-4952-8053-316678b1d0b6
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 447c4369d7a80348dfb6c5eee54c49d76c1e8a4c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="idl-attributes"></a>atrybuty IDL
Tradycyjnie utrzymywanie pliku .idl oznacza, że do:  
  
-   Należy zapoznać się ze strukturą i składni pliku .idl, aby można było go zmodyfikować.  
  
-   Zależne od kreatora, który będzie można zmodyfikować niektórych aspektów pliku .idl.  
  
 Teraz można zmodyfikować pliku .idl w pliku kodu źródłowego przy użyciu programu Visual C++ IDL atrybutów. W wielu przypadkach atrybuty Visual C++ IDL mają taką samą nazwę jak MIDL atrybutów. Nazwa atrybutu Visual C++ IDL i atrybut MIDL są takie same, oznacza, że umieszczania atrybutów języka Visual C++ w pliku kodu źródłowego spowoduje zawierający jego atrybut MIDL namesake pliku .idl. Jednak atrybut Visual C++ IDL nie może udostępnić wszystkie funkcje atrybutu MIDL.  
  
 Gdy nie jest używany z [atrybuty COM](../windows/com-attributes.md), atrybuty IDL umożliwiają definiowanie interfejsów. Podczas kompilowania kodu źródłowego, atrybuty są używane do definiowania pliku .idl wygenerowany. Gdy jest używany z atrybutami Projekt ATL COM, niektóre IDL atrybutów, takich jak **coclass**, spowodować kodu można wprowadzić do projektu.  
  
 Należy pamiętać, że [idl_quote —](../windows/idl-quote.md) pozwala używać konstrukcji MIDL, które nie są obsługiwane w bieżącej wersji programu Visual C++. To i inne atrybuty, takie jak [importlib](../windows/importlib.md) i [includelib —](../windows/includelib-cpp.md) pomocy można korzystać z istniejących plików .idl w bieżącym projekcie Visual C++.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|[aggregatable](../windows/aggregatable.md)|Wskazuje, czy formant może agregować przez inny formant.|  
|[appobject](../windows/appobject.md)|Identyfikuje coclass jako obiekt aplikacji, który jest skojarzony z aplikacją pełne EXE i wskazuje, że właściwości klasy coclass i funkcje są ogólnie dostępna w tej bibliotece typu.|  
|[async_uuid](../windows/async-uuid.md)|Określa identyfikator UUID, który określa, że kompilator MIDL, aby zdefiniować synchroniczne i asynchroniczne wersje interfejsu COM.|  
|[bindable](../windows/bindable.md)|Wskazuje, że właściwość obsługuje powiązanie danych.|  
|[call_as](../windows/call-as.md)|Włącza funkcję nonremotable, która ma być zamapowany na funkcję zdalną.|  
|[Case](../windows/case-cpp.md)|Używane z [switch_type —](../windows/switch-type.md) atrybutu w Unii.|  
|[coclass](../windows/coclass.md)|Miejsca klasy definicji do pliku .idl jako klasy coclass.|  
|[control](../windows/control.md)|Określa, że typ zdefiniowany przez użytkownika jest formantu.|  
|[cpp_quote](../windows/cpp-quote.md)|Emituje określony ciąg bez znaków cudzysłowu do wygenerowanego pliku nagłówka.|  
|[defaultbind](../windows/defaultbind.md)|Wskazuje pojedynczą, które można powiązać właściwość, która najlepiej reprezentuje obiekt.|  
|[defaultcollelem](../windows/defaultcollelem.md)|Używane do optymalizacji kodu języka Visual Basic.|  
|[defaultvalue](../windows/defaultvalue.md)|Umożliwia określenie wartości domyślnej parametru opcjonalnego typu.|  
|[default](../windows/default-cpp.md)|Wskazuje, że niestandardowe lub dispinterface zdefiniowane w obrębie klasy coclass reprezentuje domyślny interfejs programowania.|  
|[defaultvtable](../windows/defaultvtable.md)|Definiuje interfejsu jako interfejsu domyślnego vtable dla formantu.|  
|[dispinterface](../windows/dispinterface.md)|Umieszcza interfejsu w pliku .idl jako interfejs wysyłania.|  
|[displaybind](../windows/displaybind.md)|Wskazuje właściwość, która powinna być wyświetlana użytkownikowi jak możliwa do powiązania.|  
|[dual](../windows/dual.md)|Umieszcza interfejsu w pliku .idl jako interfejs podwójny.|  
|[entry](../windows/entry.md)|Określa wyeksportowanej funkcji lub stała w module, określając punkt wejścia w bibliotece DLL.|  
|[first_is](../windows/first-is.md)|Określa indeks pierwszego elementu tablicy ma zostać przesłany.|  
|[helpcontext](../windows/helpcontext.md)|Określa identyfikator kontekstu, która pozwala użytkownikowi oglądać informacje o tym elemencie w pliku pomocy.|  
|[helpfile](../windows/helpfile.md)|Ustawia nazwę pliku pomocy dla biblioteki typów.|  
|[helpstringcontext](../windows/helpstringcontext.md)|Określa identyfikator tematu pomocy w formacie pliku .hlp lub .chm.|  
|[helpstringdll](../windows/helpstringdll.md)|Określa nazwę biblioteki DLL, aby wykonać wyszukiwanie ciągu dokumentu (lokalizacja).|  
|[helpstring](../windows/helpstring.md)|Określa ciąg znaków używany do opisania elementu, którego dotyczy.|  
|[hidden](../windows/hidden.md)|Wskazuje, czy element istnieje, ale nie powinien być wyświetlany w przeglądarce zorientowanej na użytkownika.|  
|[idl_module](../windows/idl-module.md)|Określa punkt wejścia w bibliotece DLL.|  
|[idl_quote](../windows/idl-quote.md)|Umożliwia korzystanie z atrybutów lub IDL konstrukcje, które nie są obsługiwane w bieżącej wersji programu Visual C++.|  
|[id](../windows/id.md)|Określa identyfikator DISPID dla funkcji członkowskiej (właściwości lub metody, w interfejsie lub dispinterface).|  
|[iid_is](../windows/iid-is.md)|Określa identyfikator IID interfejsu COM wskazywana przez wskaźnik interfejsu.|  
|[immediatebind](../windows/immediatebind.md)|Wskazuje, że bazy danych zostanie niezwłocznie powiadomiona o wszystkich zmianach właściwości obiektu powiązanego z danymi.|  
|[importlib](../windows/importlib.md)|Powoduje, że typy, które już zostały skompilowane w innej bibliotece typu dostępne do tworzenia biblioteki typów.|  
|[import](../windows/import.md)|Określa innego pliku .idl, .odl — lub nagłówek definicjami, którego ma dotyczyć odwołanie z pliku .idl głównego.|  
|[obejmują](../windows/include-cpp.md)|Określa co najmniej jeden plik nagłówka do uwzględnienia w pliku .idl wygenerowany.|  
|[includelib —](../windows/includelib-cpp.md)|Powoduje, że pliku .idl lub .h do uwzględnienia w pliku .idl wygenerowany.|  
|[in](../windows/in-cpp.md)|Wskazuje, że parametr zostanie przekazany z procedury wywołującej do procedury wywoływanej.|  
|[last_is](../windows/last-is.md)|Określa indeks przekazywanych ostatnim elemencie tablicy.|  
|[lcid](../windows/lcid.md)|Pozwala przekazać do funkcji identyfikator ustawień regionalnych.|  
|[length_is](../windows/length-is.md)|Określa liczbę elementów tablicy ma zostać przesłany.|  
|[licensed](../windows/licensed.md)|Wskazuje, że coclass, do którego jest stosowany jest licencjonowana i musi być utworzone przy użyciu **IClassFactory2**.|  
|[lokalne](../windows/local-cpp.md)|Umożliwia przy użyciu kompilatora MIDL jako generator nagłówka w nagłówku interfejsu. W przypadku poszczególnych funkcji wyznacza procedury lokalnym, dla których są generowane nie klas zastępczych.|  
|[max_is](../windows/max-is.md)|Określa maksymalną wartość indeksu tablicy prawidłowe.|  
|[Moduł](../windows/module-cpp.md)|Określa blok biblioteki w pliku .idl.|  
|[ms_union](../windows/ms-union.md)|Określa wyrównanie reprezentację danych sieci nonencapsulated Unii.|  
|[no_injected_text](../windows/no-injected-text.md)|Zabezpiecza kompilator przed wstrzyknięcie kodu w wyniku użycia atrybutu.|  
|[nonbrowsable](../windows/nonbrowsable.md)|Wskazuje, że element członkowski interfejsu nie powinien być wyświetlany w przeglądarce właściwości.|  
|[noncreatable](../windows/noncreatable.md)|Definiuje obiekt, który nie może występować samodzielnie.|  
|[nonextensible](../windows/nonextensible.md)|Określa, że `IDispatch` implementacji zawiera tylko właściwości i metod wymienionych w opisie interfejsu i nie może zostać rozszerzony o dodatkowe elementy członkowskie w czasie wykonywania.|  
|[object](../windows/object-cpp.md)|Określa niestandardowy interfejs; synonimem atrybutu niestandardowego.|  
|[odl](../windows/odl.md)|Identyfikuje interfejsu jako interfejsu język opisu obiektów (ODL).|  
|[oleautomation](../windows/oleautomation.md)|Wskazuje, że interfejs jest zgodna z automatyzacji.|  
|[opcjonalne](../windows/optional-cpp.md)|Określa opcjonalny parametr dla funkcji członkowskiej.|  
|[out](../windows/out-cpp.md)|Określa parametry wskaźnika, które zostaną zwrócone z procedury wywoływanej do procedury wywołującej (z serwera do klienta).|  
|[pointer_default](../windows/pointer-default.md)|Określa domyślny atrybut wskaźnik dla wszystkich wskaźników z wyjątkiem wskaźniki najwyższego poziomu, które są wyświetlane na listach parametrem.|  
|[pragma](../windows/pragma.md)|Emituje określony ciąg bez znaków cudzysłowu do pliku .idl wygenerowany.|  
|[progid](../windows/progid.md)|Określa identyfikator ProgID dla obiekt COM.|  
|[propget](../windows/propget.md)|Określa funkcję właściwości metody dostępu (get).|  
|[propputref](../windows/propputref.md)|Określa funkcję ustawienie właściwości, która korzysta z odwołaniem zamiast wartości.|  
|[propput](../windows/propput.md)|Określa funkcja ustawienie właściwości.|  
|[ptr](../windows/ptr.md)|Określa wskaźnik jako pełne wskaźnika.|  
|[public](../windows/public-cpp-attributes.md)|Zapewnia, że typem typedef przejdzie do biblioteki typów nawet wtedy, gdy go nie odwołuje się w pliku .idl.|  
|[zakres](../windows/range-cpp.md)|Określa zakresu wartości dozwoloną dla argumentów lub pól, których wartości są ustawione w czasie wykonywania.|  
|[readonly](../windows/readonly-cpp.md)|Zabrania używania przypisania do zmiennej.|  
|[ref](../windows/ref-cpp.md)|Identyfikuje wskaźnik odwołania.|  
|[requestedit](../windows/requestedit.md)|Wskazuje, że właściwość obsługuje **OnRequestEdit** powiadomień.|  
|[restricted](../windows/restricted.md)|Określa, że biblioteki lub członkiem modułu, interfejsem lub dispinterface nie może być wywoływana arbitralnie.|  
|[retval](../windows/retval.md)|Określa parametr, który otrzymuje wartość zwrotną z elementu członkowskiego.|  
|[size_is](../windows/size-is.md)|Określa rozmiar pamięci przydzielona dla wskaźników o rozmiarze o rozmiarze wskaźniki do wskaźników o rozmiarze i jedno - lub tablice wielowymiarowe.|  
|[źródło](../windows/source-cpp.md)|Wskazuje, że elementem członkowskim klasy, właściwości lub metody jest źródłem zdarzeń.|  
|[string](../windows/string-cpp.md)|Oznacza to, że jednowymiarowej tablicy `char`, `wchar_t`, **bajtów**, lub równoważne tablicy lub wskaźnika do tablicy takie muszą być traktowane jako ciąg.|  
|[switch_is](../windows/switch-is.md)|Określa wyrażenie lub identyfikator działający jako discriminant Unii, który wybiera element członkowski typu union.|  
|[switch_type](../windows/switch-type.md)|Określa typ zmiennej używanej jako discriminant Unii.|  
|[transmit_as](../windows/transmit-as.md)|Instruuje kompilator, aby skojarzyć typu przedstawioną kompilowania aplikacji, które klienta i serwera, z typem przesyłane.|  
|[uidefault](../windows/uidefault.md)|Wskazuje, że element członkowski typu informacji jest domyślny element członkowski do wyświetlenia w interfejsie użytkownika.|  
|[unikatowe](../windows/unique-cpp.md)|Określa unikatowy wskaźnika.|  
|[usesgetlasterror](../windows/usesgetlasterror.md)|Obiekt wywołujący informuje, że jeśli występuje błąd podczas wywoływania tej funkcji, wywołujący może wywoływać `GetLastError` można pobrać kod błędu.|  
|[Identyfikator UUID](../windows/uuid-cpp-attributes.md)|Określa unikatowy identyfikator dla klasy ani interfejsu.|  
|[v1_enum](../windows/v1-enum.md)|Określa, że przekazywane na określony typ wyliczeniowy jako jednostki 32-bitowe zamiast domyślnego 16-bitowych.|  
|[vararg](../windows/vararg.md)|Określa, że funkcja zostać zmienną liczbę argumentów.|  
|[vi_progid](../windows/vi-progid.md)|Określa niezależny od wersji formularza identyfikatora ProgID.|  
|[wire_marshal](../windows/wire-marshal.md)|Określa typ danych, który będzie używany do przesłania zamiast typu dane specyficzne dla aplikacji.|  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty według grup](../windows/attributes-by-group.md)   
 [Ograniczenia dotyczące atrybutów](http://msdn.microsoft.com/en-us/6e6c4329-f667-4869-b991-cbe9cb7a8f61)