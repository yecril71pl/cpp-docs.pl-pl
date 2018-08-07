---
title: Implements::FillArrayWithIid, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Implements::FillArrayWithIid
dev_langs:
- C++
helpviewer_keywords:
- FillArrayWithIid method
ms.assetid: b2e62e3f-0ab9-4c70-aad7-856268544f44
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6797c274402578cfecb522c86745fb5b257e213d
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2018
ms.locfileid: "39608861"
---
# <a name="implementsfillarraywithiid-method"></a>Implements::FillArrayWithIid — Metoda
Wstawia identyfikator interfejsu określonego przez bieżący parametr szablonu zerowego do elementu określonej tablicy.  
  
## <a name="syntax"></a>Składnia  
  
```  
__forceinline static void FillArrayWithIid(  
   unsigned long &index,  
   _In_ IID* iids  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *index*  
 Liczony od zera indeks, który wskazuje element początkowy tablicy do wykonania tej operacji. Po zakończeniu tej operacji, *indeksu* jest zwiększana o 1.  
  
 *IID*  
 Tablica typu IID.  
  
## <a name="remarks"></a>Uwagi  
 Funkcja pomocnika wewnętrznego.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** implements.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Zobacz też  
 [Implements, struktura](../windows/implements-structure.md)