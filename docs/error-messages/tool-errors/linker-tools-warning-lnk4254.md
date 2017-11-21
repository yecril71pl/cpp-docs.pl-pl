---
title: "Ostrzeżenie LNK4254 narzędzi konsolidatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK4254
dev_langs: C++
helpviewer_keywords: LNK4254
ms.assetid: 6f41dfb3-ca21-40d3-bac7-b637e578efa4
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 47e8e020cdf8d888e77d212a25fa9344e744e895
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-warning-lnk4254"></a>Ostrzeżenie LNK4254 narzędzi konsolidatora
sekcja sekcja "1" (przesunięcie) została scalona z elementem "Sekcja2" (przesunięcie) z różnymi atrybutami  
  
 Zawartość jedną sekcję zostały scalone do innego, ale atrybuty dwie sekcje są różne. Program może dać nieoczekiwane wyniki. Na przykład dane, które mają być odczytywane tylko może być teraz w zapisywalna sekcja.  
  
 Aby rozwiązać LNK4254, zmodyfikuj lub Usuń żądanie scalania.  
  
 Jeśli celem x86 maszyn i cele systemu Windows CE (ARM, MIPS SH4 i Thumb) z programem Visual C++. Sekcja CRT jest tylko do odczytu. Jeśli poprzednie zależy od kodu (. CRT sekcje są odczytu/zapisu), można zaobserwować nieoczekiwane zachowanie.  
  
 Aby uzyskać więcej informacji, zobacz,  
  
-   [/ MERGE (Połącz sekcje)](../../build/reference/merge-combine-sections.md)  
  
-   [komentarz (C/C++)](../../preprocessor/comment-c-cpp.md)  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje LNK4254.  
  
```  
// LNK4254.cpp  
// compile with: /W1 /link /WX  
// LNK4254 expected  
#pragma comment(linker, "/merge:.data=.text")  
int main() {}  
```