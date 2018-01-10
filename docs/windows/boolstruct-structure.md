---
title: "Boolstruct — struktura | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: internal/Microsoft::WRL::Details::BoolStruct
dev_langs: C++
helpviewer_keywords: BoolStruct structure
ms.assetid: 666eae78-e81d-4fb7-a9e4-1ba617d6d4cd
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7daa7527c8eea2cfca3b8933b9c3e1f042883e2d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="boolstruct-structure"></a>BoolStruct — Struktura
Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```  
struct BoolStruct;  
```  
  
## <a name="remarks"></a>Uwagi  
 Boolstruct — struktura definiuje, czy comptr — Zarządzanie okres istnienia obiektu interfejsu. Boolstruct — jest używana wewnętrznie przez [BoolType()](../windows/comptr-operator-microsoft-wrl-details-booltype-operator.md) operatora.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[BoolStruct::Member, składowa danych](../windows/boolstruct-member-data-member.md)|Określa, że [comptr —](../windows/comptr-class.md) jest lub nie jest okres istnienia obiektu interfejsu zarządzania.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `BoolStruct`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** internal.h  
  
 **Namespace:** Microsoft::wrl:: details —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::wrl:: details — Namespace](../windows/microsoft-wrl-details-namespace.md)   
 [Operator ComPtr::operator Microsoft::WRL::Details::BoolType](../windows/comptr-operator-microsoft-wrl-details-booltype-operator.md)