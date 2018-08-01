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
ms.openlocfilehash: 4bf56e87b8b7949048b1e6006d3aa32f00af1462
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2018
ms.locfileid: "39404262"
---
# <a name="comptrtaddref"></a>_com_ptr_t::AddRef
**Microsoft Specific**  
  
 Wywołania `AddRef` funkcji składowej typu `IUnknown` interfejsu zhermetyzowanego wskaźnika.  
  
## <a name="syntax"></a>Składnia  
  
```  
void AddRef( );  
```  
  
## <a name="remarks"></a>Uwagi  
 Wywołania `IUnknown::AddRef` wskaźnika zhermetyzowany interfejs wywoływanie `E_POINTER` błędu, jeśli wskaźnik jest pusty.  
  
 **END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz także  
 [_com_ptr_t, klasa](../cpp/com-ptr-t-class.md)