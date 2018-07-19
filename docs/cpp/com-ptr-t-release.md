---
title: _com_ptr_t::wydanie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_ptr_t.Release
- _com_ptr_t::Release
dev_langs:
- C++
helpviewer_keywords:
- Release method [C++]
ms.assetid: db448b34-0efa-4f02-b701-ad1ca3ae6ca5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7a8a734eae486ca5e88009301b13d71b21473d9f
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37939259"
---
# <a name="comptrtrelease"></a>_com_ptr_t::Release
**Microsoft Specific**  
  
 Wywołania `Release` funkcji składowej typu `IUnknown` interfejsu zhermetyzowanego wskaźnika.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
void Release( );  
  
```  
  
## <a name="remarks"></a>Uwagi  
 Wywołania `IUnknown::Release` wskaźnika zhermetyzowany interfejs wywoływanie E_POINTER błąd, jeśli ten wskaźnik interfejsu ma wartość NULL.  
  
 **END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [_com_ptr_t, klasa](../cpp/com-ptr-t-class.md)