---
title: '#Importowanie atrybuty (C++) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- '#import directive, attributes'
ms.assetid: 2a5085e3-82ee-4f83-892b-0aa6cc13863b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6a420294b2b7d2e0ff54b829d3177935f833a4e0
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/10/2018
ms.locfileid: "42464529"
---
# <a name="import-attributes-c"></a>Atrybuty #import (C++)
Zawiera łącza do atrybutów przy użyciu `#import` dyrektywy.  
  
**Microsoft Specific**  
  
Następujące atrybuty są dostępne dla `#import` dyrektywy.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|[auto_rename](../preprocessor/auto-rename.md)|Zmienia nazwę słowa zastrzeżone w języku C++, dodając dwa znaki podkreślenia (_) do nazwy zmiennej, aby rozwiązać potencjalne konflikty nazw.|  
|[auto_search](../preprocessor/auto-search.md)|Określa, że jeśli sama odwołuje się do innej biblioteki typów z #import odwołuje się do biblioteki typów, kompilator zrobić niejawne #import biblioteki typów.|  
|[embedded_idl](../preprocessor/embedded-idl.md)|Określa, czy biblioteki typów są zapisywane do pliku .tlh, z zachowanym kodem generowanych atrybutów.|  
|[exclude](../preprocessor/exclude-hash-import.md)|Pomija pliki nagłówkowe biblioteki typów generowanych elementów.|  
|[high_method_prefix](../preprocessor/high-method-prefix.md)|Określa prefiks, który ma być używany w nazwach właściwości ogólne i metody.|  
|[high_property_prefixes](../preprocessor/high-property-prefixes.md)|Określa alternatywne prefiksów trzy metody właściwości.|  
|[implementation_only](../preprocessor/implementation-only.md)|Powoduje pominięcie generowania pliku nagłówku .tlh (główny plik nagłówka).|  
|[include()](../preprocessor/include-parens.md)|Wyłącza automatyczne wykluczenia.|  
|[inject_statement](../preprocessor/inject-statement.md)|Wstawia jej argument jako tekst źródłowy do nagłówka biblioteki typów.|  
|[named_guids](../preprocessor/named-guids.md)|Informuje kompilator, aby zdefiniować i zainicjować zmienne identyfikator GUID w starym stylu formularza `LIBID_MyLib`, `CLSID_MyCoClass`, `IID_MyInterface`, i `DIID_MyDispInterface`.|  
|[no_auto_exclude](../preprocessor/no-auto-exclude.md)|Wyłącza automatyczne wykluczenia.|  
|[no_dual_interfaces](../preprocessor/no-dual-interfaces.md)|Zmienia sposób, kompilator generuje funkcje otoki dla metod podwójnego interfejsu.|  
|[no_implementation](../preprocessor/no-implementation.md)|Powoduje pominięcie generowania nagłówka .tli, który zawiera implementacje funkcji elementów członkowskich otoki.|  
|[no_namespace](../preprocessor/no-namespace.md)|Określa, że nazwa przestrzeni nazw nie są generowane przez kompilator.|  
|[no_registry](../preprocessor/no-registry.md)|Informuje kompilator, który nie należy przeszukiwać rejestru dla biblioteki typów.|  
|[no_search_namespace](../preprocessor/no-search-namespace.md)|Ma taką samą funkcjonalność jak [no_namespace](../preprocessor/no-namespace.md) atrybutu, ale jest używana w bibliotekach typu, które użyj dyrektywy #import z [auto_search —](../preprocessor/auto-search.md) atrybutu.|  
|[no_smart_pointers](../preprocessor/no-smart-pointers.md)|Pomija Tworzenie inteligentnych wskaźników dla wszystkich interfejsów w bibliotece typów.|  
|[raw_dispinterfaces](../preprocessor/raw-dispinterfaces.md)|Informuje kompilator, aby wygenerować otoki niskiego poziomu funkcji dispinterface metody i właściwości, które wywołują `IDispatch::Invoke` i zwracają kod błędu HRESULT.|  
|[raw_interfaces_only](../preprocessor/raw-interfaces-only.md)|Pomija generację funkcje otoki obsługi błędów i [właściwość](../cpp/property-cpp.md) deklaracji, korzystających z tych funkcji otoki.|  
|[raw_method_prefix](../preprocessor/raw-method-prefix.md)|Określa różne prefiks, aby uniknąć konfliktów nazw.|  
|[raw_native_types](../preprocessor/raw-native-types.md)|Wyłącza używanie klas obsługi COM w funkcjach otoki wysokiego poziomu, a zamiast tego wymusza stosowanie typów danych niskiego poziomu.|  
|[raw_property_prefixes](../preprocessor/raw-property-prefixes.md)|Określa alternatywne prefiksów trzy metody właściwości.|  
|[Zmień nazwę](../preprocessor/rename-hash-import.md)|Działania dotyczące problemów kolizji nazw.|  
|[rename_namespace](../preprocessor/rename-namespace.md)|Zmienia nazwę przestrzeni nazw, który znajduje się zawartość biblioteki typów.|  
|[rename_search_namespace](../preprocessor/rename-search-namespace.md)|Ma taką samą funkcjonalność jak [rename_namespace](../preprocessor/rename-namespace.md) atrybutu, ale jest używana w bibliotekach typu, które użyj dyrektywy #import z [auto_search —](../preprocessor/auto-search.md) atrybutu.|  
|[tlbid](../preprocessor/tlbid.md)|Umożliwia ładowanie bibliotek innych niż biblioteki typu podstawowego.|  
  
**END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 
[#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)