---
title: MakeAllocator::Allocate — metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::MakeAllocator::Allocate
dev_langs:
- C++
helpviewer_keywords:
- Allocate method
ms.assetid: a01997bc-4ff1-4ed0-9def-e4aaa15b0598
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d0e8d387dea7687ad61d85f975d58aa47489266d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33876219"
---
# <a name="makeallocatorallocate-method"></a>MakeAllocator::Allocate — Metoda
Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```  
__forceinline void* Allocate();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 W przypadku powodzenia wskaźnik do alokacji pamięci; w przeciwnym razie `nullptr`.  
  
## <a name="remarks"></a>Uwagi  
 Przydziela pamięć i kojarzy ją z bieżącym obiektem makeallocator —.  
  
 Rozmiar alokacji pamięci jest rozmiar typu określonego przez parametr szablonu makeallocator — bieżący.  
  
 Deweloper musi zastąpić tylko metodę Allocate() do implementowania modelu alokacji pamięci różne.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** implements.h  
  
 **Namespace:** Microsoft::wrl:: details —  
  
## <a name="see-also"></a>Zobacz też  
 [Makeallocator — klasa](../windows/makeallocator-class.md)   
 [Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)