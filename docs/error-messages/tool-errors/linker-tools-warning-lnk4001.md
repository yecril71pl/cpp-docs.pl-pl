---
title: Ostrzeżenie LNK4001 narzędzi konsolidatora
ms.date: 11/04/2016
f1_keywords:
- LNK4001
helpviewer_keywords:
- LNK4001
ms.assetid: 0a8b1c3a-64ce-4311-b7c0-065995059246
ms.openlocfilehash: 75ca9ec92bbba1c15efc11a731b3894ea03e33dd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62298792"
---
# <a name="linker-tools-warning-lnk4001"></a>Ostrzeżenie LNK4001 narzędzi konsolidatora

nie określono; plików obiektów użyto bibliotek

Konsolidator przekazano co najmniej jeden plik .lib, ale nie pliki .obj.

Ponieważ konsolidator nie jest w stanie uzyskać dostępu do informacji w pliku .lib, który jest w stanie uzyskać dostęp w pliku .obj, to ostrzeżenie wskazuje, że musisz jawnie określić inne opcje konsolidatora. Na przykład może być konieczne określenie [/MACHINE](../../build/reference/machine-specify-target-platform.md), [/OUT](../../build/reference/out-output-file-name.md), lub [/Entry](../../build/reference/entry-entry-point-symbol.md) opcje.