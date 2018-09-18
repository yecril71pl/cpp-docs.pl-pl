---
title: Ostrzeżenie LNK4001 narzędzi konsolidatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4001
dev_langs:
- C++
helpviewer_keywords:
- LNK4001
ms.assetid: 0a8b1c3a-64ce-4311-b7c0-065995059246
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f684e85233c4df777a53f03f07936137c425946e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46070422"
---
# <a name="linker-tools-warning-lnk4001"></a>Ostrzeżenie LNK4001 narzędzi konsolidatora

nie określono; plików obiektów użyto bibliotek

Konsolidator przekazano co najmniej jeden plik .lib, ale nie pliki .obj.

Ponieważ konsolidator nie jest w stanie uzyskać dostępu do informacji w pliku .lib, który jest w stanie uzyskać dostęp w pliku .obj, to ostrzeżenie wskazuje, że musisz jawnie określić inne opcje konsolidatora. Na przykład może być konieczne określenie [/MACHINE](../../build/reference/machine-specify-target-platform.md), [/OUT](../../build/reference/out-output-file-name.md), lub [/Entry](../../build/reference/entry-entry-point-symbol.md) opcje.