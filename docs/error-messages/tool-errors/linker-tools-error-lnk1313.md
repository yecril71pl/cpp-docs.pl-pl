---
title: Błąd narzędzi konsolidatora LNK1313 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1313
dev_langs:
- C++
helpviewer_keywords:
- LNK1313
ms.assetid: 5df0b72e-bb3f-428c-8d84-6084238f9827
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d6a896c8ba012c69755c5292475b2d155ad92066
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34705091"
---
# <a name="linker-tools-error-lnk1313"></a>Błąd narzędzi konsolidatora LNK1313

> Moduł IJW lub natywne wykrył; Nie można połączyć z modułami czysty

## <a name="remarks"></a>Uwagi

Bieżącej wersji programu Visual C++ nie obsługuje łączenia plików .obj zarządzane lub natywne native lub mieszane z plikami .obj skompilowane z **/CLR: pure**.

**/CLR: pure** — opcja kompilatora jest przestarzałe w programie Visual Studio 2015 i nieobsługiwane w programie Visual Studio 2017 r.

## <a name="example"></a>Przykład

```cpp
// LNK1313.cpp
// compile with: /c /clr:pure
// a pure module
int main() {}
```

## <a name="example"></a>Przykład

```cpp
// LNK1313_b.cpp
// compile with: /c /clr
// an IJW module
void test(){}
```

## <a name="example"></a>Przykład

Poniższy przykład wygeneruje LNK1313.

```cpp
// LNK1313_c.cpp
// compile with: /link LNK1313.obj LNK1313_b.obj
// LNK1313 warning expected
```