---
title: retval | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.retval
dev_langs: C++
helpviewer_keywords: retval attribute
ms.assetid: bfa16f08-157d-4eea-afde-1232c54b8501
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f4e6a49f62b38c83b3cda8b92812aebcc10997bc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="retval"></a>retval
Określa parametr, który otrzymuje wartość zwrotną z elementu członkowskiego.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
[retval]  
  
```  
  
## <a name="remarks"></a>Uwagi  
 **Retval** atrybut C++ ma te same funkcje co [retval](http://msdn.microsoft.com/library/windows/desktop/aa367158) MIDL atrybutu.  
  
 **retval** musi występować w deklaracji funkcji ostatni argument.  
  
## <a name="example"></a>Przykład  
 Zobacz przykład [powiązania](../windows/bindable.md) użytku próbki **retval**.  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Atrybut kontekstu  
  
|||  
|-|-|  
|**Dotyczy**|Interfejs parametru metody interfejsu|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|**limit**|  
|**Nieprawidłowe atrybuty**|**w**|  
  
 Aby uzyskać więcej informacji na temat konteksty atrybutu, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty IDL](../windows/idl-attributes.md)   
 [Atrybuty parametrów](../windows/parameter-attributes.md)   
 [Atrybuty — metoda](../windows/method-attributes.md)   
