---
title: HandleT::Close, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleT::Close
dev_langs:
- C++
helpviewer_keywords:
- Close method
ms.assetid: 1b9d597c-abcf-4028-a068-0344560009f6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 69f3f2c756d158954676f6fc42941b1b80f4345e
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/06/2018
ms.locfileid: "39569921"
---
# <a name="handletclose-method"></a>HandleT::Close — Metoda
Zamyka bieżące **HandleT** obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
void Close();  
```  
  
## <a name="remarks"></a>Uwagi  
 Dojście, która jest podporządkowana narzędziu bieżącego **HandleT** jest zamknięte i **HandleT** ustawiono nieprawidłowy stan.  
  
 Jeśli uchwyt nie zamyka się prawidłowo, tworzony jest wyjątek w wątku wywołującego.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::wrl:: wrappers  
  
## <a name="see-also"></a>Zobacz też  
 [HandleT, klasa](../windows/handlet-class.md)