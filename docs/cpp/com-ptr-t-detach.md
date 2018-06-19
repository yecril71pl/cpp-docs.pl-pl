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
ms.openlocfilehash: 6fbe8fd203c3fda75e83aee623254676dacaf1da
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32410583"
---
# <a name="comptrtdetach"></a>_com_ptr_t::Detach
**Microsoft Specific**  
  
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