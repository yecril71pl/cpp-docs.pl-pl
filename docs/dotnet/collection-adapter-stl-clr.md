---
title: collection_adapter — (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::collection_adapter
dev_langs:
- C++
helpviewer_keywords:
- collection_adapter class [STL/CLR]
ms.assetid: 31964058-1f50-48bf-82c2-b0b3cc8a7887
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 62fb5dc48175d755771960e9121c3371a0292595
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="collectionadapter-stlclr"></a>collection_adapter (STL/CLR)
Opakowuje kolekcji .NET do użycia jako kontenera STL/CLR. A `collection_adapter` to klasa szablonu, który opisuje prostego obiektu kontenera STL/CLR. Opakowuje interfejsu biblioteki klasy podstawowej (BCL) i zwraca pary iteratora używanej do manipulowania kontrolowanej sekwencji.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<typename Coll>  
    ref class collection_adapter;  
  
template<>  
    ref class collection_adapter<  
        System::Collections::ICollection>;  
template<>  
    ref class collection_adapter<  
        System::Collections::IEnumerable>;  
template<>  
    ref class collection_adapter<  
        System::Collections::IList>;  
template<>  
    ref class collection_adapter<  
        System::Collections::IDictionary>;  
template<typename Value>  
    ref class collection_adapter<  
        System::Collections::Generic::ICollection<Value>>;  
template<typename Value>  
    ref class collection_adapter<  
        System::Collections::Generic::IEnumerable<Value>>;  
template<typename Value>  
    ref class collection_adapter<  
        System::Collections::Generic::IList<Value>>;  
template<typename Key,  
    typename Value>  
    ref class collection_adapter<  
        System::Collections::Generic::IDictionary<Key, Value>>;  
```  
  
#### <a name="parameters"></a>Parametry  
 Coll  
 Typ kolekcji opakowana.  
  
## <a name="specializations"></a>Specjalizacje  
  
|Specjalizacji|Opis|  
|--------------------|-----------------|  
|Interfejs IEnumerable|Sekwencje przez elementy.|  
|Interfejs ICollection|Przechowuje grupę elementów.|  
|IList|Obsługuje uporządkowane grupy elementów.|  
|Element IDictionary|Obsługa zestaw {klucza, wartość} pary.|  
|Interfejs IEnumerable\<wartość >|Sekwencje za pośrednictwem typu elementów.|  
|Interfejs ICollection\<wartość >|Przechowuje grupę elementów typu.|  
|IList\<wartość >|Obsługuje uporządkowane grupy elementów typu.|  
|IDictionary\<wartość >|Funkcja obsługuje zestaw typu {klucza, wartość} pary.|  
  
## <a name="members"></a>Elementy członkowskie  
  
|Definicja typu|Opis|  
|---------------------|-----------------|  
|[collection_adapter::difference_type (STL/CLR)](../dotnet/collection-adapter-difference-type-stl-clr.md)|Typ odległości ze znakiem między dwoma elementami.|  
|[collection_adapter::iterator (STL/CLR)](../dotnet/collection-adapter-iterator-stl-clr.md)|Typ iteratora dla kontrolowanej sekwencji.|  
|[collection_adapter::key_type (STL/CLR)](../dotnet/collection-adapter-key-type-stl-clr.md)|Typ klucza słownika.|  
|[collection_adapter::mapped_type (STL/CLR)](../dotnet/collection-adapter-mapped-type-stl-clr.md)|Typ wartości słownika.|  
|[collection_adapter::reference (STL/CLR)](../dotnet/collection-adapter-reference-stl-clr.md)|Typ odwołania do elementu.|  
|[collection_adapter::size_type (STL/CLR)](../dotnet/collection-adapter-size-type-stl-clr.md)|Typ odległości ze znakiem między dwoma elementami.|  
|[collection_adapter::value_type (STL/CLR)](../dotnet/collection-adapter-value-type-stl-clr.md)|Typ elementu.|  
  
|Funkcja elementów członkowskich|Opis|  
|---------------------|-----------------|  
|[collection_adapter::base (STL/CLR)](../dotnet/collection-adapter-base-stl-clr.md)|Określa interfejs BCL opakowana.|  
|[collection_adapter::begin (STL/CLR)](../dotnet/collection-adapter-begin-stl-clr.md)|Określa początek kontrolowanej sekwencji.|  
|[collection_adapter::collection_adapter (STL/CLR)](../dotnet/collection-adapter-collection-adapter-stl-clr.md)|Tworzy obiekt karty.|  
|[collection_adapter::end (STL/CLR)](../dotnet/collection-adapter-end-stl-clr.md)|Określa koniec kontrolowanej sekwencji.|  
|[collection_adapter::size (STL/CLR)](../dotnet/collection-adapter-size-stl-clr.md)|Liczy liczbę elementów.|  
|[collection_adapter::swap (STL/CLR)](../dotnet/collection-adapter-swap-stl-clr.md)|Zamienia zawartości dwóch kontenerów.|  
  
|Operator|Opis|  
|--------------|-----------------|  
|[collection_adapter::operator= (STL/CLR)](../dotnet/collection-adapter-operator-assign-stl-clr.md)|Zastępuje przechowywanych dojście BCL.|  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa szablon służy do manipulowania kontener BCL jako kontenera STL/CLR. `collection_adapter` Przechowuje dojście do interfejsu BCL, który z kolei kontroluje sekwencję elementów. A `collection_adapter` obiektu `X` zwraca parę wejściowych Iteratory `X.begin()` i `X.end()` umożliwia odwiedź elementów, w kolejności. Niektóre specjalizacji pozwalają również zapisu `X.size()` do określania długości kontrolowanej sekwencji.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/karty >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [range_adapter — (STL/CLR)](../dotnet/range-adapter-stl-clr.md)   
 [make_collection (STL/CLR)](../dotnet/make-collection-stl-clr.md)