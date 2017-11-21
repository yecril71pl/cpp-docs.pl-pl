---
title: "_com_error::błąd | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _com_error::Error
- Error
dev_langs: C++
helpviewer_keywords: Error method [C++]
ms.assetid: b53a15fd-198e-4276-afcd-13439c4807f7
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 010d1b2e10d1435855c35929516ff0e7f3fd8d4e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="comerrorerror"></a>_com_error::Error
**Dotyczące firmy Microsoft**  
  
 Pobiera `HRESULT` przekazany do konstruktora.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
HRESULT Error( ) const throw( );  
  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Nieprzetworzona `HRESULT` element przekazany do konstruktora.  
  
## <a name="remarks"></a>Uwagi  
 Pobiera hermetyzowany `HRESULT` elementu `_com_error` obiektu.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [_com_error — klasa](../cpp/com-error-class.md)