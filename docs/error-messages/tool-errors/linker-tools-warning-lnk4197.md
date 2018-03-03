---
title: "Ostrzeżenie LNK4197 narzędzi konsolidatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK4197
dev_langs:
- C++
helpviewer_keywords:
- LNK4197
ms.assetid: 8a976fd7-a74b-4c83-ab66-a9e7d7073c4a
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b1fadbf2ba5b18004f0e89142c88a68437842a92
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-warning-lnk4197"></a>Ostrzeżenie LNK4197 narzędzi konsolidatora
Eksport "exportname" określony wiele razy; użyta pierwsza Specyfikacja  
  
 Eksport jest określone w wielu i różne sposoby. Konsolidator używa pierwsza Specyfikacja i pomija pozostałe.  
  
 Odbudowywania biblioteki wykonawczej języka C, możesz zignorować ten komunikat.  
  
 Jeżeli eksport został określony wiele razy ten sam sposób, konsolidator nie będzie wystawiać ostrzeżenie.  
  
 Na przykład następujące zawartość pliku .def spowodowałoby to ostrzeżenie:  
  
```  
EXPORTS  
   functioname      NONAME  
   functioname      @10  
```  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać problem, sprawdzając następujące możliwe przyczyny  
  
1.  Tej samej eksportu jest określony zarówno w wierszu polecenia (za pośrednictwem eksportu:) w plik .def  
  
2.  Tym samym eksportu znajduje się dwa razy w pliku .def z różnymi atrybutami.