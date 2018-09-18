---
title: Błąd kompilatora C3194 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3194
dev_langs:
- C++
helpviewer_keywords:
- C3194
ms.assetid: 49d3ffc6-eff6-4b46-865b-18811692a8bb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 923e4d5535a1be4f4c8a3f7b60730eb6a656ac33
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46077103"
---
# <a name="compiler-error-c3194"></a>Błąd kompilatora C3194

"członek": typ wartościowy nie może mieć operatora przypisania

Specjalne funkcje Członkowskie, które wymagają automatyczne wywołanie przez kompilator, takich jak Konstruktor kopiujący lub kopia operatora przypisania nie są obsługiwane w klasie wartości.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3194.

```
// C3194.cpp
// compile with: /clr /c
value struct MyStruct {
   MyStruct& operator= (const MyStruct& i) { return *this; }   // C3194
};

ref struct MyStruct2 {
   MyStruct2% operator= (const MyStruct2% i) { return *this; }   // OK
};
```