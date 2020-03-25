---
title: Ostrzeżenie LNK4217 narzędzi konsolidatora
ms.date: 07/23/2019
f1_keywords:
- LNK4217
helpviewer_keywords:
- LNK4217
ms.assetid: 280dc03e-5933-4e8d-bb8c-891fbe788738
ms.openlocfilehash: 1ce410312493b353bb68ea7264fce9cd6a394e0d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183114"
---
# <a name="linker-tools-warning-lnk4217"></a>Ostrzeżenie LNK4217 narzędzi konsolidatora

> Symbol "*symbol*" zdefiniowany w elemencie "*filename_1. obj*" został zaimportowany przez element "*filename_2. obj*" w funkcji "*Function*"

[__declspec (dllimport)](../../cpp/dllexport-dllimport.md) została określona dla symbolu, chociaż symbol jest zdefiniowany w pliku obiektu w tym samym obrazie. Usuń modyfikator `__declspec(dllimport)`, aby usunąć to ostrzeżenie.

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

a następnie

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

## <a name="see-also"></a>Zobacz też

[Ostrzeżenie narzędzi konsolidatora lnk4049 narzędzi konsolidatora](linker-tools-warning-lnk4049.md) \
[Ostrzeżenie narzędzi konsolidatora LNK4286](linker-tools-warning-lnk4286.md) \
[dllexport, dllimport](../../cpp/dllexport-dllimport.md)
