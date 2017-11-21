---
title: "Kompilatora (poziom 1) ostrzeżenie C4274 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4274
dev_langs: C++
helpviewer_keywords: C4274
ms.assetid: 5a948680-7ed1-469f-978d-ae99d154e161
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0c6bb31350af030879f23d9c0a9ac105e7293480
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4274"></a>Kompilator C4274 ostrzegawcze (poziom 1)
\#Ident ignorowane. zobacz dokumentację dla #pragma comment (exestr, "string")  
  
 `#ident` Dyrektywa, która wstawia ciąg określone przez użytkownika w obiekcie lub pliku wykonywalnego, jest przestarzały. W rezultacie Kompilator ignoruje dyrektywy.  
  
> [!CAUTION]
>  Ostrzeżenie C4274 informacją o tym, aby użyć [#pragma comment (exestr, "string")](../../preprocessor/comment-c-cpp.md) dyrektywy. Jednak ta informacja jest przestarzała i zostanie zaktualizowany w przyszłej wersji kompilatora. Jeśli używasz `#pragma` dyrektywy, narzędzi konsolidatora (LINK.exe) ignoruje rekordu komentarz utworzonego przez dyrektywę i ostrzeżenie [LNK4229](../../error-messages/tool-errors/linker-tools-warning-lnk4229.md). Zamiast `#ident` dyrektywy, firma Microsoft zaleca się używanie ciąg zasobu wersji pliku w aplikacji.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Usuń `#ident "` *ciąg* `"` dyrektywy.  
  
## <a name="see-also"></a>Zobacz też  
 [komentarz (C/C++)](../../preprocessor/comment-c-cpp.md)   
 [Ostrzeżenie LNK4229 narzędzi konsolidatora](../../error-messages/tool-errors/linker-tools-warning-lnk4229.md)   
 [Praca z plikami zasobów](../../windows/working-with-resource-files.md)