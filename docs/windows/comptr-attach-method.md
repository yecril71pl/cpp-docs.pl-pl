---
title: ComPtr::Attach, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::Attach
dev_langs:
- C++
helpviewer_keywords:
- Attach method
ms.assetid: 5b911f2d-9830-4dc7-b9e3-527abd55d2c8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 78b5039268bd122ade815ed6040a1df546e0f293
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39641333"
---
# <a name="comptrattach-method"></a>ComPtr::Attach — Metoda
To skojarzenie **ComPtr** z typu interfejsu, określonego przez bieżący parametrowi typu szablonu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
void Attach(  
   _In_opt_ InterfaceType* other  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *other*  
 Typ interfejsu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** client.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Zobacz też  
 [ComPtr, klasa](../windows/comptr-class.md)