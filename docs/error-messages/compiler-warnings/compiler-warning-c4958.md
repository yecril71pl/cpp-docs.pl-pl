---
title: "C4958 ostrzeżenia kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4958
dev_langs: C++
helpviewer_keywords: C4958
ms.assetid: e79b9e9c-d572-4a3a-a3b6-60962b70864a
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 932f12c5465d08db22c7bac977dfeab94d61f1f4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-c4958"></a>C4958 ostrzeżenia kompilatora
"operacji": arytmetyka wskaźnika nie jest możliwe do zweryfikowania  
  
 Przy użyciu arytmetyki wskaźnika utworzy obrazie niemożliwy.  
  
 Aby uzyskać więcej informacji, zobacz [czystej i weryfikowalny kod (C + +/ CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md).  
  
 To ostrzeżenie jest wystawione jako błąd i może być wyłączone z [ostrzeżenie](../../preprocessor/warning.md) pragma lub [/wd](../../build/reference/compiler-option-warning-level.md) — opcja kompilatora.  
  
 Poniższy przykład generuje C4958:  
  
```  
// C4958.cpp  
// compile with: /clr:safe  
// #pragma warning( disable : 4958 )  
using namespace System;  
  
int main( ) {  
   Int32 arr[] = new Int32[10];  
   Int32* p = &arr[0];  
   p++;   // C4958  
}  
```  
  
 Kompilator implementuje operacji tablicy z arytmetyka wskaźnika. W związku z tym natywnego tablice nie są możliwe do zweryfikowania; w zamian użyj tablicy CLR. Aby uzyskać więcej informacji, zobacz [tablicy](../../windows/arrays-cpp-component-extensions.md).  
  
 Poniższy przykład generuje C4958:  
  
```  
// C4958b.cpp  
// compile with: /clr:safe  
// #pragma warning( disable : 4958 )  
  
int main() {  
   int array[5];  
   array[4] = 0;   // C4958  
}  
```