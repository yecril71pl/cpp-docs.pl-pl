---
title: "C2593 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2593
dev_langs:
- C++
helpviewer_keywords:
- C2593
ms.assetid: 4a0fe9bb-2163-447d-91f6-1890ed8250f6
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 675c929995e7b0c4043586cf081343136d8e7a5e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2593"></a>C2593 błąd kompilatora
'operator identyfikator' jest niejednoznaczny  
  
 Więcej niż jeden operator możliwe jest zdefiniowany dla przeciążonego operatora.  
  
 Ten błąd może być ustalony użycie jawnego rzutowania na jeden lub więcej parametrów rzeczywistych.  
  
 Poniższy przykład generuje C2593:  
  
```  
// C2593.cpp  
struct A {};  
struct B : A {};  
struct X {};  
struct D : B, X {};  
void operator+( X, X );  
void operator+( A, B );  
D d;  
  
int main() {  
   d +  d;         // C2593, D has an A, B, and X   
   (X)d + (X)d;    // OK, uses operator+( X, X )  
}  
```  
  
 Ten błąd może być spowodowane serializacji zmiennoprzecinkowe using zmiennej `CArchive` obiektu. Kompilator identyfikuje `<<` operatora jako niejednoznaczne. C++ tylko typy pierwotne typy, które `CArchive` może wykonać serializację typu stałym rozmiarze `BYTE`, `WORD`, `DWORD`, i `LONG`. Wszystkie typy całkowite musi być rzutowane na jednego z tych typów do serializacji. Typy zmiennoprzecinkowe musi być archiwizowane za pomocą `CArchive::Write()` funkcję elementu członkowskiego.  
  
 Poniższy przykład przedstawia sposób archiwum zmienną liczb zmiennoprzecinkowych (`f`) do archiwum `ar`:  
  
```  
ar.Write(&f, sizeof( float ));  
```