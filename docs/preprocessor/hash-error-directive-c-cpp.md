---
title: '#Błąd — dyrektywa (C/C++) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- '#error'
dev_langs:
- C++
helpviewer_keywords:
- '#error directive'
- preprocessor, directives
- error directive (#error directive)
ms.assetid: d550a802-ff19-4347-9597-688935d23b2b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d2da939fe52e41e122ecd4926e34fb9c4be735ae
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/10/2018
ms.locfileid: "42465328"
---
# <a name="error-directive-cc"></a>#error — dyrektywa (C/C++)
**#Error** dyrektywy emituje komunikat określony przez użytkownika w czasie kompilacji, a następnie kończy kompilacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
#errortoken-string  
```  
  
## <a name="remarks"></a>Uwagi  
 
Zawiera komunikat o błędzie, który emituje ta dyrektywa *ciąg tokenu* parametru. *Ciąg tokenu* parametru nie podlega rozwinięciu makra. Ta dyrektywa jest najbardziej przydatna podczas przetwarzania wstępnego powiadamiania Deweloper niespójność program lub naruszenie ograniczenia. W poniższym przykładzie pokazano wystąpił błąd podczas przetwarzania podczas przetwarzania wstępnego:  
  
```  
#if !defined(__cplusplus)  
#error C++ compiler required.  
#endif  
```  
  
## <a name="see-also"></a>Zobacz też  
 
[Dyrektywy preprocesora](../preprocessor/preprocessor-directives.md)