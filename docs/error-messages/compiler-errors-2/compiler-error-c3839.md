---
title: Błąd kompilatora C3839 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3839
dev_langs:
- C++
helpviewer_keywords:
- C3839
ms.assetid: 0957faff-1e9f-439b-876b-85bd8d2c578d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 597d02ff347d399833e2376743b50f65e7674a18
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46092911"
---
# <a name="compiler-error-c3839"></a>Błąd kompilatora C3839

Nie można zmienić wyrównania w zarządzanej lub typu WinRT

Wyrównanie zmiennych w zarządzanych lub typów środowiska wykonawczego Windows jest kontrolowany przez CLR lub Windows Runtime i nie można modyfikować za pomocą [wyrównać](../../cpp/align-cpp.md).

Poniższy przykład spowoduje wygenerowanie C3839:

```
// C3839a.cpp
// compile with: /clr
ref class C
{
public:
   __declspec(align(32)) int m_j; // C3839
};

int main()
{
}
```