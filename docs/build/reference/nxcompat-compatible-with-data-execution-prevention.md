---
title: /NXCOMPAT (Zgodny z zapobieganiem wykonywaniu danych)
ms.date: 12/29/2017
f1_keywords:
- /NXCOMPAT
helpviewer_keywords:
- /NXCOMPAT linker option
- -NXCOMPAT linker option
- NXCOMPAT linker option
ms.openlocfilehash: 7c788f5ec499f0edf0c44f1ff269af9767af6c08
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492663"
---
# <a name="nxcompat-compatible-with-data-execution-prevention"></a>/NXCOMPAT (Zgodny z zapobieganiem wykonywaniu danych)

Wskazuje, że plik wykonywalny jest zgodny z funkcją zapobiegania wykonywaniu danych systemu Windows.

## <a name="syntax"></a>Składnia

> **/NXCOMPAT**[ **:NO**]

## <a name="remarks"></a>Uwagi

Domyślnie **/NXCOMPAT** jest włączone.

**/NXCOMPAT: nie** można użyć funkcji, aby jawnie określić plik wykonywalny jako niezgodny z funkcją zapobiegania wykonywaniu danych.

Aby uzyskać więcej informacji na temat zapobiegania wykonywaniu danych, zobacz następujące artykuły:

- [Szczegółowy opis funkcji zapobiegania wykonywaniu danych (DEP)](https://support.microsoft.com/help/875352/a-detailed-description-of-the-data-execution-prevention-dep-feature-in)

- [Zapobieganie wykonywaniu danych](/windows/win32/Memory/data-execution-prevention)

- [Zapobieganie wykonywaniu danych (Windows Embedded)](/previous-versions/windows/embedded/ms913190\(v=winembedded.5\))

### <a name="to-set-this-linker-option-in-visual-studio"></a>Aby ustawić tę opcję konsolidatora w programie Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [ C++ Ustawianie właściwości kompilatora i Build w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz stronę właściwości **Konfiguracja właściwości** > **wiersza polecenia** **konsolidatora** > .

1. Wprowadź opcję w polu **dodatkowe opcje** . Wybierz **przycisk OK** lub **Zastosuj** , aby zastosować zmianę.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[Dokumentacja konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)
