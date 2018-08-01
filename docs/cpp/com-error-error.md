---
title: _com_error::błąd | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::Error
- Error
dev_langs:
- C++
helpviewer_keywords:
- Error method [C++]
ms.assetid: b53a15fd-198e-4276-afcd-13439c4807f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6a7ddaefcf3bd46bf40b03c03d2d1fb00cf8fbbb
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2018
ms.locfileid: "39408430"
---
# <a name="comerrorerror"></a>_com_error::Error
**Microsoft Specific**  
  
 Pobiera wartość HRESULT przekazany do konstruktora.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Error( ) const throw( );  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Nieprzetworzone elementu HRESULT przekazany do konstruktora.  
  
## <a name="remarks"></a>Uwagi  
 Pobiera element HRESULT hermetyzowany w `_com_error` obiektu.  
  
 **END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz także  
 [_com_error, klasa](../cpp/com-error-class.md)