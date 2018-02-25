---
title: "rename_namespace — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- rename_namespace
dev_langs:
- C++
helpviewer_keywords:
- rename_namespace attribute
ms.assetid: 45006d2b-36cd-4bec-98b9-3b8ec45299e3
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 37b2c01479cb489f7ed573f55a48f5807161bf63
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="renamenamespace"></a>rename_namespace
**Określonego języka C++**  
  
 Zmienia nazwę przestrzeni nazw, która zawiera zawartość biblioteki typów.  
  
## <a name="syntax"></a>Składnia  
  
```  
rename_namespace("NewName")  
```  
  
#### <a name="parameters"></a>Parametry  
 `NewName`  
 Nowa nazwa przestrzeni nazw.  
  
## <a name="remarks"></a>Uwagi  
 Trwa jeden argument *NewName*, który określa nową nazwę dla przestrzeni nazw.  
  
 Aby usunąć przestrzeń nazw, należy użyć [no_namespace —](../preprocessor/no-namespace.md) zamiast tego atrybutu.  
  
 **KOŃCOWY określonego języka C++**  
  
## <a name="see-also"></a>Zobacz też  
 [atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)   
 [#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)