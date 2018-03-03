---
title: "range_adapter — (STL/CLR) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::range_adapter
dev_langs:
- C++
helpviewer_keywords:
- range_adapter class [STL/CLR]
ms.assetid: 3fbe2a65-1216-46a0-a182-422816b80cfb
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: b9adb22c14fb5b59dfb4e89e69c724ca8c7462bf
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="rangeadapter-stlclr"></a>range_adapter (STL/CLR)
Klasa szablonu, która opakowuje parę Iteratory, które są używane do implementowania kilka interfejsów biblioteki klasy podstawowej (BCL). Range_adapter — służy do manipulowania zakres STL/CLR, tak jakby był on kolekcji BCL.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<typename Iter>  
    ref class range_adapter  
        :   public  
        System::Collections::IEnumerable,  
        System::Collections::ICollection,  
        System::Collections::Generic::IEnumerable<Value>,  
        System::Collections::Generic::ICollection<Value>  
    { ..... };  
```  
  
#### <a name="parameters"></a>Parametry  
 ITER  
 Typ skojarzony z Iteratory opakowana.  
  
## <a name="members"></a>Elementy członkowskie  
  
|Funkcja elementów członkowskich|Opis|  
|---------------------|-----------------|  
|[range_adapter::range_adapter (STL/CLR)](../dotnet/range-adapter-range-adapter-stl-clr.md)|Tworzy obiekt karty.|  
  
|Operator|Opis|  
|--------------|-----------------|  
|[range_adapter::operator= (STL/CLR)](../dotnet/range-adapter-operator-assign-stl-clr.md)|Zastępuje pary iteratora przechowywane.|  
  
## <a name="interfaces"></a>Interfejsy  
  
|Interface|Opis|  
|---------------|-----------------|  
|<xref:System.Collections.IEnumerable>|Wykonuje iterację elementów w kolekcji.|  
|<xref:System.Collections.ICollection>|Przechowuje grupę elementów.|  
|<xref:System.Collections.Generic.IEnumerable%601>|Wykonuje iterację typu elementów w kolekcji.|  
|<xref:System.Collections.Generic.ICollection%601>|Przechowuje grupę elementów typu.|  
  
## <a name="remarks"></a>Uwagi  
 Range_adapter — przechowuje parę Iteratory, która z kolei określa sekwencję elementów. Obiekt implementuje cztery interfejsów BCL, które pozwalają iterowania po elementach, w kolejności. Ta klasa szablon służy do modyfikowania zakresów STL/CLR, podobnie jak kontenery BCL.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/karty >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [collection_adapter — (STL/CLR)](../dotnet/collection-adapter-stl-clr.md)   
 [make_collection (STL/CLR)](../dotnet/make-collection-stl-clr.md)