---
title: RoInitializeWrapper::RoInitializeWrapper, Konstruktor | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::RoInitializeWrapper::RoInitializeWrapper
dev_langs:
- C++
ms.assetid: c6f7fb07-14af-4574-9135-cea164607f30
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 193f0d16b03991e24cb16a90b3310512f6e86054
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2018
ms.locfileid: "39604401"
---
# <a name="roinitializewrapperroinitializewrapper-constructor"></a>RoInitializeWrapper::RoInitializeWrapper — Konstruktor
Inicjuje nowe wystąpienie klasy **RoInitializeWrapper** klasy.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
RoInitializeWrapper(   RO_INIT_TYPE flags)  
```  
  
### <a name="parameters"></a>Parametry  
 *flagi*  
 Jedno z wyliczeń RO_INIT_TYPE, które określa pomoc techniczną świadczoną przez środowisko wykonawcze Windows.  
  
## <a name="remarks"></a>Uwagi  
 **RoInitializeWrapper** wywołuje klasę `Windows::Foundation::Initialize(flags)`.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::wrl:: wrappers  
  
## <a name="see-also"></a>Zobacz też  
 [HandleT, klasa](../windows/handlet-class.md)