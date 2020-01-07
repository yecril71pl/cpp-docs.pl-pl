---
title: /NXCOMPAT (Zgodny z zapobieganiem wykonywaniu danych)
description: Opisuje opcję konsolidatora MicrosoftC++ C/(MSVC)/NXCOMPAT, która oznacza plik wykonywalny jako zgodny z funkcją zapobiegania wykonywaniu danych (DEP).
ms.date: 12/17/2019
f1_keywords:
- /NXCOMPAT
helpviewer_keywords:
- /NXCOMPAT linker option
- -NXCOMPAT linker option
- NXCOMPAT linker option
ms.openlocfilehash: f3a0906a49e3524fff3e1ef1643d1eceee28f169
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75298990"
---
# <a name="nxcompat-compatible-with-data-execution-prevention"></a>/NXCOMPAT (Zgodny z zapobieganiem wykonywaniu danych)

Wskazuje, że plik wykonywalny jest zgodny z funkcją zapobiegania wykonywaniu danych systemu Windows.

## <a name="syntax"></a>Składnia

> **/NXCOMPAT**[ **:NO**]

## <a name="remarks"></a>Uwagi

Domyślnie **/NXCOMPAT** jest włączone.

**/NXCOMPAT: nie** można użyć funkcji, aby jawnie określić plik wykonywalny jako niezgodny z funkcją zapobiegania wykonywaniu danych.

Aby uzyskać więcej informacji na temat zapobiegania wykonywaniu danych, zobacz następujące artykuły:

- [Zapobieganie wykonywaniu danych](/windows/win32/Memory/data-execution-prevention)

- [Zapobieganie wykonywaniu danych (Windows Embedded)](/previous-versions/windows/embedded/ms913190\(v=winembedded.5\))

### <a name="to-set-this-linker-option-in-visual-studio"></a>Aby ustawić tę opcję konsolidatora w programie Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [ C++ Ustawianie właściwości kompilatora i Build w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz opcję **Właściwości konfiguracji** > **konsolidator** > strony właściwości **wiersza polecenia** .

1. Wprowadź opcję w polu **dodatkowe opcje** . Wybierz **przycisk OK** lub **Zastosuj** , aby zastosować zmianę.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[Odwołanie\ konsolidatora MSVC](linking.md)
[Opcje konsolidatora MSVC](linker-options.md)
