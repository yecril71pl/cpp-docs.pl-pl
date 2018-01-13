---
title: '_com_ptr_t:: oddziel | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: _com_ptr_t::Detach
dev_langs: C++
helpviewer_keywords: Detach method [C++]
ms.assetid: 0652053e-af37-44e9-a278-2522212ebfed
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c04007df7d40e12f3f416b2f2cd437bdaf1314f4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="comptrtdetach"></a>_com_ptr_t::Detach
**Dotyczące firmy Microsoft**  
  
 Wyodrębnia i zwraca wskaźnik hermetyzowany interfejsu.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
Interface* Detach( ) throw( );  
  
```  
  
## <a name="remarks"></a>Uwagi  
 Wyodrębnia i zwraca wskaźnik interfejsu hermetyzowany, a następnie czyści magazynu hermetyzowany wskaźnika **NULL**. Spowoduje to usunięcie wskaźnika interfejsu z hermetyzacji. Aby wywołać jest **wersji** na wskaźnik interfejsu zwrócony.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [_com_ptr_t, klasa](../cpp/com-ptr-t-class.md)