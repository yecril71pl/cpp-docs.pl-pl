---
title: Kompilator ostrzeżenie (poziom 1) C4160 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4160
dev_langs:
- C++
helpviewer_keywords:
- C4160
ms.assetid: a9610cb7-cac4-4a74-8b4e-049030ebb92b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c62bf021065870f2ddd64cd7ee08cc00504cf7bd
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43219678"
---
# <a name="compiler-warning-level-1-c4160"></a>Kompilator ostrzeżenie (poziom 1) C4160

> #<a name="pragma-pop--did-not-find-previously-pushed-identifier-identifier"></a>pragma (POP, Point,...): nie znaleziono poprzednio włożonego identyfikatora "*identyfikator*"

## <a name="remarks"></a>Uwagi

Pragma instrukcji w kodzie źródłowym próbuje pop identyfikator, który nie został wypchnięty. Aby uniknąć tego ostrzeżenia, upewnij się, prawidłowo przypisany identyfikator są zdjęte ze stosu.

## <a name="example"></a>Przykład

Poniższy przykład generuje C4160 i pokazuje, jak go naprawić:

```cpp
// C4160.cpp
// compile with: /W1
#pragma pack(push)

#pragma pack(pop, id)   // C4160
// use identifier when pushing to resolve the warning
// #pragma pack(push, id)

int main() {
}
```