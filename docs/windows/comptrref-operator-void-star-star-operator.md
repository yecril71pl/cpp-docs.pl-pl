---
title: ComPtrRef::operator void ** Operator | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRef::operator void**
dev_langs:
- C++
helpviewer_keywords:
- operator void** operator
ms.assetid: f020045c-9de4-4392-8783-73f0fc0761c6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 16fa7964af8f56ec54f6870b8866e69266bdc414
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39648792"
---
# <a name="comptrrefoperator-void-operator"></a>ComPtrRef::operator void\* \* — Operator
Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
operator void**() const;  
```  
  
## <a name="remarks"></a>Uwagi  
 Usuwa bieżący **comptrref —** obiektów, wskaźnik do interfejsu, który został przedstawiony przez rzutuje **comptrref —** obiektu jako wskaźnik do wskaźnik do **void**, a następnie Zwraca wskaźnik rzutowania.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** client.h  
  
 **Namespace:** Microsoft::wrl:: details  
  
## <a name="see-also"></a>Zobacz też  
 [Comptrref — klasa](../windows/comptrref-class.md)   
 [Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)