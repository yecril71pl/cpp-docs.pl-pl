---
title: ModuleBase::DecrementObjectCount — metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::ModuleBase::DecrementObjectCount
dev_langs:
- C++
helpviewer_keywords:
- DecrementObjectCount method
ms.assetid: a016fb07-a36e-40cd-bc7b-8f6e85e256e7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: daf27930261c0350c1e48b851fe989decd52dde2
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33876296"
---
# <a name="modulebasedecrementobjectcount-method"></a>ModuleBase::DecrementObjectCount — Metoda
Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```  
virtual long DecrementObjectCount() = 0;  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Liczba przed wykonaniem operacji dekrementacji.  
  
## <a name="remarks"></a>Uwagi  
 Po zaimplementowaniu, zmniejsza liczbę obiektów śledzone przez moduł.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** implements.h  
  
 **Namespace:** Microsoft::wrl:: details —  
  
## <a name="see-also"></a>Zobacz też  
 [Modulebase — klasa](../windows/modulebase-class.md)   
 [Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)