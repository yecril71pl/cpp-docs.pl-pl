---
title: "Implements::FillArrayWithIid — metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::Implements::FillArrayWithIid
dev_langs: C++
helpviewer_keywords: FillArrayWithIid method
ms.assetid: b2e62e3f-0ab9-4c70-aad7-856268544f44
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a53a7eb9a05e1f4583c49b42fa10efdf1ee815ab
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="implementsfillarraywithiid-method"></a>Implements::FillArrayWithIid — Metoda
Wstawia podany identyfikator interfejsu przez bieżący parametr szablonu zeroth w element określonej tablicy.  
  
## <a name="syntax"></a>Składnia  
  
```  
__forceinline static void FillArrayWithIid(  
   unsigned long &index,  
   _In_ IID* iids  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `index`  
 Liczony od zera indeks, który wskazuje element tablicy początkowy dla tej operacji. Po zakończeniu tej operacji, `index` jest zwiększana o 1.  
  
 `iids`  
 Tablica typu IID.  
  
## <a name="remarks"></a>Uwagi  
 Funkcja pomocnika wewnętrznego.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** implements.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [Implements — struktura](../windows/implements-structure.md)