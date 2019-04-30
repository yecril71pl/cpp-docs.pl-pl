---
title: Błąd kompilatora C3194
ms.date: 11/04/2016
f1_keywords:
- C3194
helpviewer_keywords:
- C3194
ms.assetid: 49d3ffc6-eff6-4b46-865b-18811692a8bb
ms.openlocfilehash: 181a18dde45c3363f1f77bc0cbbd5b0ffca3e898
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397461"
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