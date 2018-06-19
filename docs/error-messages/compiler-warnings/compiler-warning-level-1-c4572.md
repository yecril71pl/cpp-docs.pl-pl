---
title: Kompilatora (poziom 1) ostrzeżenie C4572 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4572
dev_langs:
- C++
helpviewer_keywords:
- C4572
ms.assetid: 482dee5a-29bd-4fc3-b769-9dfd4cd2a964
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ec0c0068a3da1033162f90330876d74d62878178
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33280471"
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