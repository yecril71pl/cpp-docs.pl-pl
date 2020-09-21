---
title: /ERRORREPORT (Zgłaszaj wewnętrzne błędy konsolidatora)
description: Dowiedz się, jak używać/ERRORREPORT.
ms.date: 02/09/2020
f1_keywords:
- /ERRORREPORT
- VC.Project.VCLinkerTool.ErrorReporting
helpviewer_keywords:
- /ERRORREPORT linker option
- ERRORREPORT linker option
- -ERRORREPORT linker option
ms.assetid: f5fab595-a2f1-4eb0-ab5c-1c0fbd3d8c28
ms.openlocfilehash: 7d16904da8490018235278347f23e37339739415
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2020
ms.locfileid: "90742739"
---
# <a name="errorreport-report-internal-linker-errors"></a>/ERRORREPORT (Zgłaszaj wewnętrzne błędy konsolidatora)

Opcja **/errorreport** jest przestarzała. Począwszy od systemu Windows Vista, raportowanie błędów jest kontrolowane przez ustawienia [raportowanie błędów systemu Windows (wer)](/windows/win32/wer/windows-error-reporting) .

## <a name="syntax"></a>Składnia

> **/ErrorReport:** \[ **Brak** \| **Monituj** \| **Kolejka** \| **Wyślij** ]

## <a name="remarks"></a>Uwagi

Argumenty **/errorreport** są zastępowane przez ustawienia usługi Raportowanie błędów systemu Windows. Konsolidator automatycznie wysyła raporty o błędach wewnętrznych do firmy Microsoft, jeśli raportowanie jest włączone przez Raportowanie błędów systemu Windows. Nie jest wysyłany raport, jeśli jest wyłączony przez Raportowanie błędów systemu Windows.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać więcej informacji, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. Otwórz **Configuration Properties**  >  **Linker**  >  stronę właściwości**Zaawansowane** konsolidatora właściwości konfiguracji.

1. Zmodyfikuj właściwość **raportowanie błędów** .

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz: <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ErrorReporting%2A>.

## <a name="see-also"></a>Zobacz też

[Odwołanie konsolidatora MSVC](linking.md)\
[Opcje konsolidatora MSVC](linker-options.md)
