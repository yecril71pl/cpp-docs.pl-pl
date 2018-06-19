---
title: no_smart_pointers — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- no_search_pointers
dev_langs:
- C++
helpviewer_keywords:
- no_smart_pointers attribute
ms.assetid: d69dd71e-08a8-4446-a3d0-a062dc29cb17
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8e4503ab027589f54c5b5bce60dc405a570dcc59
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33849694"
---
# <a name="nosmartpointers"></a>no_smart_pointers
**Określonego języka C++**  
  
 Pomija tworzenie wskaźników inteligentne dla wszystkich interfejsów w bibliotece typów.  
  
## <a name="syntax"></a>Składnia  
  
```  
no_smart_pointers  
```  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie, gdy używasz `#import`, możesz uzyskać deklaracji wskaźnika inteligentnego dla wszystkich interfejsów w bibliotece typów. Te wskaźniki inteligentne są typu [_com_ptr_t — klasa](../cpp/com-ptr-t-class.md).  
  
 **KOŃCOWY określonego języka C++**  
  
## <a name="see-also"></a>Zobacz też  
 [atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)   
 [#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)