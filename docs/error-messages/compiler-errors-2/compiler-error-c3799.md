---
title: Błąd kompilatora C3799 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3799
dev_langs:
- C++
helpviewer_keywords:
- C3799
ms.assetid: 336a2811-9370-4e6e-b03b-325bda470805
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1022a2a1f5c5bb6279fc4af0acedbf28d7723aa6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46105339"
---
# <a name="compiler-error-c3799"></a>Błąd kompilatora C3799

indeksowana właściwość nie może mieć pustą listę parametrów

Właściwość indeksowana zadeklarowano niepoprawnie. Aby uzyskać więcej informacji, zobacz [porady: użycie właściwości w języku C + +/ interfejsu wiersza polecenia](../../dotnet/how-to-use-properties-in-cpp-cli.md).

## <a name="example"></a>Przykład

Poniższy przykład generuje C3799 i pokazuje, jak go naprawić.

```cpp
// C3799.cpp
// compile with: /clr /c
ref struct C {
   property int default[] {   // C3799
   // try the following line instead
   // property int default[int] {
      int get(int index) { return 0; }
      void set(int index, int value) {}
   }
};
```