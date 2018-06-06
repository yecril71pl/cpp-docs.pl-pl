---
title: C2441 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2441
dev_langs:
- C++
helpviewer_keywords:
- C2441
ms.assetid: ffbd6573-777a-48dd-892f-5cf4a758dcab
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6d4224d9090f3ace43f61a10c599fafa78d21600
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34705283"
---
# <a name="compiler-error-c2441"></a>C2441 błąd kompilatora

> "*zmiennej*": symbol zadeklarowany z __declspec(proces) musi być stały w/CLR: pure tryb czysty

## <a name="remarks"></a>Uwagi

**/CLR: pure** i **/CLR: Safe** — opcje kompilatora są używane w programie Visual Studio 2015 i nieobsługiwane w programie Visual Studio 2017 r.

Domyślnie zmienne są właściwe dla domeny aplikacji w obszarze **/CLR: pure**. Oznaczone jako zmienną `__declspec(process)` w obszarze **/CLR: pure** jest podatne na błędy, jeśli zmodyfikowany w domenie jedną aplikację, a następnie odczytywane w innym.

W związku z tym kompilator wymusza na proces zmienne są `const` w obszarze **/CLR: pure**, wprowadzania je odczytać tylko we wszystkich domenach aplikacji.

Aby uzyskać więcej informacji, zobacz [procesu](../../cpp/process.md) i [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Przykład

Poniższy przykład generuje C2441.

```cpp
// C2441.cpp
// compile with: /clr:pure /c
__declspec(process) int i;   // C2441
__declspec(process) const int j = 0;   // OK
```