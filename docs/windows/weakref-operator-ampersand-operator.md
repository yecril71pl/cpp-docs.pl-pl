---
title: WeakRef::operator&amp; Operator | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::WeakRef::operator&
dev_langs:
- C++
helpviewer_keywords:
- operator& operator
ms.assetid: 900afb73-3801-4d08-9b41-2e6a62011ccd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 125ffe998e7c3f225f72e3fb47df4ef3525c37f9
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39649051"
---
# <a name="weakrefoperatoramp-operator"></a>WeakRef::operator&amp; — Operator
Zwraca `ComPtrRef` obiekt, który reprezentuje bieżący **WeakRef** obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
Details::ComPtrRef<WeakRef> operator&() throw()  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 A `ComPtrRef` obiekt, który reprezentuje bieżący **WeakRef** obiektu.  
  
## <a name="remarks"></a>Uwagi  
 Jest to wewnętrzny pomocnika operatora, który nie jest przeznaczona do użycia w kodzie.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** client.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Zobacz też  
 [WeakRef, klasa](../windows/weakref-class.md)