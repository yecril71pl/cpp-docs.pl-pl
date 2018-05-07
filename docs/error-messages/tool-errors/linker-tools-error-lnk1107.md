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
ms.openlocfilehash: fee2105cb0c12287cd2b47636f0e47011854a608
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-error-lnk1107"></a>Błąd narzędzi konsolidatora LNK1107
nieprawidłowy lub uszkodzony plik: nie można odczytać w lokalizacji  
  
 Narzędzie nie może odczytać pliku. Utwórz ponownie plik.  
  
 LNK1107 mógł także wystąpić, jeśli próba przekazania modułu (rozszerzenie .dll lub moduł .netmodule utworzone za pomocą [/clr:noAssembly](../../build/reference/clr-common-language-runtime-compilation.md) lub [/noassembly](../../build/reference/noassembly-create-a-msil-module.md)) do konsolidatora; przekazać plik .obj zamiast tego.  
  
 Jeśli kompilacja następującym przykładowym:  
  
```  
// LNK1107.cpp  
// compile with: /clr /LD  
public ref class MyClass {  
public:  
   void Test(){}  
};  
```  
  
 a następnie określ **link LNK1107.dll** w wierszu polecenia, zostanie wyświetlony LNK1107.  Aby rozwiązać problem, określ **link LNK1107.obj** zamiast tego.