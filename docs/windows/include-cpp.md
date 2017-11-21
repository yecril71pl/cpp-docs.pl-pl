---
title: "obejmują (C++) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.include
dev_langs: C++
helpviewer_keywords: include attribute
ms.assetid: d23f8b91-fe5b-48fa-9371-8bd73af7b8e3
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4091c8ae127077acbfe87d50a23a986d468d67ff
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="include-c"></a>include (C++)
Określa co najmniej jeden plik nagłówka do uwzględnienia w pliku .idl wygenerowany.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      [ include(  
   header_file  
) ];  
```  
  
#### <a name="parameters"></a>Parametry  
 *header_file*  
 Nazwa pliku, który ma zawarty w pliku .idl wygenerowany.  
  
## <a name="remarks"></a>Uwagi  
 **Obejmują** atrybut C++ powoduje `#include` instrukcji do umieszczenia poniżej `import "docobj.idl"` instrukcji w pliku .idl wygenerowany.  
  
 **Obejmują** atrybut C++ ma te same funkcje co [obejmują](http://msdn.microsoft.com/library/windows/desktop/aa367052) MIDL atrybutu.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia przykład sposobu użycia **obejmują**. Na przykład include.h plik zawiera tylko #include instrukcji.  
  
```  
// cpp_attr_ref_include.cpp  
// compile with: /LD  
[module(name="MyLib")];  
[include(cpp_attr_ref_include.h)];  
```  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Atrybut kontekstu  
  
|||  
|-|-|  
|**Dotyczy**|Dowolnego miejsca|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|Brak|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty IDL](../windows/idl-attributes.md)   
 [Oddzielne atrybuty](../windows/stand-alone-attributes.md)   
 [Import](../windows/import.md)   
 [importidl —](../windows/importidl.md)   
 [includelib —](../windows/includelib-cpp.md)   
 [importlib](../windows/importlib.md)   
