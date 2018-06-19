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
ms.openlocfilehash: acf65c00c5c039769a05e009dcfe46ea42633ac4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33300361"
---
# <a name="linker-tools-warning-lnk4001"></a>Ostrzeżenie LNK4001 narzędzi konsolidatora
nie określono; plików obiektów użyto bibliotek  
  
 Konsolidator przekazano jeden lub więcej plików lib, ale żadne pliki .obj.  
  
 Ponieważ konsolidator nie będzie mógł uzyskać dostępu do informacji w pliku .lib, który jest w stanie uzyskać dostęp w pliku .obj, to ostrzeżenie oznacza, że zostaną jawnie określone inne opcje konsolidatora. Na przykład może być konieczne określenie [/maszyny](../../build/reference/machine-specify-target-platform.md), [/OUT](../../build/reference/out-output-file-name.md), lub [/Entry](../../build/reference/entry-entry-point-symbol.md) opcje.