---
title: Ostrzeżenie LNK4217 narzędzi konsolidatora
ms.date: 07/23/2019
f1_keywords:
- LNK4217
helpviewer_keywords:
- LNK4217
ms.assetid: 280dc03e-5933-4e8d-bb8c-891fbe788738
ms.openlocfilehash: 1301dd53f71c616d7b7af346923a54c42903c9fd
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68450863"
---
# <a name="linker-tools-warning-lnk4217"></a>Ostrzeżenie LNK4217 narzędzi konsolidatora

> Symbol "*symbol*" zdefiniowany w elemencie "*filename_1. obj*" został zaimportowany przez element "*filename_2. obj*" w funkcji "*Function*"

określono [__declspec (dllimport)](../../cpp/dllexport-dllimport.md) dla symbolu, chociaż symbol jest zdefiniowany w pliku obiektu w tym samym obrazie. Usuń modyfikator `__declspec(dllimport)` , aby rozwiązać to ostrzeżenie.

## <a name="remarks"></a>Uwagi

*symbol* jest nazwą symbolu, który jest zdefiniowany w obrazie. *Funkcja* jest funkcją, która importuje symbol.

To ostrzeżenie nie pojawia się podczas kompilowania przy użyciu opcji [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) .

LNK4217 narzędzi KONSOLIDATORA może również wystąpić, jeśli spróbujesz połączyć dwa moduły jednocześnie, gdy zamiast tego należy skompilować drugi moduł z biblioteką importu pierwszego modułu.

```cpp
// main.cpp
__declspec(dllimport) void func();

int main()
{
    func();
    return 0;
}

```

A następnie

```cpp
// tt.cpp
// compile with: /c
void func() {}
```

Próba skompilowania tych dwóch modułów, jak pokazano w tym miejscu, spowoduje LNK4217 narzędzi KONSOLIDATORA:

```cmd
cl.exe /c main.cpp tt.cpp
link.exe main.obj tt.obj
```

Aby naprawić ten błąd, po skompilowaniu dwóch plików, należy przekazać TT. obj do lib. exe, aby utworzyć plik. lib, a następnie połączyć Main. obj z TT. lib, jak pokazano poniżej:

```cmd
cl.exe /c main.cpp tt.cpp
lib.exe tt.obj /export:func /def
link.exe main.obj tt.lib
```

## <a name="see-also"></a>Zobacz także

[Linker Tools Warning LNK4049](linker-tools-warning-lnk4049.md) \
[Ostrzeżenie narzędzi konsolidatora LNK4286](linker-tools-warning-lnk4286.md) \
[dllexport, dllimport](../../cpp/dllexport-dllimport.md)