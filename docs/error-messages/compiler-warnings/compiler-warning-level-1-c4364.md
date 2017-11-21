---
title: "Kompilatora (poziom 1) ostrzeżenie C4364 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4364
dev_langs: C++
helpviewer_keywords: C4364
ms.assetid: 1477634c-d60f-4570-ad16-1aaeae24ac7f
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 94004ea52d76d39657da1fdb79e0b61777524d47
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4364"></a>Kompilator C4364 ostrzegawcze (poziom 1)
\#przy użyciu zestawu "file" poprzednio widziano w location(line_number) bez atrybutu as_friend; nie zastosowano as_friend  
  
 A `#using` dyrektywa został powtórzony pliku metadanych, ale `as_friend` kwalifikatora nie użyto pierwszego wystąpienia; Kompilator zignoruje drugi `as_friend`.  
  
 Aby uzyskać więcej informacji, zobacz [przyjazne zestawy (C++)](../../dotnet/friend-assemblies-cpp.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy składnik.  
  
```  
// C4364.cpp  
// compile with: /clr /LD  
ref class A {};  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C4364.  
  
```  
// C4364_b.cpp  
// compile with: /clr /W1 /c  
#using " C4364.dll"  
#using " C4364.dll" as_friend   // C4364  
```