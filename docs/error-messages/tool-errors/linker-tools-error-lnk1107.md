---
title: Błąd narzędzi konsolidatora LNK1107
ms.date: 11/04/2016
f1_keywords:
- LNK1107
helpviewer_keywords:
- LNK1107
ms.assetid: a37a893d-5efa-4eba-8f40-6c5518b4b9d0
ms.openlocfilehash: c75966d9c6c22f1bd2123fb30282bb2bed467130
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991029"
---
# <a name="linker-tools-error-lnk1107"></a>Błąd narzędzi konsolidatora LNK1107

nieprawidłowy lub uszkodzony plik: nie można odczytać w lokalizacji

Narzędzie nie może odczytać pliku. Utwórz ponownie plik.

LNK1107 może również wystąpić, jeśli spróbujesz przekazać moduł (. dll lub rozszerzenie modułu utworzonego za pomocą [/CLR: noAssembly](../../build/reference/clr-common-language-runtime-compilation.md) lub [/NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md)) do konsolidatora; Zamiast tego Przekaż plik. obj.

Jeśli kompilujesz następujący przykład:

```cpp
// LNK1107.cpp
// compile with: /clr /LD
public ref class MyClass {
public:
   void Test(){}
};
```

a następnie określ **link LNK1107. dll** w wierszu polecenia, uzyskasz LNK1107.  Aby rozwiązać ten problem, należy zamiast tego określić **link LNK1107. obj** .
