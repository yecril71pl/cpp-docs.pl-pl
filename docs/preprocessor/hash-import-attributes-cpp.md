---
title: '#Importuj atrybuty (C++)'
ms.date: 08/29/2019
helpviewer_keywords:
- '#import directive, attributes'
ms.assetid: 2a5085e3-82ee-4f83-892b-0aa6cc13863b
ms.openlocfilehash: 7e0de241bd27269d7d758c49bc54c4bf435cf383
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220092"
---
# <a name="import-attributes-c"></a>Atrybuty #import (C++)

Zawiera linki do atrybutów używanych z `#import` dyrektywą.

**Microsoft Specific**

Następujące atrybuty są dostępne dla `#import` dyrektywy.

|Atrybut|Opis|
|---------------|-----------------|
|[auto_rename](../preprocessor/auto-rename.md)|Zmienia nazwy wyrazów C++ zarezerwowanych, dołączając dwa znaki podkreślenia (__) do nazwy zmiennej, aby rozwiązać potencjalne konflikty nazw.|
|[auto_search](../preprocessor/auto-search.md)|Określa, że gdy do biblioteki typów odwołuje się #import i sama odwołuje się do innej biblioteki typów, kompilator może wykonać niejawną #import dla innej biblioteki typów.|
|[embedded_idl](../preprocessor/embedded-idl.md)|Określa, że biblioteka typów jest zapisywana w pliku TLH z zachowaniem kodu generowanego przez atrybut.|
|[exclude](../preprocessor/exclude-hash-import.md)|Wyklucza elementy z generowanych plików nagłówkowych biblioteki typów.|
|[high_method_prefix](../preprocessor/high-method-prefix.md)|Określa prefiks do użycia podczas nazywania właściwości i metod wysokiego poziomu.|
|[high_property_prefixes](../preprocessor/high-property-prefixes.md)|Określa alternatywne prefiksy dla trzech metod właściwości.|
|[implementation_only](../preprocessor/implementation-only.md)|Pomija generowanie pliku nagłówkowego. tlh (podstawowy plik nagłówkowy).|
|[include()](../preprocessor/include-parens.md)|Wyłącza automatyczne wykluczenie.|
|[inject_statement](../preprocessor/inject-statement.md)|Wstawia swój argument jako tekst źródłowy do nagłówka biblioteki typów.|
|[named_guids](../preprocessor/named-guids.md)|Instruuje kompilator, aby definiować i inicjować zmienne GUID w starym stylu, w `LIBID_MyLib`postaci `CLSID_MyCoClass` `IID_MyInterface`,, i `DIID_MyDispInterface`.|
|[no_auto_exclude](../preprocessor/no-auto-exclude.md)|Wyłącza automatyczne wykluczenie.|
|[no_dual_interfaces](../preprocessor/no-dual-interfaces.md)|Zmienia sposób, w jaki kompilator generuje funkcje otoki dla dwóch metod interfejsu.|
|[no_implementation](../preprocessor/no-implementation.md)|Pomija generowanie nagłówka. tli, który zawiera implementacje funkcji elementu członkowskiego otoki.|
|[no_namespace](../preprocessor/no-namespace.md)|Określa, że nazwa przestrzeni nazw nie jest generowana przez kompilator.|
|[no_registry](../preprocessor/no-registry.md)|Instruuje kompilator, aby nie przeszukiwać rejestru dla bibliotek typów.|
|[no_search_namespace](../preprocessor/no-search-namespace.md)|Ma taką samą funkcjonalność jak atrybut [no_namespace](../preprocessor/no-namespace.md) , ale jest używany w bibliotekach typów, które używają dyrektywy #import z atrybutem [auto_search](../preprocessor/auto-search.md) .|
|[no_smart_pointers](../preprocessor/no-smart-pointers.md)|Pomija Tworzenie inteligentnych wskaźników dla wszystkich interfejsów w bibliotece typów.|
|[raw_dispinterfaces](../preprocessor/raw-dispinterfaces.md)|Instruuje kompilator, aby generował funkcje otoki niskiego poziomu dla metod dispinterface i właściwości `IDispatch::Invoke` , które wywołują i zwracają kod błędu HRESULT.|
|[raw_interfaces_only](../preprocessor/raw-interfaces-only.md)|Pomija generowanie funkcji otoki obsługi błędów i deklaracji [Właściwości](../cpp/property-cpp.md) , które korzystają z tych funkcji otoki.|
|[raw_method_prefix](../preprocessor/raw-method-prefix.md)|Określa inny prefiks, aby uniknąć kolizji nazw.|
|[raw_native_types](../preprocessor/raw-native-types.md)|Wyłącza korzystanie z klas obsługi COM w funkcjach otoki wysokiego poziomu i wymusza użycie typów danych niskiego poziomu.|
|[raw_property_prefixes](../preprocessor/raw-property-prefixes.md)|Określa alternatywne prefiksy dla trzech metod właściwości.|
|[ZmieńNazwę](../preprocessor/rename-hash-import.md)|Działa wokół problemów z kolizją nazw.|
|[rename_namespace](../preprocessor/rename-namespace.md)|Zmienia nazwę przestrzeni nazw, która zawiera zawartość biblioteki typów.|
|[rename_search_namespace](../preprocessor/rename-search-namespace.md)|Ma taką samą funkcjonalność jak atrybut [rename_namespace](../preprocessor/rename-namespace.md) , ale jest używany w bibliotekach typów, które używają dyrektywy #import z atrybutem [auto_search](../preprocessor/auto-search.md) .|
|[tlbid](../preprocessor/tlbid.md)|Umożliwia ładowanie bibliotek poza podstawową biblioteką typów.|

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)