---
title: Błąd narzędzi konsolidatora LNK2039 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2039
dev_langs:
- C++
helpviewer_keywords:
- LNK2039
ms.assetid: eaa296bd-4901-41f6-8410-6d03ee827144
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 954ea12eb9b49c2bdf59b31a1ec2ec2e66c124ef
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33302100"
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