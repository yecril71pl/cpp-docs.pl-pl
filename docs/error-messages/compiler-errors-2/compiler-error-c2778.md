---
title: Błąd kompilatora C2778 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2778
dev_langs:
- C++
helpviewer_keywords:
- C2778
ms.assetid: b24cb732-2914-42cc-8928-e2d87b393428
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d68180e2fc0c7c33e742f0ffdb3776baa50976f6
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43209716"
---
# <a name="compiler-error-c2778"></a>Błąd kompilatora C2778
niewłaściwie uformowane GUID w __declspec(uuid())  
  
 Podano niepoprawny identyfikator GUID do [uuid](../../cpp/uuid-cpp.md) atrybutów rozszerzonych.  
  
 Identyfikator GUID musi być ciągiem liczb szesnastkowych o następującym formacie:  
  
```  
// C2778a.cpp  
// compile with: /c  
struct __declspec(uuid("00000000-0000-0000-0000-000000000000")) A {};  
struct __declspec(uuid("{00000000-0000-0000-0000-000000000000}")) B{};  
```  
  
 `uuid` Atrybutów rozszerzonych akceptuje ciągi rozpoznawane przez [CLSIDFromString](/windows/desktop/api/combaseapi/nf-combaseapi-clsidfromstring), z ogranicznikami lub bez nawiasów.  
  
 Poniższy przykład spowoduje wygenerowanie C2778:  
  
```  
// C2778b.cpp  
struct __declspec(uuid(" 00000000-0000-0000-0000-000000000000 ")) C { };   // C2778  
struct __declspec(uuid("00000000000000000000000000000000")) D { };   // C2778  
```