---
title: Ostrzeżenie LNK4001 narzędzi konsolidatora
ms.date: 11/04/2016
f1_keywords:
- LNK4001
helpviewer_keywords:
- LNK4001
ms.assetid: 0a8b1c3a-64ce-4311-b7c0-065995059246
ms.openlocfilehash: d9659b0cf372ff8ebc225b890fb68866872bb3d6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194411"
---
# <a name="linker-tools-warning-lnk4001"></a>Ostrzeżenie LNK4001 narzędzi konsolidatora

nie określono plików obiektów; używane biblioteki

Konsolidator przeszedł jeden lub więcej plików. lib, ale nie ma plików. obj.

Ponieważ konsolidator nie jest w stanie uzyskać dostępu do informacji w pliku lib, do którego może uzyskać dostęp w pliku. obj, to ostrzeżenie wskazuje, że trzeba będzie jawnie określić inne Opcje konsolidatora. Na przykład może być konieczne określenie opcji [/Machine](../../build/reference/machine-specify-target-platform.md), [/out](../../build/reference/out-output-file-name.md)lub [/entry](../../build/reference/entry-entry-point-symbol.md) .
