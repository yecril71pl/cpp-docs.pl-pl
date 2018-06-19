---
title: Kompilatora (poziom 4) ostrzeżenie C4681 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4681
dev_langs:
- C++
helpviewer_keywords:
- C4681
ms.assetid: a4e6d85f-3e21-4b45-a551-c23d3c554d3f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fea1628ec77294ff6698e123b2c199cad2a17596
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33295366"
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