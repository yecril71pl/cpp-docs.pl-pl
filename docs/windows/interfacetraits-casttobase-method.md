---
title: InterfaceTraits::CastToBase, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceTraits::CastToBase
dev_langs:
- C++
helpviewer_keywords:
- CastToBase method
ms.assetid: 0591a017-0adf-4358-b946-eb0a307ce7f2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4f284514472796f22d176325a0223848a827c85c
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2018
ms.locfileid: "39606452"
---
# <a name="interfacetraitscasttobase-method"></a>InterfaceTraits::CastToBase — Metoda
Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<typename T>  
static __forceinline Base* CastToBase(  
   _In_ T* ptr  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *T*  
 Typ parametru *ptr*.  
  
 *ptr*  
 Wskaźnik do typu *T*.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do `Base`.  
  
## <a name="remarks"></a>Uwagi  
 Rzutuje określony wskaźnik do wskaźnika do `Base`.  
  
 Aby uzyskać więcej informacji na temat `Base`, zobacz sekcję publiczne definicje typów w [interfacetraits — struktura](../windows/interfacetraits-structure.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** implements.h  
  
 **Namespace:** Microsoft::wrl:: details  
  
## <a name="see-also"></a>Zobacz też  
 [Interfacetraits — struktura](../windows/interfacetraits-structure.md)   
 [Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)