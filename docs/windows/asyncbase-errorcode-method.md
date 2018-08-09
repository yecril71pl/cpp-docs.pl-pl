---
title: AsyncBase::ErrorCode, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::ErrorCode
dev_langs:
- C++
helpviewer_keywords:
- ErrorCode method
ms.assetid: 3f5f0f69-d60a-4a67-8cc6-a55fdc89a192
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a5f4ccbe1789914f5a7c378f5cb847aaa1c49bb8
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39644706"
---
# <a name="asyncbaseerrorcode-method"></a>AsyncBase::ErrorCode — Metoda
Pobiera kod błędu dla bieżącej operacji asynchronicznej.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
inline void ErrorCode(  
   HRESULT *error  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *Błąd*  
 Lokalizacja, w której przechowuje bieżący kod błędu w tej operacji.  
  
## <a name="remarks"></a>Uwagi  
 Ta operacja jest metodą o bezpiecznych wątkach.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** async.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Zobacz też  
 [AsyncBase, klasa](../windows/asyncbase-class.md)