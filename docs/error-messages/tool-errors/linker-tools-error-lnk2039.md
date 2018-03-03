---
title: "Błąd narzędzi konsolidatora LNK2039 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK2039
dev_langs:
- C++
helpviewer_keywords:
- LNK2039
ms.assetid: eaa296bd-4901-41f6-8410-6d03ee827144
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 441765d85ce65a80102ed94b3f4394ae48c0e29f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk2039"></a>Błąd narzędzi konsolidatora LNK2039
Importowanie klasy referencyjnej\<typu > "zdefiniowanego w another.obj; powinien być albo importowanych albo zdefiniowana, ale nie oba  
  
 Klasa ref "<`type`>" jest importowany w pliku .obj określony, ale jest także zdefiniowana w innym pliku .obj. Ten warunek może spowodować błąd czasu wykonywania lub inne nieoczekiwane zachowania.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Sprawdź, czy "`type`" musi być zdefiniowana w pliku obj. i sprawdź, czy należy zaimportować z pliku winmd.  
  
2.  Usuń definicję lub importu.  
  
## <a name="see-also"></a>Zobacz też  
 [Błędy i ostrzeżenia narzędzi konsolidatora](../../error-messages/tool-errors/linker-tools-errors-and-warnings.md)   
 [Błąd narzędzi konsolidatora LNK1332](../../error-messages/tool-errors/linker-tools-error-lnk1332.md)