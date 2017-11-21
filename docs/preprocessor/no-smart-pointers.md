---
title: "no_smart_pointers — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: no_search_pointers
dev_langs: C++
helpviewer_keywords: no_smart_pointers attribute
ms.assetid: d69dd71e-08a8-4446-a3d0-a062dc29cb17
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0837a702eb54ac19ba1a034d4c899284aba6cb37
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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