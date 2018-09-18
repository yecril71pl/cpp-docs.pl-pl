---
title: Kompilator ostrzeżenie (poziom 1) C4002 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4002
dev_langs:
- C++
helpviewer_keywords:
- C4002
ms.assetid: 6bda1dfe-e2e4-4771-9794-5a404c466dd5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a3b3d51b4408e79236993d49f7ceba5fc9537b6d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46050141"
---
# <a name="compiler-warning-level-1-c4002"></a>Kompilator ostrzeżenie (poziom 1) C4002

zbyt wiele parametrów rzeczywistych dla makra 'Identyfikator'

Liczba rzeczywistych parametrów w makrze przekracza liczbę parametrów formalnych w definicji makra. Preprocesora zbiera dodatkowe parametry ale je ignoruje w rozwinięciu makra.

C4002 może wystąpić, gdy niepoprawnie przy użyciu [makra Wariadyczne](../../preprocessor/variadic-macros.md).

Poniższy przykład spowoduje wygenerowanie C4002:

```
// C4002.cpp
// compile with: /W1
#define test(a) (a)

int main() {
   int a = 1;
   int b = 2;
   a = test(a,b);   // C4002
   // try..
   a = test(a);
}
```

Ten błąd może być też wygenerowany w wyniku pracy zgodności kompilatora, która została wykonana dla Visual Studio .NET 2003: dodatkowy przecinkami w makrze już akceptowane.

Kompilator nie będzie akceptował dodatkowe przecinkami w makrze. Aby kod był prawidłowy w Visual Studio .NET 2003 i wersji programu Visual Studio .NET, Visual c++ należy usunąć dodatkowe przecinkami.

```
// C4002b.cpp
// compile with: /W1
#define F(x,y)
int main()
{
   F(2,,,,,,3,,,,,,)   // C4002
   // Try the following line instead:
   // F(2,3)
}
```