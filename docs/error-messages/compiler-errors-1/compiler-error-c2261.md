---
title: Błąd C2261 kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2261
dev_langs:
- C++
helpviewer_keywords:
- C2261
ms.assetid: 60969482-9e83-49b5-9631-a04bc844da12
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 45050daf3149cd813fb23b5814be5fe49c375f03
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33170469"
---
# <a name="compiler-error-c2261"></a>Błąd C2261 kompilatora
"string": odwołanie do zestawu jest nieprawidłowa i nie można go rozpoznać  
  
 Wartość jest nieprawidłowa.  
  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> Służy do określania przyjaznego zestawu. Na przykład, jeśli a.dll chce określić b.dll jako przyjaznego zestawu, należy określić (w a.dll): InternalsVisibleTo("b"). Środowisko uruchomieniowe umożliwia następnie b.dll na dostęp do wszystkich elementów w a.dll (z wyjątkiem typów prywatnych).  
  
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