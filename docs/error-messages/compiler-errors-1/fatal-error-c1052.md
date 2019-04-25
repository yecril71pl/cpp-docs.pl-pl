---
title: Błąd krytyczny C1052
ms.date: 05/08/2017
f1_keywords:
- C1052
helpviewer_keywords:
- C1052
ms.assetid: f2c09a2f-d3c1-4420-9501-ffcb65caf87b
ms.openlocfilehash: b381cc3cfe27d4c4a9d744a6b854a0e43727fe71
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62243688"
---
# <a name="fatal-error-c1052"></a>Błąd krytyczny C1052

> plik bazy danych programu "*filename*", został wygenerowany przez konsolidator przy użyciu fastlink; kompilator nie może aktualizować takich plików PDB; usuń go lub użyj elementu /Fd w celu określenia innej nazwy pliku PDB

Kompilator nie może zaktualizować tych samych plików bazy danych (PDB) programu, które są generowane przez konsolidator przy [fastlink](../../build/reference/debug-generate-debug-info.md) określono opcję. Zwykle w pliki PDB generowanych przez kompilator i pliki PDB generowanych przez konsolidator mieć różne nazwy. Jednak jeśli zostało ono skonfigurowane do użycia takich samych nazwach może spowodować błąd.

Aby rozwiązać ten problem, możesz jawnie usunąć pliki PDB zanim ponownie skompiluj lub można utworzyć różne nazwy plików PDB generowanych przez kompilator i generowanych przez konsolidator.

Aby określić nazwę pliku PDB generowanych przez kompilator w wierszu polecenia, użyj [/Fd](../../build/reference/fd-program-database-file-name.md) — opcja kompilatora. Aby określić nazwę pliku PDB generowanych przez kompilator w IDE, otwórz **stron właściwości** okno dialogowe dla projektu, a w **właściwości konfiguracji**, **C/C++**,  **Pliki wyjściowe** ustaw **nazwa pliku bazy danych programu** właściwości. Domyślnie ta właściwość jest `$(IntDir)vc$(PlatformToolsetVersion).pdb`.

Alternatywnie można ustawić nazwę pliku PDB generowanych przez konsolidator. Aby określić nazwę pliku PDB generowanych przez konsolidator, w wierszu polecenia, użyj [/PDB](../../build/reference/pdb-use-program-database.md) — opcja konsolidatora. Aby określić nazwę pliku PDB generowanych przez konsolidator w IDE, otwórz **stron właściwości** okno dialogowe dla projektu, a w **właściwości konfiguracji**, **konsolidatora**,  **Debugowanie** ustaw **Generuj plik bazy danych programu** właściwości. Domyślnie wartość tej właściwości to `$(OutDir)$(TargetName).pdb`.
