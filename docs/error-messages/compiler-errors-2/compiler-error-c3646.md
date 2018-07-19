---
title: Błąd kompilatora C3646 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 06/14/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3646
dev_langs:
- C++
helpviewer_keywords:
- C3646
ms.assetid: 4391ead2-9637-4ca3-aeda-5a991b18d66d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c038520c1a35fa5264e1e98b074687efb336d028
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "35658614"
---
# <a name="compiler-error-c3646"></a>Błąd kompilatora C3646

> "specyfikatora": nieznany specyfikator przesłonięcia

## <a name="remarks"></a>Uwagi

Tokenu można znaleźć kompilatora w miejscu, w którym ją Oczekiwano znalezienia specyfikator przesłonięcia, ale token nie został rozpoznany przez kompilator.

Na przykład jeśli rozpoznane *specyfikator* jest **_NOEXCEPT**, zastąp ją ze słowem kluczowym **noexcept**.

Aby uzyskać więcej informacji, zobacz [zastąpienie specyfikatorów](../../windows/override-specifiers-cpp-component-extensions.md).

## <a name="example"></a>Przykład

Poniższy przykład generuje C3646 i pokazuje sposób, aby rozwiązać ten problem:

```cpp
// C3646.cpp
// compile with: /clr /c
ref class C {
   void f() unknown;   // C3646
   // try the following line instead
   // virtual void f() abstract;
};
```