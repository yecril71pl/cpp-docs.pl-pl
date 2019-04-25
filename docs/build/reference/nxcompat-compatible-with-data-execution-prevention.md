---
title: /NXCOMPAT (Zgodny z zapobieganiem wykonywaniu danych)
ms.date: 12/29/2017
f1_keywords:
- /NXCOMPAT
helpviewer_keywords:
- /NXCOMPAT linker option
- -NXCOMPAT linker option
- NXCOMPAT linker option
ms.openlocfilehash: a8550337189f9c92a1c8a8d86f2f9b2b829bbc3e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320373"
---
# <a name="nxcompat-compatible-with-data-execution-prevention"></a>/NXCOMPAT (Zgodny z zapobieganiem wykonywaniu danych)

Wskazuje, że plik wykonywalny jest zgodny z funkcją zapobiegania wykonywaniu danych Windows.

## <a name="syntax"></a>Składnia

> **/NXCOMPAT**[**:NO**]

## <a name="remarks"></a>Uwagi

Domyślnie **/NXCOMPAT** znajduje się na.

**: No** może służyć do jawnego określenia pliku wykonywalnego jako niezgodny z zapobieganiem wykonywaniu danych.

Aby uzyskać więcej informacji dotyczących zapobiegania wykonywaniu danych zobacz następujące artykuły:

- [Szczegółowy opis funkcji Zapobieganie wykonywania danych (DEP)](https://support.microsoft.com/help/875352/a-detailed-description-of-the-data-execution-prevention-dep-feature-in)

- [Zapobieganie wykonywaniu danych](/windows/desktop/Memory/data-execution-prevention)

- [Zapobieganie wykonywaniu danych (Windows Embedded)](/previous-versions/windows/embedded/ms913190\(v=winembedded.5\))

### <a name="to-set-this-linker-option-in-visual-studio"></a>Aby ustawić tę opcję konsolidatora w programie Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **konsolidatora** > **wiersza polecenia** stronę właściwości.

1. Wpisz opcje w **dodatkowe opcje** pole. Wybierz **OK** lub **Zastosuj** do zastosowania zmiany.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[Dokumentacja konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)
