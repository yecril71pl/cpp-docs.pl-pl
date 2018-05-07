---
title: C2593 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2593
dev_langs:
- C++
helpviewer_keywords:
- C2593
ms.assetid: 4a0fe9bb-2163-447d-91f6-1890ed8250f6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e419416266e0e3c4ebff8190b3b26b1c43c9ba0f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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