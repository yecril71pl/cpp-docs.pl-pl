---
title: size_is | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.size_is
dev_langs: C++
helpviewer_keywords: size_is attribute
ms.assetid: 70192d09-f6c5-4d52-b3fe-303f8cb10aa5
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0e8b3f6e8df8ff7f493c50f52e1e839f4ca9baa9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="sizeis"></a>size_is
Określ rozmiar pamięci przydzielona dla wskaźników rozmiarze o rozmiarze wskaźniki do wskaźników o rozmiarze i jedno - lub tablice wielowymiarowe.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      [ size_is(  
   "expression"  
) ]  
```  
  
#### <a name="parameters"></a>Parametry  
 *wyrażenie*  
 Rozmiar pamięci przydzielonej dla wskaźników o określonym rozmiarze.  
  
## <a name="remarks"></a>Uwagi  
 **Size_is** atrybut C++ ma te same funkcje co [size_is](http://msdn.microsoft.com/library/windows/desktop/aa367164) MIDL atrybutu.  
  
## <a name="example"></a>Przykład  
 Zobacz przykład [first_is —](../windows/first-is.md) przykład sposobu określania sekcji tablicy.  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Atrybut kontekstu  
  
|||  
|-|-|  
|**Dotyczy**|Pole w `struct` lub **Unii**, interfejs parametru, interfejsu — metoda|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|Brak|  
|**Nieprawidłowe atrybuty**|**max_is —**|  
  
 Aby uzyskać więcej informacji na temat konteksty atrybutu, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty IDL](../windows/idl-attributes.md)   
 [Element TypeDef, Enum, Unii i struct — atrybuty](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Atrybuty parametrów](../windows/parameter-attributes.md)   
 [first_is —](../windows/first-is.md)   
 [last_is —](../windows/last-is.md)   
 [max_is —](../windows/max-is.md)   
 [length_is —](../windows/length-is.md)   
