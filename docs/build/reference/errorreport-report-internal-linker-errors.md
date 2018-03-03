---
title: "-ERRORREPORT (zgłaszaj wewnętrzne błędy konsolidatora) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 12/28/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /ERRORREPORT
- VC.Project.VCLinkerTool.ErrorReporting
dev_langs:
- C++
helpviewer_keywords:
- /ERRORREPORT linker option
- ERRORREPORT linker option
- -ERRORREPORT linker option
ms.assetid: f5fab595-a2f1-4eb0-ab5c-1c0fbd3d8c28
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6ddf65ed2a17dae2d86b0dc4582f1d3158328898
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2018
---
# <a name="errorreport-report-internal-linker-errors"></a>/ERRORREPORT (Zgłaszaj wewnętrzne błędy konsolidatora)

> **/ errorreport:**[ **Brak** | **wiersza** | **kolejki** | **wysyłania** ]

## <a name="arguments"></a>Argumenty

**Brak**  
Raporty o błędach wewnętrznych kompilatora nie będą zbierane lub wysyłane do firmy Microsoft.

**wiersz**  
Monituje o wysłanie raportu po pojawieniu się błędu wewnętrznego kompilatora. **wiersz** jest domyślną kolekcją podczas kompilowania aplikacji w środowisku programistycznym.

**kolejki**  
Kolejkuje raport o błędzie. Podczas logowania się z uprawnieniami administratora, wyświetlane jest okno, aby wszelkie błędy mogą raportować od czasu ostatniego zalogowania w (zostanie nie się monit o wysłanie raportu błędów więcej niż raz na trzy dni). **kolejka** jest domyślną kolekcją podczas kompilowania aplikacji w wierszu polecenia.

**Wyślij**  
Automatycznie wysyła raporty błędów wewnętrznych kompilatora do firmy Microsoft, jeśli za pomocą ustawień usługi raportowania błędów systemu Windows jest włączone raportowanie.

## <a name="remarks"></a>Uwagi

**/Errorreport** opcja pozwala zapewnić wewnętrznych kompilatora informacje o błędzie (ICE) bezpośrednio do firmy Microsoft.

Opcja **/errorreport: Send** automatyczne wysyłanie informacji o błędach do firmy Microsoft, włączenie ustawienia usługi raportowania błędów systemu Windows.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Otwórz **właściwości konfiguracji** > **konsolidatora** > **zaawansowane** strony właściwości.

1. Modyfikowanie **raportowanie błędów** właściwości.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ErrorReporting%2A>.

## <a name="see-also"></a>Zobacz także

[/ errorreport (zgłaszaj wewnętrzne błędy kompilatora)](../../build/reference/errorreport-report-internal-compiler-errors.md)  
[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)  
[Opcje konsolidatora](../../build/reference/linker-options.md)  
