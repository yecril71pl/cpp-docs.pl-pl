---
title: Błąd krytyczny C1052 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 05/08/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1052
dev_langs:
- C++
helpviewer_keywords:
- C1052
ms.assetid: f2c09a2f-d3c1-4420-9501-ffcb65caf87b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d8d272b71a527763245ccf7c8d69bd11a915eab7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="fatal-error-c1052"></a>Błąd krytyczny C1052

> plik bazy danych programu "*filename*", został wygenerowany przez narzędzie konsolidacji z /DEBUG:fastlink; kompilator nie może aktualizować takich plików PDB; usuń go lub użyj elementu /Fd w celu określenia innej nazwy pliku PDB

Kompilator nie może zaktualizować tych samych plików bazy danych (PDB) programu, które są generowane przez konsolidator podczas [/DEBUG:fastlink](../../build/reference/debug-generate-debug-info.md) określono opcję. Zwykle pliki PDB wygenerowany przez kompilator i pliki PDB generowanych przez konsolidator mieć różne nazwy. Jednak jeśli zostało ono skonfigurowane do używania tych samych nazw, ten błąd może spowodować.

Aby rozwiązać ten problem, należy jawnie usunąć pliki PDB przed ponownie skompiluj lub można utworzyć różne nazwy plików PDB wygenerowany przez kompilator i generowanych przez konsolidator.

Aby określić nazwę pliku PDB wygenerowany przez kompilator w wierszu polecenia, użyj [/Fd](../../build/reference/fd-program-database-file-name.md) — opcja kompilatora. Aby określić nazwę pliku PDB wygenerowany przez kompilator w IDE, otwórz **strony właściwości** okna dialogowego projektu, a w **właściwości konfiguracji**, **C/C++**,  **Pliki wyjściowe** ustaw **nazwa pliku bazy danych programu** właściwości. Domyślnie ta właściwość jest `$(IntDir)vc$(PlatformToolsetVersion).pdb`.

Alternatywnie można ustawić nazwę pliku PDB generowanych przez konsolidator. Aby określić nazwę pliku PDB generowanych przez konsolidator w wierszu polecenia, użyj [/PDB](../../build/reference/pdb-use-program-database.md) — opcja konsolidatora. Aby określić nazwę pliku PDB generowanych przez konsolidator w IDE, otwórz **strony właściwości** okna dialogowego projektu, a w **właściwości konfiguracji**, **konsolidatora**,  **Debugowanie** ustaw **Generuj plik bazy danych programu** właściwości. Domyślnie wartość tej właściwości to `$(OutDir)$(TargetName).pdb`.
