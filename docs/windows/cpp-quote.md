---
title: cpp_quote — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.cpp_quote
dev_langs:
- C++
helpviewer_keywords:
- cpp_quote attribute
ms.assetid: f75327ff-42bd-498b-9177-7ffa25427e1f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3dc81eacdbadb971ab86f4cfde1353e89bbe1342
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/02/2018
ms.locfileid: "39463830"
---
# <a name="cppquote"></a>cpp_quote
Generuje określony ciąg bez znaków cudzysłowu do pliku .idl wygenerowany.  
  
## <a name="syntax"></a>Składnia  
  
```  
[ cpp_quote(  
   "statement"  
) ];  
```  
  
#### <a name="parameters"></a>Parametry  
 *Instrukcja*  
 Instrukcja języka C.  
  
## <a name="remarks"></a>Uwagi  
 **Cpp_quote —** C++ atrybut jest przydatna, jeśli chcesz umieścić dyrektywy preprocesora w pliku .idl.  
  
 Można również użyć **cpp_quote —** i Wygeneruj plik .h jako część kompilacji MIDL. Na przykład jeśli masz plik nagłówka C++, który używa atrybuty C++ IDL, ale nie można użyć tego pliku dla niektórych zadań, następnie będzie można kompilować go, aby utworzyć plik MIDL generowane .h, powinno być możliwe do użycia.  
  
 **Cpp_quote —** atrybut ma taką samą funkcjonalność jak [cpp_quote —](http://msdn.microsoft.com/library/windows/desktop/aa366765) atrybutów w MIDL.  
  
## <a name="example"></a>Przykład  
 Zobacz przykład [podwójną](../windows/dual.md) na przykład użyć sposób używania **cpp_quote —**.  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Kontekst atrybutu  
  
|||  
|-|-|  
|**Dotyczy**|Dowolne miejsce|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|Brak|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty IDL](../windows/idl-attributes.md)   
 [Oddzielne atrybuty](../windows/stand-alone-attributes.md)   