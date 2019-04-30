---
title: Błąd kompilatora C3839
ms.date: 11/04/2016
f1_keywords:
- C3839
helpviewer_keywords:
- C3839
ms.assetid: 0957faff-1e9f-439b-876b-85bd8d2c578d
ms.openlocfilehash: b8382213fbe7cc953dafd9610bfb993ba7837947
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400074"
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