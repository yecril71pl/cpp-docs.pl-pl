---
title: ChainInterfaces::CastToUnknown, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::ChainInterfaces::CastToUnknown
dev_langs:
- C++
helpviewer_keywords:
- CastToUnknown method
ms.assetid: a6a58555-e5b0-4773-aba0-959d9d362c6b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 45cc86c873e7c45a7352f0035b2fd16e312e7c6c
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39644449"
---
# <a name="chaininterfacescasttounknown-method"></a>ChainInterfaces::CastToUnknown — Metoda
Rzutuje wskaźnika interfejsu typu zdefiniowanego przez *I0* parametr szablonu na wskaźnik do `IUnknown`.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
__forceinline IUnknown* CastToUnknown();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do `IUnknown`.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** implements.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Zobacz też  
 [ChainInterfaces, struktura](../windows/chaininterfaces-structure.md)