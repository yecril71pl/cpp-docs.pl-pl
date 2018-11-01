---
title: Błąd narzędzi konsolidatora LNK1107
ms.date: 11/04/2016
f1_keywords:
- LNK1107
helpviewer_keywords:
- LNK1107
ms.assetid: a37a893d-5efa-4eba-8f40-6c5518b4b9d0
ms.openlocfilehash: 68048d9f824283d002a4ea8b64d88f37bbeefc48
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50646566"
---
# <a name="linker-tools-error-lnk1107"></a>Błąd narzędzi konsolidatora LNK1107

nieprawidłowy lub uszkodzony plik: nie można odczytać lokalizacji

Narzędzie nie może odczytać pliku. Utwórz ponownie plik.

LNK1107 mógł także wystąpić, Jeśli spróbujesz przekazać modułu (rozszerzenie .dll lub moduł .netmodule utworzone za pomocą [/clr:noAssembly](../../build/reference/clr-common-language-runtime-compilation.md) lub [/noassembly](../../build/reference/noassembly-create-a-msil-module.md)) do konsolidatora; Przekaż plik .obj zamiast tego.

Jeśli kompilujesz z poniższego przykładu:

```
// LNK1107.cpp
// compile with: /clr /LD
public ref class MyClass {
public:
   void Test(){}
};
```

a następnie określ **link LNK1107.dll** w wierszu polecenia zostanie wyświetlony LNK1107.  Aby naprawić błąd, należy określić **link LNK1107.obj** zamiast tego.