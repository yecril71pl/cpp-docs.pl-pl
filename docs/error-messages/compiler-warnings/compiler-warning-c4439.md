---
title: C4439 ostrzeżenia kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4439
dev_langs:
- C++
helpviewer_keywords:
- C4439
ms.assetid: 9449958f-f407-4824-829b-9e092f2af97d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4767f03d51bf1fcaac51678d17d454949eb30875
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33286958"
---
# <a name="compiler-warning-c4439"></a>C4439 ostrzeżenia kompilatora
"Funkcja": definicja funkcji z zarządzanym typem w sygnaturze musi mieć konwencję wywołania __clrcall  
  
 Kompilator niejawnie zastąpić Konwencja wywoływania z [__clrcall](../../cpp/clrcall.md). Aby usunąć to ostrzeżenie, Usuń `__cdecl` lub `__stdcall` konwencji wywoływania.  
  
 C4439 jest zawsze wystawione jako błąd. Możesz wyłączyć to ostrzeżenie o `#pragma warning` lub **/wd**; zobacz [ostrzeżenie](../../preprocessor/warning.md) lub [/w, /W0, /W1, /W2, /W3, / W4, /w1, /w2, /w3, / W4, / Wall, /wd, / możemy /wo, /Wv, wx (poziom ostrzegawczy)](../../build/reference/compiler-option-warning-level.md)Aby uzyskać więcej informacji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C4439.  
  
```  
// C4439.cpp  
// compile with: /clr  
void __stdcall f( System::String^ arg ) {}   // C4439  
void __clrcall f2( System::String^ arg ) {}   // OK  
void f3( System::String^ arg ) {}   // OK  
```