---
title: "MakeAllocator::Allocate — metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::Details::MakeAllocator::Allocate
dev_langs: C++
helpviewer_keywords: Allocate method
ms.assetid: a01997bc-4ff1-4ed0-9def-e4aaa15b0598
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 997386e42851c6d4e15aceac006b4e27eea35c44
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
 [Microsoft::wrl:: details — Namespace](../windows/microsoft-wrl-details-namespace.md)