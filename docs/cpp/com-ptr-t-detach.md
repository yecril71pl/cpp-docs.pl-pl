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
ms.openlocfilehash: cf38e433f7042707b502a4cba2088db9412adb29
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2018
ms.locfileid: "39405837"
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
  
## <a name="see-also"></a>Zobacz także  
 [_com_ptr_t, klasa](../cpp/com-ptr-t-class.md)