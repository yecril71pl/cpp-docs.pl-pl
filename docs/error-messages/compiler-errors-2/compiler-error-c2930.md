---
title: Błąd kompilatora C2930
ms.date: 11/04/2016
f1_keywords:
- C2930
helpviewer_keywords:
- C2930
ms.assetid: f07eecd1-e5d1-4518-bd89-b1fd2a003a17
ms.openlocfilehash: 20fa3e81e66bb30bd63e579a863b6071de4ef871
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50434830"
---
# <a name="compiler-error-c2930"></a>Błąd kompilatora C2930

"class": typ klasy identyfikator ponownie definiowana jako moduł wyliczający 'Identyfikator enum'

Nie można użyć klasy generyczny lub szablonu jest członkiem wyliczenia.

Ten błąd może być spowodowany nawiasy klamrowe są nieprawidłowo dopasowywane.

Poniższy przykład spowoduje wygenerowanie C2930:

```
// C2930.cpp
// compile with: /c
template<class T>
class x{};
enum SomeEnum { x };   // C2930

class y{};
enum SomeEnum { y };
```

C2930 może również wystąpić, gdy za pomocą typów ogólnych:

```
// C2930c.cpp
// compile with: /clr /c
generic<class T>
ref struct GC {};
enum SomeEnum { GC };   // C2930

ref struct GC2 {};
enum SomeEnum2 { GC2 };
```