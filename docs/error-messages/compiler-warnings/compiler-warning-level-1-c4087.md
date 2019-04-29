---
title: Kompilatora (poziom 1) ostrzeżenie C4087
ms.date: 11/04/2016
f1_keywords:
- C4087
helpviewer_keywords:
- C4087
ms.assetid: 546e4d57-5c8e-422c-8ef1-92657336dad5
ms.openlocfilehash: 84d24d95053b962c1776dc18576e4ed236b63469
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62363872"
---
# <a name="compiler-warning-level-1-c4087"></a>Kompilatora (poziom 1) ostrzeżenie C4087

'Funkcja': zadeklarowana z listą parametrów "void"

Deklaracja funkcji nie ma formalnych parametrów, ale wywołanie funkcji ma rzeczywistych parametrów. Dodatkowe parametry są przekazywane według konwencji wywołania funkcji.

To ostrzeżenie jest dla kompilatora C.

## <a name="example"></a>Przykład

```
// C4087.c
// compile with: /W1
int f1( void ) {
}

int main() {
   f1( 10 );   // C4087
}
```