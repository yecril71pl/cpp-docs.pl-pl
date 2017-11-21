---
title: "cpp_quote — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.cpp_quote
dev_langs: C++
helpviewer_keywords: cpp_quote attribute
ms.assetid: f75327ff-42bd-498b-9177-7ffa25427e1f
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: cc91c884bb58ce21e4419a8082f15792a0fc2246
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cppquote"></a>cpp_quote
Emituje określony ciąg bez znaków cudzysłowu do pliku .idl wygenerowany.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      [ cpp_quote(  
   "statement"  
) ];  
```  
  
#### <a name="parameters"></a>Parametry  
 *— Instrukcja*  
 Instrukcja C.  
  
## <a name="remarks"></a>Uwagi  
 **Cpp_quote —** atrybut C++ jest przydatne, jeśli chcesz umieścić dyrektywy preprocesora w pliku .idl.  
  
 Można również użyć **cpp_quote —** i Wygeneruj plik .h jako część kompilacji MIDL. Na przykład jeśli masz pliku nagłówka C++ używającego atrybuty C++ IDL, ale nie można użyć tego pliku dla niektórych zadań, następnie będzie można kompilować go w celu utworzenia pliku .h generowanych przez MIDL, powinno być możliwe do użycia.  
  
 **Cpp_quote —** atrybut ma te same funkcje co [cpp_quote —](http://msdn.microsoft.com/library/windows/desktop/aa366765) MIDL atrybutu.  
  
## <a name="example"></a>Przykład  
 Zobacz przykład [podwójną](../windows/dual.md) na przykład użyć sposób użycia **cpp_quote —**.  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Atrybut kontekstu  
  
|||  
|-|-|  
|**Dotyczy**|Dowolnego miejsca|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|Brak|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji na temat konteksty atrybutu, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty IDL](../windows/idl-attributes.md)   
 [Oddzielne atrybuty](../windows/stand-alone-attributes.md)   
