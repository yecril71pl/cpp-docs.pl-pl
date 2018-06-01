---
title: C2812 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2812
dev_langs:
- C++
helpviewer_keywords:
- C2812
ms.assetid: 22aadb8c-7232-489d-a3ad-60662dda30a8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0c5469e4f7be3c164cc63fa30f5069009846be48
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34705026"
---
# <a name="compiler-error-c2812"></a>C2812 błąd kompilatora

> \#Import nie jest obsługiwany z/CLR: pure i/CLR: Safe

## <a name="remarks"></a>Uwagi

**/CLR: pure** i **/CLR: Safe** — opcje kompilatora są używane w programie Visual Studio 2015 i nieobsługiwane w programie Visual Studio 2017 r.

[#import — dyrektywa](../../preprocessor/hash-import-directive-cpp.md) nie jest obsługiwany z **/CLR: pure** i **/CLR: Safe** ponieważ `#import` wymaga użycia bibliotek obsługi macierzystego kompilatora.

## <a name="example"></a>Przykład

Poniższy przykład generuje C2812.

```cpp
// C2812.cpp
// compile with: /clr:pure /c
#import "importlib.tlb"   // C2812
```