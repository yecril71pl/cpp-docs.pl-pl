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
ms.workload: cplusplus
ms.openlocfilehash: 3d92c6940c4eabc83143ce1054604ae4648347d4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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