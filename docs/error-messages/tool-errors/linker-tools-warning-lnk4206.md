---
title: Ostrzeżenie LNK4206 narzędzi konsolidatora
ms.date: 12/05/2017
f1_keywords:
- LNK4206
helpviewer_keywords:
- LNK4206
ms.assetid: 6c108e33-00cf-4c5a-830d-d65d470930a7
ms.openlocfilehash: dc81df89609f59834c8a3271dd64f3b99b281f90
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62395082"
---
# <a name="linker-tools-warning-lnk4206"></a>Ostrzeżenie LNK4206 narzędzi konsolidatora

> informacje o wstępnie skompilowanym typie nie znaleziono; "*filename*" nie połączone lub zastąpione; skonsolidowany obiektu bez informacji debugowania

*Filename* skompilowane przy użyciu pliku obiektu [/Yc](../../build/reference/yc-create-precompiled-header-file.md), albo nie został określony w poleceniu łącze lub została zastąpiona.

Typowy scenariusz w przypadku tego ostrzeżenia jest .obj, który został skompilowany z parametrem/yc znajduje się w bibliotece i których nie odwołania do symboli do tego .obj w kodzie.  W takim przypadku konsolidator będzie nie używać (lub nawet zobaczysz) pliku .obj.  W takiej sytuacji należy ponownie skompilować kod i użyj [/Yl](../../build/reference/yl-inject-pch-reference-for-debug-library.md) dla obiektów skompilowanych przy użyciu [/Yu](../../build/reference/yu-use-precompiled-header-file.md).