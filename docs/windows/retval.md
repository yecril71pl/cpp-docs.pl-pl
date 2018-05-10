---
title: retval | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.retval
dev_langs:
- C++
helpviewer_keywords:
- retval attribute
ms.assetid: bfa16f08-157d-4eea-afde-1232c54b8501
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1c0bf7ecd989b51a17c853c6d2986db204c3ce34
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
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
|**Wymaganych atrybutów**|**out**|  
|**Nieprawidłowe atrybuty**|**in**|  
  
 Aby uzyskać więcej informacji na temat konteksty atrybutu, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty IDL](../windows/idl-attributes.md)   
 [Atrybuty parametrów](../windows/parameter-attributes.md)   
 [Atrybuty metody](../windows/method-attributes.md)   
