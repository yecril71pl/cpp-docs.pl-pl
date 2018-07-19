---
title: '_com_ptr_t:: oddziel | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_ptr_t::Detach
dev_langs:
- C++
helpviewer_keywords:
- Detach method [C++]
ms.assetid: 0652053e-af37-44e9-a278-2522212ebfed
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c07a9ce1d315c6738472850b987ccb397feda267
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37941356"
---
# <a name="comptrtdetach"></a>_com_ptr_t::Detach
**Microsoft Specific**  
  
 Wyodrębnia i zwraca wskaźnik zhermetyzowany interfejs.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
Interface* Detach( ) throw( );  
  
```  
  
## <a name="remarks"></a>Uwagi  
 Wyodrębnia i zwraca wskaźnik zhermetyzowany interfejs, a następnie czyści magazyn zhermetyzowanego wskaźnika o wartości NULL. Spowoduje to usunięcie wskaźnika interfejsu z hermetyzacji. Aby wywołać to `Release` na wskaźnik interfejsu zwrócone.  
  
 **END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [_com_ptr_t, klasa](../cpp/com-ptr-t-class.md)