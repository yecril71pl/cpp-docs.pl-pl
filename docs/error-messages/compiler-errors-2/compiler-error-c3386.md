---
title: Błąd kompilatora C3386
ms.date: 11/04/2016
f1_keywords:
- C3386
helpviewer_keywords:
- C3386
ms.assetid: 93fa8c33-0f10-402b-8eec-b0a217a1f8dc
ms.openlocfilehash: efe882db447b9ebc69d02e3b10d9e484a3cfd8a8
ms.sourcegitcommit: f2a135d69a2a8ef1777da60c53d58fe06980c997
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/03/2020
ms.locfileid: "87520451"
---
# <a name="compiler-error-c3386"></a>Błąd kompilatora C3386

> "*type-name*": `__declspec(dllexport)` / `__declspec(dllimport)` nie można zastosować do typu zarządzanego lub WinRT

[`dllimport`](../../cpp/dllexport-dllimport.md) [`dllexport`](../../cpp/dllexport-dllimport.md) **`__declspec`** Modyfikatory i nie są prawidłowe dla typu zarządzanego lub środowisko wykonawcze systemu Windows.

Poniższy przykład generuje C3386 i pokazuje, jak to naprawić:

```cpp
// C3386.cpp
// compile with: /clr /c
ref class __declspec(dllimport) X1 {   // C3386
// try the following line instead
// ref class X1 {
};
```
