---
title: Błąd kompilatora C3370
ms.date: 11/04/2016
f1_keywords:
- C3370
helpviewer_keywords:
- C3370
ms.assetid: ee6d4c85-78fc-42b2-836e-5cc491a3b2ba
ms.openlocfilehash: 0dbc95fcb26354b0f963d1844ddd6a43783c532a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62300612"
---
# <a name="compiler-error-c3370"></a>Błąd kompilatora C3370

"idl_module name": idl_module jeszcze nie jest zdefiniowana

Przed użyciem [idl_module](../../windows/idl-module.md) do określonego punktu wejścia w bibliotece DLL, należy najpierw użyć `idl_module` do określenia nazwy biblioteki DLL.

Poniższy przykład spowoduje wygenerowanie C3370:

```
// C3370.cpp
[module(name=MyLibrary)];
// uncomment the following line to resolve the error
// [idl_module(name="name1", dllname=x.dll)];
[idl_module(name="name1"), entry(100)] // C3370
int f1();

int main()
{
}
```