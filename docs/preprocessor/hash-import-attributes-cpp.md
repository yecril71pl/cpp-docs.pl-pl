---
title: "#<a name=\"import-attributes-c--microsoft-docs\"></a>Importowanie atrybutów (C++) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: '#import directive, attributes'
ms.assetid: 2a5085e3-82ee-4f83-892b-0aa6cc13863b
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d5c2da30fd2b92ea302c40dc7dbef71499fdecdf
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="import-attributes-c"></a>Atrybuty #import (C++)
Zawiera łącza do atrybuty używane dyrektywy #import.  
  
 **Dotyczące firmy Microsoft**  
  
 Następujące atrybuty są dostępne dla dyrektywy #import.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|[auto_rename](../preprocessor/auto-rename.md)|Zmienia nazwę słowa zastrzeżone w języku C++ przez dołączenie do nazwy zmiennej, aby rozwiązać potencjalne konflikty nazw dwa znaki podkreślenia (_).|  
|[auto_search](../preprocessor/auto-search.md)|Określa, że z #import odwołuje się do biblioteki typów, a sama odwołuje się do innego biblioteki typów, kompilator można wykonać niejawnej #import biblioteki typów.|  
|[embedded_idl](../preprocessor/embedded-idl.md)|Określa, czy biblioteki typów są zapisywane do pliku danych .tlh — kod wygenerowany przez atrybut zachowane.|  
|[Wyklucz](../preprocessor/exclude-hash-import.md)|Wyklucza elementów z generowaną pliki nagłówków biblioteki typu.|  
|[high_method_prefix](../preprocessor/high-method-prefix.md)|Określa prefiks do użycia w nazewnictwa ogólne właściwości i metody.|  
|[high_property_prefixes](../preprocessor/high-property-prefixes.md)|Określa alternatywny prefiksów dla trzech metod właściwości.|  
|[implementation_only](../preprocessor/implementation-only.md)|Pomija generację .tlh — plik nagłówka (plik nagłówka głównej).|  
|[include()](../preprocessor/include-parens.md)|Wyłącza automatyczne wyłączenie.|  
|[inject_statement](../preprocessor/inject-statement.md)|Wstawia jej argument jako tekst źródłowy do nagłówka biblioteki typów.|  
|[named_guids](../preprocessor/named-guids.md)|Informuje kompilator, aby zdefiniować i zainicjować zmienne identyfikatora GUID w starym stylu formularza **LIBID_MyLib**, **CLSID_MyCoClass**, **IID_MyInterface**, i **DIID _MyDispInterface**.|  
|[no_auto_exclude](../preprocessor/no-auto-exclude.md)|Wyłącza automatyczne wyłączenie.|  
|[no_dual_interfaces](../preprocessor/no-dual-interfaces.md)|Zmienia sposób kompilator generuje funkcje otoki dla metody interfejsu podwójny.|  
|[no_implementation](../preprocessor/no-implementation.md)|Pomija generację nagłówka .tli, który zawiera implementacje funkcji Członkowskich otoki.|  
|[no_namespace](../preprocessor/no-namespace.md)|Określa, że nazwa przestrzeni nazw nie jest generowana przez kompilator.|  
|[no_registry](../preprocessor/no-registry.md)|Informuje kompilator, aby nie wyszukiwania rejestru dla biblioteki typów.|  
|[no_search_namespace](../preprocessor/no-search-namespace.md)|Ma te same funkcje co [no_namespace —](../preprocessor/no-namespace.md) atrybutu, ale jest używana na typ biblioteki, w których można użyć dyrektywy #import z [auto_search —](../preprocessor/auto-search.md) atrybutu.|  
|[no_smart_pointers](../preprocessor/no-smart-pointers.md)|Pomija tworzenie wskaźników inteligentne dla wszystkich interfejsów w bibliotece typów.|  
|[raw_dispinterfaces](../preprocessor/raw-dispinterfaces.md)|Informuje kompilator, aby wygenerować otoki niskiego poziomu funkcji dispinterface metody i właściwości, które wywołują **IDispatch::Invoke** i zwracać `HRESULT` kod błędu.|  
|[raw_interfaces_only](../preprocessor/raw-interfaces-only.md)|Pomija generację funkcje otoki Obsługa błędów i [właściwości](../cpp/property-cpp.md) deklaracje korzystających z tych funkcji otoki.|  
|[raw_method_prefix](../preprocessor/raw-method-prefix.md)|Określa różne prefiksu, aby uniknąć konfliktów nazw.|  
|[raw_native_types](../preprocessor/raw-native-types.md)|Wyłącza używanie klas obsługi COM w funkcjach otoki wysokiego poziomu, a zamiast tego wymusza stosowanie typów danych niskiego poziomu.|  
|[raw_property_prefixes](../preprocessor/raw-property-prefixes.md)|Określa alternatywny prefiksów dla trzech metod właściwości.|  
|[Zmień nazwę](../preprocessor/rename-hash-import.md)|Sprawdza się wokół problemów kolizji nazw.|  
|[rename_namespace](../preprocessor/rename-namespace.md)|Zmienia nazwę przestrzeni nazw, która zawiera zawartość biblioteki typów.|  
|[rename_search_namespace](../preprocessor/rename-search-namespace.md)|Ma te same funkcje co [rename_namespace —](../preprocessor/rename-namespace.md) atrybutu, ale jest używana na typ biblioteki, w których można użyć dyrektywy #import z [auto_search —](../preprocessor/auto-search.md) atrybutu.|  
|[tlbid](../preprocessor/tlbid.md)|Umożliwia ładowanie biblioteki innego niż biblioteki typu podstawowego.|  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)