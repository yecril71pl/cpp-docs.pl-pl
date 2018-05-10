---
title: rename_namespace — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- rename_namespace
dev_langs:
- C++
helpviewer_keywords:
- rename_namespace attribute
ms.assetid: 45006d2b-36cd-4bec-98b9-3b8ec45299e3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a51114787dde2f858a8409538083282ef292d599
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
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