---
title: Błąd kompilatora C3862
ms.date: 11/04/2016
f1_keywords:
- C3862
helpviewer_keywords:
- C3862
ms.assetid: ba547366-4189-4077-8c00-ab45e08a9533
ms.openlocfilehash: 0b9c1e1213949d7d700094caa6687232df881ce6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165486"
---
# <a name="compiler-error-c3862"></a>Błąd kompilatora C3862

> "*Function*": nie można skompilować niezarządzanej funkcji z/CLR: Pure lub/CLR: Safe

## <a name="remarks"></a>Uwagi

**/CLR: Pure** i **/CLR:** opcje kompilatora bezpiecznego są przestarzałe w programie Visual Studio 2015 i nieobsługiwane w programie Visual Studio 2017.

Kompilacja z **/CLR: Pure** lub **/CLR: Safe** spowoduje wygenerowanie obrazu tylko MSIL, obrazu bez kodu natywnego (niezarządzanego).  W związku z tym nie można używać dyrektywy pragma `unmanaged` w przypadku kompilacji z **opcją/CLR: Pure** lub **/CLR: Safe** .

Aby uzyskać więcej informacji, zobacz [/CLR (Kompilacja środowiska uruchomieniowego języka wspólnego)](../../build/reference/clr-common-language-runtime-compilation.md) i [zarządzana, niezarządzana](../../preprocessor/managed-unmanaged.md).

## <a name="example"></a>Przykład

Poniższy przykład generuje C3862:

```cpp
// C3862.cpp
// compile with: /clr:pure /c
#pragma unmanaged
void f() {}   // C3862
```
