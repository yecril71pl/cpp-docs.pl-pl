---
title: "#<a name=\"error-directive-cc--microsoft-docs\"></a>Błąd — dyrektywa (C/C++) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: '#error'
dev_langs: C++
helpviewer_keywords:
- '#error directive'
- preprocessor, directives
- error directive (#error directive)
ms.assetid: d550a802-ff19-4347-9597-688935d23b2b
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5bb05612ed7262b9daf287793c93ccce654306d6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="error-directive-cc"></a>#error — dyrektywa (C/C++)
`#error` Dyrektywy emituje komunikat określone przez użytkownika w czasie kompilacji, a następnie kończy kompilacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
#errortoken-string  
```  
  
## <a name="remarks"></a>Uwagi  
 Zawiera komunikat o błędzie, który emituje tej dyrektywy *ciąg tokenu* parametru. `token-string` Parametru nie podlega rozwinięciu makra. Ta dyrektywa jest najbardziej przydatna podczas przetwarzania wstępnego powiadamiania dewelopera niespójność program lub naruszenie ograniczenia. W poniższym przykładzie pokazano wystąpił błąd podczas przetwarzania podczas przetwarzania wstępnego:  
  
```  
#if !defined(__cplusplus)  
#error C++ compiler required.  
#endif  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Dyrektywy preprocesora](../preprocessor/preprocessor-directives.md)