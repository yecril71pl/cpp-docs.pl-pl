---
title: _com_ptr_t::wydanie | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _com_ptr_t.Release
- _com_ptr_t::Release
dev_langs: C++
helpviewer_keywords: Release method [C++]
ms.assetid: db448b34-0efa-4f02-b701-ad1ca3ae6ca5
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 207569a2ad719e907fc46ba2abdd80a0c2e6239e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="comptrtrelease"></a>_com_ptr_t::Release
**Dotyczące firmy Microsoft**  
  
 Wywołania **wersji** funkcji członkowskiej klasy **IUnknown** na wskaźnik hermetyzowany interfejsu.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
void Release( );  
  
```  
  
## <a name="remarks"></a>Uwagi  
 Wywołania `IUnknown::Release` na wskaźniku zhermetyzowany interfejs wywoływanie `E_POINTER` błędu, jeśli jest to wskaźnik interfejsu **NULL**.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [_com_ptr_t — klasa](../cpp/com-ptr-t-class.md)