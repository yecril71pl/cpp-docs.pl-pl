---
title: "Ostrzeżenie LNK4253 narzędzi konsolidatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK4253
dev_langs: C++
helpviewer_keywords: LNK4253
ms.assetid: ec7433a9-aa9c-495a-a9f2-075e7bc3e7bc
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6d1142544852980b8bd1d543783a9ffdf3361879
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-warning-lnk4253"></a>Ostrzeżenie LNK4253 narzędzi konsolidatora
sekcja sekcja "1" nie została scalona z elementem 'Sekcja2'; już scalona z elementem "section3"  
  
 Konsolidator Wykryto wiele żądań powodujące konflikty scalania. Konsolidator zignoruje jednego żądania.  
  
 A **/MERGE** napotkano opcji lub dyrektywie i `from` sekcji już została scalona innej sekcji z powodu poprzedniej **/MERGE** opcji lub dyrektywie (lub z powodu niejawne scalania z konsolidator).  
  
 Aby rozwiązać LNK4253, Usuń jedno z żądań scalania.  
  
 Jeśli celem x86 maszyn i cele systemu Windows CE (ARM, MIPS SH4 i Thumb) z programem Visual C++. Sekcja CRT jest teraz tylko do odczytu. Jeśli kod jest zależny od poprzednie (. CRT sekcje są odczytu/zapisu), można zaobserwować nieoczekiwane zachowanie.  
  
 Aby uzyskać więcej informacji, zobacz,  
  
-   [/ MERGE (Połącz sekcje)](../../build/reference/merge-combine-sections.md)  
  
-   [komentarz (C/C++)](../../preprocessor/comment-c-cpp.md)  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie konsolidator otrzymuje instrukcję merge `.rdata` sekcji dwa razy, ale w różne sekcje. Poniższy przykład generuje LNK4253.  
  
```  
// LNK4253.cpp  
// compile with: /W1 /link /merge:.rdata=text2  
// LNK4253 expected  
#pragma comment(linker, "/merge:.rdata=.text")  
int main() {}  
```