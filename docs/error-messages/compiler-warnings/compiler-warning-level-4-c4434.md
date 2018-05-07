---
title: Kompilatora (poziom 4) ostrzeżenie C4434 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4434
dev_langs:
- C++
helpviewer_keywords:
- C4434
ms.assetid: 24b8785e-353a-4c37-8bed-ed61001a871d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c639fa1cc89266fd9cc2935d88132ceae225a85e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-4-c4434"></a>Kompilator C4434 ostrzegawcze (poziom 4)
Konstruktor klasy musi posiadać prywatną dostępność; Zmiana na prywatny dostęp  
  
 C4434 oznacza, że kompilator zmieniony dostępność Konstruktor statyczny. Konstruktory statyczne musi posiadać prywatną dostępność, ponieważ są one przeznaczone tylko do wywołania przez środowisko uruchomieniowe języka wspólnego. Aby uzyskać więcej informacji, zobacz [konstruktory statyczne](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Static_constructors).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C4434.  
  
```  
// C4434.cpp  
// compile with: /W4 /c /clr  
public ref struct R {  
   static R(){}   // C4434  
};  
```