---
title: Błąd narzędzi konsolidatora LNK1201
ms.date: 11/04/2016
f1_keywords:
- LNK1201
helpviewer_keywords:
- LNK1201
ms.assetid: 64c3f496-a428-4b54-981e-faa82ef9c8a1
ms.openlocfilehash: c5cbb9a7159a976ad0f96f46462669cff7b19f26
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62213268"
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