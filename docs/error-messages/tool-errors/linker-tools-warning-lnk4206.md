---
title: Ostrzeżenie LNK4206 narzędzi konsolidatora | Dokumentacja firmy Microsoft
ms.date: 12/05/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4206
dev_langs:
- C++
helpviewer_keywords:
- LNK4206
ms.assetid: 6c108e33-00cf-4c5a-830d-d65d470930a7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f0cb74776f307affb0455d972e27e594e6d06294
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-warning-lnk4206"></a>Ostrzeżenie LNK4206 narzędzi konsolidatora

> informacje o wstępnie skompilowanym typie nie można odnaleźć; "*filename*" nie połączone lub zastąpione; Konsolidacja obiekt zostanie skonsolidowany bez informacji debugowania

*Filename* pliku obiektu, skompilowanego za pomocą [/Yc](../../build/reference/yc-create-precompiled-header-file.md), albo nie został określony w poleceniu łącze lub została zastąpiona.

Typowy scenariusz dla to ostrzeżenie jest podczas .obj, który został skompilowany z /Yc znajduje się w bibliotece oraz gdzie nie ma żadnych odwołań do symboli do tego .obj w kodzie.  W takim przypadku konsolidator zostanie nie używać (lub nawet) pliku obj.  W takiej sytuacji należy ponownie skompilować kod i użyć [/Yl](../../build/reference/yl-inject-pch-reference-for-debug-library.md) dla skompilowanych przy użyciu obiektów [/Yu](../../build/reference/yu-use-precompiled-header-file.md).