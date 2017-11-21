---
title: "C3618 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3618
dev_langs: C++
helpviewer_keywords: C3618
ms.assetid: cacc105d-4389-4cb8-ae6c-41a3622e9a86
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3b014cb60c2e9a65888fa425f4046c118cfc31d2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3618"></a>C3618 błąd kompilatora
"Funkcja": nie można zdefiniować metody oznaczonej jako DllImport  
  
 Metody oznaczone <xref:System.Runtime.InteropServices.DllImportAttribute> jest zdefiniowany w określonym. BIBLIOTEKI DLL.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3618.  
  
```  
// C3618.cpp  
// compile with: /clr /c  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
[ DllImport("user32.dll", EntryPoint="MessageBox", CharSet=CharSet::Ansi) ]  // CHANGED   
void Func();   
  
void Func() {}   // C3618, remove this function definition to resolve  
```