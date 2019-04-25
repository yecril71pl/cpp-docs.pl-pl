---
title: /ERRORREPORT (Zgłaszaj wewnętrzne błędy konsolidatora)
ms.date: 12/28/2017
f1_keywords:
- /ERRORREPORT
- VC.Project.VCLinkerTool.ErrorReporting
helpviewer_keywords:
- /ERRORREPORT linker option
- ERRORREPORT linker option
- -ERRORREPORT linker option
ms.assetid: f5fab595-a2f1-4eb0-ab5c-1c0fbd3d8c28
ms.openlocfilehash: 26cc157cb7247a3a2ea7c10b415df1160540c9ad
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62271732"
---
# <a name="errorreport-report-internal-linker-errors"></a>/ERRORREPORT (Zgłaszaj wewnętrzne błędy konsolidatora)

> **/ errorreport:**[ **Brak** | **wiersza** | **kolejki** | **wysyłania** ]

## <a name="arguments"></a>Argumenty

**Brak**<br/>
Raporty o błędach wewnętrznych kompilatora nie będą zbierane ani wysyłane do firmy Microsoft.

**wiersz**<br/>
Monituje o wysłanie raportu po pojawieniu się błędu wewnętrznego kompilatora. **wiersz** jest domyślną kolekcją podczas kompilowania aplikacji w środowisku programistycznym.

**kolejki**<br/>
Kolejkuje raport o błędach. Po zalogowaniu się przy użyciu uprawnień administratora, wyświetlane jest okno, dzięki czemu możesz zgłaszać błędów od czasu ostatniego zostały zarejestrowane w (użytkownik nie jest monitowany o wysłanie raportu błędów więcej niż raz na trzy dni). **kolejka** jest domyślną kolekcją podczas kompilowania aplikacji w wierszu polecenia.

**Wyślij**<br/>
Automatycznie wysyła raporty błędów wewnętrznych kompilatora do firmy Microsoft, jeśli za pomocą ustawień usługi Windows Error Reporting jest włączone raportowanie.

## <a name="remarks"></a>Uwagi

**/Errorreport** opcja umożliwia dostarczanie wewnętrznych kompilatora-informacje o błędzie (ICE) bezpośrednio do firmy Microsoft.

Opcja **/errorreport: Send** automatycznie wysyła informacje o błędzie do firmy Microsoft, jeśli włączone za pomocą ustawień usługi Windows Error Reporting.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Otwórz **właściwości konfiguracji** > **konsolidatora** > **zaawansowane** stronę właściwości.

1. Modyfikowanie **raportowanie błędów** właściwości.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ErrorReporting%2A>.

## <a name="see-also"></a>Zobacz także

[/errorReport (Zgłaszaj wewnętrzne błędy kompilatora)](errorreport-report-internal-compiler-errors.md)<br/>
[Dokumentacja konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)
