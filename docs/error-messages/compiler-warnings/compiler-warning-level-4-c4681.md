---
title: "Kompilatora (poziom 4) ostrzeżenie C4681 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4681
dev_langs:
- C++
helpviewer_keywords:
- C4681
ms.assetid: a4e6d85f-3e21-4b45-a551-c23d3c554d3f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0c7c53ef74208907b30eb800ed0d7021d0f71e6e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4681"></a>Kompilator C4681 ostrzegawcze (poziom 4)
"class": klasa coclass nie określa domyślnego interfejsu, który jest źródłem zdarzenia  
  
 A [źródła](../../windows/source-cpp.md) interfejs nie został określony dla klasy.  
  
 Poniższy przykład generuje C4681:  
  
```  
// C4681.cpp  
// compile with: /W4 /c  
#define _ATL_ATTRIBUTES 1  
#include <atlbase.h>  
#include <atlcom.h>  
  
[module(name="test")];  
  
[dual, uuid("00000000-0000-0000-0000-000000000000")]  
__interface IEvent { [id(3)] HRESULT myEvent(); };  
  
[object, uuid("00000000-0000-0000-0000-000000000001")]  
__interface ISource { HRESULT Fire(); };  
  
[ coclass,   
  source(IEvent),   
  default(ISource),  
  // Uncomment the following line to resolve.  
  // default(IEvent),   
  uuid("00000000-0000-0000-0000-000000000002")   
]  
struct CSource : ISource {   // C4681  
   HRESULT Fire() { return 0; }  
};  
```