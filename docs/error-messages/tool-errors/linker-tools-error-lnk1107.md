---
title: Błąd narzędzi konsolidatora LNK1107 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1107
dev_langs:
- C++
helpviewer_keywords:
- LNK1107
ms.assetid: a37a893d-5efa-4eba-8f40-6c5518b4b9d0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 73a1643d10ea9adc6ac6979eb2de023593ba8d01
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46060710"
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