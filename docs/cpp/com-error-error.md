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
ms.openlocfilehash: 21f2da8c10b9b796740144f81d0390f1af124cab
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37942058"
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
  
## <a name="see-also"></a>Zobacz też  
 [_com_error, klasa](../cpp/com-error-class.md)