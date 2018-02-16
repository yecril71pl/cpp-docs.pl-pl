---
title: "domyślny obszar nazw | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 4712e9dc-57ba-43cc-811e-022e1dae4de8
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 96b4fc906048d8f8e02d5359526e095c0f12118d
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="default-namespace"></a>Domyślna przestrzeń nazw
`default` Przestrzeni nazw zakresów wbudowanych typów, które są obsługiwane przez C + +/ CX.  
  
## <a name="syntax"></a>Składnia  
  
```  
namespace default;  
```  
  
### <a name="members"></a>Elementy członkowskie  
 Wszystkie typy wbudowane dziedziczą następujące elementy członkowskie.  
  
|||  
|-|-|  
|[default::(type_name)::Equals](../cppcx/default-type-name-equals-method.md)|Określa, czy określony obiekt jest równy bieżącemu obiektowi.|  
|[default::(type_name)::GetHashCode](../cppcx/default-type-name-gethashcode-method.md)|Zwraca kod skrótu dla tego wystąpienia.|  
|[default::(type_name)::GetType](../cppcx/default-type-name-gettype-method.md)|Zwraca ciąg reprezentujący bieżący typ.|  
|[default::(type_name)::ToString](../cppcx/default-type-name-tostring-method.md)|Zwraca ciąg reprezentujący bieżący typ.|  
  
### <a name="built-in-types"></a>Typy wbudowane  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`char16`|16-bitową liczbą wartość odpowiadającą punkt kodu Unicode (UTF-16).|  
|`float32`|Liczba zmiennoprzecinkowa IEEE-754 32-bitowa.|  
|`float64`|Liczby zmiennoprzecinkowej IEEE-754 64-bitowe.|  
|`int16`|16-bitową liczbę całkowitą ze znakiem.|  
|`int32`|Całkowita 32-bitowych.|  
|`int64`|Całkowita 64-bitowych.|  
|`int8`|8-bitową podpisem wartość liczbowa.|  
|`uint16`|16-bitową liczbę całkowitą bez znaku.|  
|`uint32`|32-bitowa liczba całkowita bez znaku.|  
|`uint64`|64-bitowa liczba całkowita bez znaku.|  
|`uint8`|8-bitowych unsigned wartość liczbowa.|  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** vccorlib.h  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja języka Visual C++](../cppcx/visual-c-language-reference-c-cx.md)