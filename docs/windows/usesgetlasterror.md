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
ms.openlocfilehash: 011cf954a0b111e46afcaf6e55a54914075864db
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2018
ms.locfileid: "40014565"
---
# <a name="usesgetlasterror"></a>usesgetlasterror
Informuje obiekt wywołujący, że jeśli występuje błąd podczas wywoływania tej funkcji, następnie element wywołujący może wywoływać `GetLastError` można pobrać kod błędu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
[usesgetlasterror]  
```  
  
## <a name="remarks"></a>Uwagi  
 **Usesgetlasterror —** atrybut C++ ma taką samą funkcjonalność jak [usesgetlasterror —](http://msdn.microsoft.com/library/windows/desktop/aa367297) atrybutów w MIDL.  
  
## <a name="example"></a>Przykład  
 Zobacz [idl_module](../windows/idl-module.md) przykład przykład sposobu użycia **usesgetlasterror —**.  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Kontekst atrybutu  
  
|||  
|-|-|  
|**Dotyczy**|**Moduł** atrybutu|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|Brak|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty IDL](../windows/idl-attributes.md)   