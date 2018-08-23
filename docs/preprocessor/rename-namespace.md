---
title: rename_namespace | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 0876aed966db79b23d506bffd9247dd68d4a3935
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/10/2018
ms.locfileid: "42465331"
---
# <a name="renamenamespace"></a>rename_namespace
**Określonego język C++**  
  
Zmienia nazwę przestrzeni nazw, który znajduje się zawartość biblioteki typów.  
  
## <a name="syntax"></a>Składnia  
  
```  
rename_namespace("NewName")  
```  
  
### <a name="parameters"></a>Parametry  
*Nowa nazwa*  
Nowa nazwa przestrzeni nazw.  
  
## <a name="remarks"></a>Uwagi  
 
Trwa pojedynczy argument *NewName*, która określa nową nazwę dla przestrzeni nazw.  
  
Aby usunąć przestrzeń nazw, należy użyć [no_namespace](../preprocessor/no-namespace.md) zamiast tego atrybutu.  
  
**KONIEC określonego języka C++**  
  
## <a name="see-also"></a>Zobacz też  
 
[atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)   
[#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)