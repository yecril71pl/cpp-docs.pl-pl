---
title: HandleT::Close — metoda | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 4f0c1e47420106651cfe0526d6d212e9819a72ff
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="handletclose-method"></a>HandleT::Close — Metoda
Zamyka bieżący obiekt handlet —.  
  
## <a name="syntax"></a>Składnia  
  
```  
void Close();  
```  
  
## <a name="remarks"></a>Uwagi  
 Dojście źródłową bieżącego handlet — jest zamknięty, a handlet — ustawiono nieprawidłowy stan.  
  
 Jeśli dojście nie zamknięty poprawnie, jest wyjątek w wątku wywołującym.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::wrl:: wrappers —  
  
## <a name="see-also"></a>Zobacz też  
 [HandleT, klasa](../windows/handlet-class.md)