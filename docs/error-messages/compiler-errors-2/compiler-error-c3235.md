---
title: Błąd kompilatora C3235 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3235
dev_langs:
- C++
helpviewer_keywords:
- C3235
ms.assetid: 0554d6c7-e1dc-4c99-8934-cbcf491c8203
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d156a9c1a6cda2ad8bb15e31034927b39a1a82e8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46027872"
---
# <a name="compiler-error-c3235"></a>Błąd kompilatora C3235

"specjalizacja": jawna lub częściowa specjalizacja klasy generycznej jest niedozwolona.

Nie można używać klas ogólnych dla jawne lub częściowe specjalizacje.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3235.

```
// C3235.cpp
// compile with: /clr
generic<class T>
public ref class C {};

generic<>
public ref class C<int> {};   // C3235 Remove this specialization to resolve this error.
```