---
title: "Ostrzeżenie LNK4224 narzędzi konsolidatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK4224
dev_langs: C++
helpviewer_keywords: LNK4224
ms.assetid: 8624b70e-0b93-43cf-b457-834d38632d0b
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: cc1e54f2dbe3af96194fb6af0fae99292e49b545
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-warning-lnk4224"></a>Ostrzeżenie LNK4224 narzędzi konsolidatora
opcja nie jest już obsługiwany; ignorowane  
  
 — Opcja konsolidatora nieprawidłowy, przestarzałe został określony i zignorowany.  
  
 Na przykład LNK4224 może wystąpić, jeśli dyrektywa/Comment pojawia się w. obiektu Dyrektywa/Comment zostałyby dodane za pośrednictwem [komentarz (C/C++)](../../preprocessor/comment-c-cpp.md) pragma przy użyciu opcji exestr przestarzałe. Użyj polecenia dumpbin [/ALL](../../build/reference/all.md) do wyświetlenia w pliku .obj dyrektywy konsolidatora.  
  
 Jeśli to możliwe zmodyfikuj źródła dla plików .obj i Usuń pragma. Jeśli możesz zignorować to ostrzeżenie, istnieje możliwość, że .executable skompilowana z **/CLR: pure** nie będzie działać zgodnie z oczekiwaniami.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje LNK4224.  
  
```  
// LNK4224.cpp  
// compile with: /c /Zi  
// post-build command: link LNK4224.obj /debug /debugtype:map  
int main () {  
   return 0;  
}  
```