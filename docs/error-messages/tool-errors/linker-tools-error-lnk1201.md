---
title: Błąd narzędzi konsolidatora LNK1201 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1201
dev_langs:
- C++
helpviewer_keywords:
- LNK1201
ms.assetid: 64c3f496-a428-4b54-981e-faa82ef9c8a1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4c133748f95846160e1387e31e023d9ce459b281
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46055276"
---
# <a name="linker-tools-error-lnk1201"></a>Błąd narzędzi konsolidatora LNK1201

Wystąpił błąd podczas zapisywania do bazy danych programu 'NazwaPliku'; Sprawdź, czy brak miejsca na dysku, nieprawidłowa ścieżka lub niewystarczające uprawnienia

ŁĄCZE nie można zapisać w bazie danych programu (PDB) dla pliku wyjściowego.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać problem, sprawdzając następujące możliwe przyczyny

1. Plik jest uszkodzony. Usuń plik PDB i połącz ponownie.

1. Nie ma wystarczającej ilości miejsca na dysku do zapisania pliku.

1. Dysk nie jest dostępna, prawdopodobnie z powodu problemu sieciowego.

1. Debuger jest aktywny w programie, w którym próbujesz się połączyć.

1. Brak miejsca na stosie.  Zobacz [C1060](../../error-messages/compiler-errors-1/fatal-error-c1060.md) Aby uzyskać więcej informacji.