---
title: size_is | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.size_is
dev_langs:
- C++
helpviewer_keywords:
- size_is attribute
ms.assetid: 70192d09-f6c5-4d52-b3fe-303f8cb10aa5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8dbb3bfbf61c4ad7303c6cee272e14fc91bc9656
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2018
ms.locfileid: "40011858"
---
# <a name="sizeis"></a>size_is
Określ rozmiar pamięci przydzielonej dla wskaźników o rozmiarze rozmiar wskaźniki do wskaźników o rozmiarze i jedno - lub tablic wielowymiarowych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
[ size_is(  
   "expression"  
) ]  
```  
  
### <a name="parameters"></a>Parametry  
 *Wyrażenie*  
 Rozmiar pamięci przydzielonej dla wskaźników o rozmiarze.  
  
## <a name="remarks"></a>Uwagi  
 **Size_is** atrybut C++ ma taką samą funkcjonalność jak [size_is](http://msdn.microsoft.com/library/windows/desktop/aa367164) atrybutów w MIDL.  
  
## <a name="example"></a>Przykład  
 Zobacz przykład [first_is —](../windows/first-is.md) przykład sposobu określania część tablicy.  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Kontekst atrybutu  
  
|||  
|-|-|  
|**Dotyczy**|Pole **struktury** lub **Unii**, interfejs parametrów, metody interfejsu|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|Brak|  
|**Nieprawidłowe atrybuty**|`max_is`|  
  
 Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty IDL](../windows/idl-attributes.md)   
 [Element TypeDef, Enum, Union i struct — atrybuty](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Atrybuty parametru](../windows/parameter-attributes.md)   
 [first_is —](../windows/first-is.md)   
 [last_is —](../windows/last-is.md)   
 [max_is —](../windows/max-is.md)   
 [length_is](../windows/length-is.md)   