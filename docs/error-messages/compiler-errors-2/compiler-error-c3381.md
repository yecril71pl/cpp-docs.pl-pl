---
title: "C3381 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3381
dev_langs: C++
helpviewer_keywords: C3381
ms.assetid: d276c89f-8377-4cb6-a8d4-7770885f06c4
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: af632ae602cacb5204f1fac1088bef8a6cd20168
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3381"></a>C3381 błąd kompilatora
"assembly": specyfikatory dostępu do zestawu są dostępne tylko w kodzie skompilowanym z opcją/CLR  
  
 Typy natywne może być widoczny spoza zestawu, ale można określić tylko dostęp do zestawu dla natywnych typów w **/CLR** kompilacji.  
  
 Aby uzyskać więcej informacji, zobacz [wpisz widoczność](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility) i [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../../build/reference/clr-common-language-runtime-compilation.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3381.  
  
```  
// C3381.cpp  
// compile with: /c  
public class A {};   // C3381  
```