---
title: Kompilatora (poziom 1) ostrzeżenie C4581 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4581
dev_langs:
- C++
helpviewer_keywords:
- C4581
ms.assetid: 598bcd87-257d-4eb3-94e4-15bb31aadc99
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 415fb9ffc3e53ddfe9edcee2ec99361b38de0dea
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4581"></a>Kompilator C4581 ostrzegawcze (poziom 1)
zachowanie przestarzałe: "ciąg1" zastąpione "ciąg2", aby przetwarzać atrybut  
  
 Ten błąd może być wygenerowanego w wyniku pracy zgodność kompilatora, która została wykonana dla Visual C++ 2005: parametr sprawdzanie dla atrybutów języka Visual C++.  
  
 W poprzednich wersjach wartości atrybutów zostały zaakceptowane, czy zostały one ujęte w cudzysłów. Jeśli wartość to wyliczanie, nie musi być ujęta w cudzysłów.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C4581.  
  
```  
// C4581.cpp  
// compile with: /c /W1  
#include "unknwn.h"  
[object, uuid("00000000-0000-0000-0000-000000000001")]  
__interface IMyI : IUnknown {};  
  
[coclass, uuid(12345678-1111-2222-3333-123456789012), threading("free")]   // C4581  
// try the following line instead  
// [coclass, uuid(12345678-1111-2222-3333-123456789012), threading(free)]  
class CSample : public IMyI {};  
```