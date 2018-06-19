---
title: Kompilatora (poziom 1) ostrzeżenie C4917 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4917
dev_langs:
- C++
helpviewer_keywords:
- C4917
ms.assetid: c05e2610-4a5d-4f4b-a99b-c15fd7f1d5f1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: afc38da9bb06879745fb96afd8224a4f599bb252
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33298866"
---
# <a name="compiler-warning-level-1-c4917"></a>Kompilator C4917 ostrzegawcze (poziom 1)
"deklarator": identyfikator GUID może być skojarzony tylko z klasą, interfejsem lub przestrzeni nazw  
  
Struktury zdefiniowane przez użytkownika innego niż [klasy](../../cpp/class-cpp.md), [interfejsu](../../cpp/interface.md), lub [przestrzeni nazw](../../cpp/namespaces-cpp.md) nie może mieć postać identyfikatora GUID.  
  
To ostrzeżenie jest domyślnie wyłączone. Zobacz [kompilatora ostrzeżeń czy są wyłączone domyślnie](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Aby uzyskać więcej informacji.  
  
## <a name="example"></a>Przykład  
Poniższy przykład kodu generuje C4917:  
  
```cpp  
// C4917.cpp  
// compile with: /W1  
#pragma warning(default : 4917)  
__declspec(uuid("00000000-0000-0000-0000-000000000001")) struct S  
{  
} s;   // C4917, don't put uuid on a struct  
  
int main()  
{  
}  
```