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
ms.openlocfilehash: 1c8221b405618b1879f4e4c865115a227eb09857
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33890120"
---
# <a name="weakrefoperatoramp-operator"></a>WeakRef::operator&amp; — Operator
Zwraca obiekt comptrref — reprezentujący bieżący obiekt weakref —.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
Details::ComPtrRef<WeakRef> operator&() throw()  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Obiekt comptrref — reprezentujący bieżący obiekt weakref —.  
  
## <a name="remarks"></a>Uwagi  
 Jest to wewnętrzny pomocnika operatora, który nie jest przeznaczona do użycia w kodzie.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** client.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [WeakRef, klasa](../windows/weakref-class.md)