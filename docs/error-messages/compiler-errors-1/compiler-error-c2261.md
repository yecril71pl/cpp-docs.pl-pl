---
title: "Błąd C2261 kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2261
dev_langs: C++
helpviewer_keywords: C2261
ms.assetid: 60969482-9e83-49b5-9631-a04bc844da12
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8269b891ed899501625973b81c1823d4db2d56c8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2261"></a>Błąd C2261 kompilatora
"string": odwołanie do zestawu jest nieprawidłowa i nie można go rozpoznać  
  
 Wartość jest nieprawidłowa.  
  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>Służy do określania przyjaznego zestawu. Na przykład, jeśli a.dll chce określić b.dll jako przyjaznego zestawu, należy określić (w a.dll): InternalsVisibleTo("b"). Środowisko uruchomieniowe umożliwia następnie b.dll na dostęp do wszystkich elementów w a.dll (z wyjątkiem typów prywatnych).  
  
 Aby uzyskać więcej informacji o poprawnej składni podczas określania przyjazne zestawy zobacz [przyjazne zestawy (C++)](../../dotnet/friend-assemblies-cpp.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C2261.  
  
```  
// C2261.cpp  
// compile with: /clr /c  
using namespace System::Runtime::CompilerServices;  
[assembly: InternalsVisibleTo("a,a,a")];   // C2261  
[assembly: InternalsVisibleTo("a.a")];   // OK  
[assembly: InternalsVisibleTo("a")];   // OK  
```