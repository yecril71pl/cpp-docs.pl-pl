---
title: HANDLETraits::Close, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits::Close
dev_langs:
- C++
helpviewer_keywords:
- Close method
ms.assetid: 3c631a7c-ccce-472a-b1da-aab8fa815c13
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 561862427238a86dbb23ee05044c1d01558abab5
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39647602"
---
# <a name="handletraitsclose-method"></a>HANDLETraits::Close — Metoda
Zamyka określone dojście.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
inline static bool Close(  
   _In_ Type h  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *h*  
 Dojście do zamknięcia.  
  
## <a name="return-value"></a>Wartość zwracana  
 **wartość true,** Jeśli obsługi *h* zamknięta pomyślnie; w przeciwnym razie **false**.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::HandleTraits  
  
## <a name="see-also"></a>Zobacz też  
 [HANDLETraits, struktura](../windows/handletraits-structure.md)