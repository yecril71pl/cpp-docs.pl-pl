---
title: Błąd kompilatora C2441
ms.date: 11/04/2016
f1_keywords:
- C2441
helpviewer_keywords:
- C2441
ms.assetid: ffbd6573-777a-48dd-892f-5cf4a758dcab
ms.openlocfilehash: 7fcf333f62253eb676c0f0ada1c927ab962ae1ca
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62338925"
---
# <a name="compiler-error-c2441"></a>Błąd kompilatora C2441

> "*zmiennej*": symbol zadeklarowany z __declspec(proces) musi być stały w/CLR: pure tryb czysty

## <a name="remarks"></a>Uwagi

**/CLR: pure** i **/CLR: Safe** opcje kompilatora są przestarzałe w programie Visual Studio 2015 i obsługiwane w programie Visual Studio 2017.

Domyślnie są zmienne dla domeny aplikacji, w obszarze **/CLR: pure**. Oznaczone jako zmienną `__declspec(process)` w obszarze **/CLR: pure** jest podatne na błędy, jeśli w jednej aplikacji domeny modyfikowane i odczytywane w innym.

W związku z tym, kompilator wymusza na proces zmienne być `const` w obszarze **/CLR: pure**, podejmowanie je odczytać tylko we wszystkich domenach aplikacji.

Aby uzyskać więcej informacji, zobacz [procesu](../../cpp/process.md) i [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C2441.

```cpp
// C2441.cpp
// compile with: /clr:pure /c
__declspec(process) int i;   // C2441
__declspec(process) const int j = 0;   // OK
```