---
title: C2868 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2868
dev_langs:
- C++
helpviewer_keywords:
- C2868
ms.assetid: 6ff5837b-e66d-44d1-9d17-80af35e08d08
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 84465453ca7a1d76a9dd6b199232384c2ef9124b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33244368"
---
# <a name="compiler-error-c2868"></a>C2868 błąd kompilatora  
  
> "*identyfikator*": Niedozwolona składnia dla deklaracji using; Oczekiwano kwalifikowanej nazwy  
  
A [za pomocą deklaracji](../../cpp/using-declaration.md) wymaga *kwalifikowana nazwa*, operatora zakresu (`::`) oddzielone sekwencji nazwy przestrzeni nazw, klasy lub wyliczenia, która kończy się nazwa identyfikatora. Operator rozpoznawania pojedynczy zakres może służyć do wprowadzenia nazwy z globalnej przestrzeni nazw.  
  
## <a name="example"></a>Przykład  
  
Poniższy przykład generuje C2868 i przedstawiono również poprawne użycie:  
  
```cpp  
// C2868.cpp  
class X {  
public:  
   int i;  
};  
  
class Y : X {  
public:  
   using X::i;   // OK  
};  
  
int main() {  
   using X;   // C2868  
}  
```