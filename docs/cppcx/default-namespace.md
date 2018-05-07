---
title: domyślny obszar nazw | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 4712e9dc-57ba-43cc-811e-022e1dae4de8
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3f4386d3636744a673a10dd9530fd3836fdb78e6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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