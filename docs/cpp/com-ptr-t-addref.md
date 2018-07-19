---
title: _com_ptr_t::AddRef | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_ptr_t::AddRef
dev_langs:
- C++
helpviewer_keywords:
- AddRef method [C++], interface pointers
ms.assetid: c104dac3-aad3-40bb-a298-75c6cd0e63a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 40ed48b54a3862f7ac5804e7652d98b661bb071d
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37940995"
---
# <a name="comptrtaddref"></a>_com_ptr_t::AddRef
**Microsoft Specific**  
  
 Wywołania `AddRef` funkcji składowej typu `IUnknown` interfejsu zhermetyzowanego wskaźnika.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
void AddRef( );  
  
```  
  
## <a name="remarks"></a>Uwagi  
 Wywołania `IUnknown::AddRef` wskaźnika zhermetyzowany interfejs wywoływanie E_POINTER błąd, jeśli wskaźnik jest pusty.  
  
 **END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [_com_ptr_t, klasa](../cpp/com-ptr-t-class.md)