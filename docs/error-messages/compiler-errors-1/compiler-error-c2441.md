---
title: Błąd kompilatora C2441
ms.date: 11/04/2016
f1_keywords:
- C2441
helpviewer_keywords:
- C2441
ms.assetid: ffbd6573-777a-48dd-892f-5cf4a758dcab
ms.openlocfilehash: 4e5d5335717ec77c61069ad08e209f9e1851dc2f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80205312"
---
# <a name="compiler-error-c2441"></a>Błąd kompilatora C2441

> "*zmienna*": symbol zadeklarowany z __declspec (Process) musi być stały w/CLR: Pure Mode

## <a name="remarks"></a>Uwagi

**/CLR: Pure** i **/CLR:** opcje kompilatora bezpiecznego są przestarzałe w programie Visual Studio 2015 i nieobsługiwane w programie Visual Studio 2017.

Domyślnie zmienne są dla domeny aplikacji w ramach opcji **/CLR: Pure**. Zmienna oznaczona `__declspec(process)` w opcji **/CLR: Pure** jest podatna na błędy w przypadku zmodyfikowania w jednej domenie aplikacji i odczytania w innej.

W związku z tym kompilator wymusza na zmienne procesów `const` w obszarze **/CLR: Pure**, co sprawia, że są one odczytane tylko we wszystkich domenach aplikacji.

Aby uzyskać więcej informacji, zobacz [proces](../../cpp/process.md) i [/CLR (Kompilacja środowiska uruchomieniowego języka wspólnego)](../../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Przykład

Poniższy przykład generuje C2441.

```cpp
// C2441.cpp
// compile with: /clr:pure /c
__declspec(process) int i;   // C2441
__declspec(process) const int j = 0;   // OK
```
