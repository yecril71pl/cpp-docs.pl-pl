---
title: "raw_dispinterfaces — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: raw_dispinterfaces
dev_langs: C++
helpviewer_keywords: raw_dispinterfaces attribute
ms.assetid: f762864d-29bf-445b-825a-ba7b29a95409
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c73a30779bf85e39ca97d0e6f4979c070de4e00c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="rawdispinterfaces"></a>raw_dispinterfaces
**Określonego języka C++**  
  
 Informuje kompilator, aby wygenerować otoki niskiego poziomu funkcji dispinterface metody i właściwości, które wywołują **IDispatch::Invoke** i zwracać `HRESULT` kod błędu.  
  
## <a name="syntax"></a>Składnia  
  
```  
raw_dispinterfaces  
```  
  
## <a name="remarks"></a>Uwagi  
 Jeśli ten atrybut nie jest określona, tylko wysokiego poziomu otoki są generowane, które zgłaszają wyjątki C++ w razie awarii.  
  
 **KOŃCOWY określonego języka C++**  
  
## <a name="see-also"></a>Zobacz też  
 [atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)   
 [#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)