---
title: "C2778 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2778
dev_langs: C++
helpviewer_keywords: C2778
ms.assetid: b24cb732-2914-42cc-8928-e2d87b393428
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d3801f7ddef23f90a76007a09fdc7a2d552b7fdb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2778"></a>C2778 błąd kompilatora
niewłaściwie uformowane GUID w __declspec(uuid())  
  
 Nieprawidłowy identyfikator GUID został dostarczony do [uuid](../../cpp/uuid-cpp.md) rozszerzonych atrybutów.  
  
 Identyfikator GUID musi być ciągiem szesnastkowym liczb o następującym formacie:  
  
```  
// C2778a.cpp  
// compile with: /c  
struct __declspec(uuid("00000000-0000-0000-0000-000000000000")) A {};  
struct __declspec(uuid("{00000000-0000-0000-0000-000000000000}")) B{};  
```  
  
 `uuid` Rozszerzonych atrybutów akceptuje ciągi rozpoznał [CLSIDFromString](http://msdn.microsoft.com/library/windows/desktop/ms680589), z lub bez ograniczników nawiasu klamrowego.  
  
 Poniższy przykład generuje C2778:  
  
```  
// C2778b.cpp  
struct __declspec(uuid(" 00000000-0000-0000-0000-000000000000 ")) C { };   // C2778  
struct __declspec(uuid("00000000000000000000000000000000")) D { };   // C2778  
```