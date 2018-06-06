---
title: C4936 ostrzeżenia kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4936
dev_langs:
- C++
helpviewer_keywords:
- C4936
ms.assetid: 6676de35-bf1b-4d0b-a70f-b5734130336c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0be4a565dd251da77174c401c23b8ed8bfc531b0
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34703942"
---
# <a name="compiler-warning-c4936"></a>C4936 ostrzeżenia kompilatora

> Ta deklaracja __declspec jest obsługiwana tylko w przypadku, gdy skompilowano z opcją/CLR lub/CLR: pure

## <a name="remarks"></a>Uwagi

**/CLR: pure** — opcja kompilatora jest przestarzałe w programie Visual Studio 2015 i nieobsługiwane w programie Visual Studio 2017 r.

A `__declspec` modyfikator użyto ale `__declspec` modyfikator obowiązuje tylko, gdy skompilowano z jednym z [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) opcje.

Aby uzyskać więcej informacji, zobacz [elementu appdomain](../../cpp/appdomain.md) i [procesu](../../cpp/process.md).

C4936 jest zawsze wystawione jako błąd.  Możesz wyłączyć C4936 z [ostrzeżenie](../../preprocessor/warning.md) pragma.

## <a name="example"></a>Przykład

Poniższy przykład generuje C4936:

```cpp
// C4936.cpp
// compile with: /c
// #pragma warning (disable : 4936)
__declspec(process) int i;   // C4936
__declspec(appdomain) int j;   // C4936
```