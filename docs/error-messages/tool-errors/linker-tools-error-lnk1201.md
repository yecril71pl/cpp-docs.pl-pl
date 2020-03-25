---
title: Błąd narzędzi konsolidatora LNK1201
ms.date: 11/04/2016
f1_keywords:
- LNK1201
helpviewer_keywords:
- LNK1201
ms.assetid: 64c3f496-a428-4b54-981e-faa82ef9c8a1
ms.openlocfilehash: 8d02743333c02c7cdff3b75e4a16bfecda442fa9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195113"
---
# <a name="linker-tools-error-lnk1201"></a>Błąd narzędzi konsolidatora LNK1201

Wystąpił błąd podczas zapisywania do bazy danych programu "filename"; Sprawdź, czy jest za mało miejsca na dysku, nieprawidłowa ścieżka lub niewystarczające uprawnienia

LINK nie może zapisać do bazy danych programu (PDB) dla pliku wyjściowego.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać ten problem, sprawdzając następujące możliwe przyczyny

1. Plik jest uszkodzony. Usuń plik PDB i ponownie połącz.

1. Za mało miejsca na dysku, aby zapisać plik.

1. Stacja dysków jest niedostępna, prawdopodobnie z powodu problemu z siecią.

1. Debuger jest aktywny w programie, który próbujesz połączyć.

1. Za mało miejsca na stercie.  Aby uzyskać więcej informacji, zobacz [C1060](../../error-messages/compiler-errors-1/fatal-error-c1060.md) .
