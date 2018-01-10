---
title: "Kompilatora (poziom 1) ostrzeżenie C4572 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4572
dev_langs: C++
helpviewer_keywords: C4572
ms.assetid: 482dee5a-29bd-4fc3-b769-9dfd4cd2a964
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ee599d1385d71fee1b03d4298f27e1c8ed5ccbd2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4572"></a>Kompilator C4572 ostrzegawcze (poziom 1)
Atrybut [ParamArray] jest przestarzały z opcją/CLR, użyj "..." zamiast niego  
  
 Przestarzały styl służący do określania listy zmiennych argumentów została użyta. W przypadku kompilowania kodu dla środowiska CLR, należy użyć składni wielokropka zamiast <xref:System.ParamArrayAttribute>. Aby uzyskać więcej informacji, zobacz [zmiennej listy argumentów (...) (C + +/ CLI) ](../../windows/variable-argument-lists-dot-dot-dot-cpp-cli.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C4572.  
  
```  
// C4572.cpp  
// compile with: /clr /W1  
void Func([System::ParamArray] array<int> ^);   // C4572  
void Func2(... array<int> ^){}   // OK  
  
int main() {  
   Func2(1, 2, 3);  
}  
```