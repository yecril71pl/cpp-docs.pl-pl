---
title: usesgetlasterror — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.usesgetlasterror
dev_langs:
- C++
helpviewer_keywords:
- usesgetlasterror attribute
ms.assetid: d149e33d-35a7-46cb-9137-ae6883d86122
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 399b9fbbcf4b449f5f91beaea89c403d120d0a21
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33890278"
---
# <a name="usesgetlasterror"></a>usesgetlasterror
Obiekt wywołujący informuje, że jeśli występuje błąd podczas wywoływania tej funkcji, następnie obiekt wywołujący może wywoływać `GetLastError` można pobrać kod błędu.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
[usesgetlasterror]  
  
```  
  
## <a name="remarks"></a>Uwagi  
 **Usesgetlasterror —** atrybut C++ ma te same funkcje co [usesgetlasterror —](http://msdn.microsoft.com/library/windows/desktop/aa367297) MIDL atrybutu.  
  
## <a name="example"></a>Przykład  
 Zobacz [idl_module](../windows/idl-module.md) przykład przykładowy sposób użycia **usesgetlasterror —**.  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Atrybut kontekstu  
  
|||  
|-|-|  
|**Dotyczy**|**Moduł** atrybutu|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|Brak|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji na temat konteksty atrybutu, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty IDL](../windows/idl-attributes.md)   
