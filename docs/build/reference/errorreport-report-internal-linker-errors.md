---
title: /ERRORREPORT (Zgłaszaj wewnętrzne błędy konsolidatora)
description: Przewodnik referencyjny dotyczący opcji wiersza polecenia w programie Microsoft NMAKE.
ms.date: 02/09/2020
f1_keywords:
- /ERRORREPORT
- VC.Project.VCLinkerTool.ErrorReporting
helpviewer_keywords:
- /ERRORREPORT linker option
- ERRORREPORT linker option
- -ERRORREPORT linker option
ms.assetid: f5fab595-a2f1-4eb0-ab5c-1c0fbd3d8c28
ms.openlocfilehash: 5e919d4f7eb59524b9145c8e3e59613e60aef1d2
ms.sourcegitcommit: 8414cd91297dea88c480e208c7b5301db9972f19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77257692"
---
# <a name="errorreport-report-internal-linker-errors"></a>/ERRORREPORT (Zgłaszaj wewnętrzne błędy konsolidatora)

Opcja **/errorreport** jest przestarzała. Począwszy od systemu Windows Vista, raportowanie błędów jest kontrolowane przez ustawienia [raportowanie błędów systemu Windows (wer)](/windows/win32/wer/windows-error-reporting) .

## <a name="syntax"></a>Składnia

> **/ErrorReport:** \[ **none** \| **monit** \| **kolejki** \| **send** ]

## <a name="remarks"></a>Uwagi

Argumenty **/errorreport** są zastępowane przez ustawienia usługi Raportowanie błędów systemu Windows. Konsolidator automatycznie wysyła raporty o błędach wewnętrznych do firmy Microsoft, jeśli raportowanie jest włączone przez Raportowanie błędów systemu Windows. Nie jest wysyłany raport, jeśli jest wyłączony przez Raportowanie błędów systemu Windows.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać więcej informacji, [Zobacz C++ Ustawianie właściwości kompilatora i Build w programie Visual Studio](../working-with-project-properties.md).

1. Otwórz stronę właściwości **konfiguracji** > **konsolidator** > **zaawansowanej** strony właściwości.

1. Zmodyfikuj właściwość **raportowanie błędów** .

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz: <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ErrorReporting%2A>.

## <a name="see-also"></a>Zobacz też

[Odwołanie\ konsolidatora MSVC](linking.md)
[MSVC Opcje konsolidatora](linker-options.md)
