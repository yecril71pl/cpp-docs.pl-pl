---
title: / NXCOMPAT (zgodny z zapobieganiem wykonywaniu danych) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 12/29/2017
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /NXCOMPAT
dev_langs:
- C++
helpviewer_keywords:
- /NXCOMPAT linker option
- -NXCOMPAT linker option
- NXCOMPAT linker option
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9f6e2c3f1c297493b2af72f280ac5eabcb6f17ce
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43690322"
---
# <a name="nxcompat-compatible-with-data-execution-prevention"></a>/NXCOMPAT (Zgodny z zapobieganiem wykonywaniu danych)

Wskazuje, że plik wykonywalny jest zgodny z funkcją zapobiegania wykonywaniu danych Windows.

## <a name="syntax"></a>Składnia

> **/ NXCOMPAT**[**: NO**]

## <a name="remarks"></a>Uwagi

Domyślnie **/NXCOMPAT** znajduje się na.

**: No** może służyć do jawnego określenia pliku wykonywalnego jako niezgodny z zapobieganiem wykonywaniu danych.

Aby uzyskać więcej informacji dotyczących zapobiegania wykonywaniu danych zobacz następujące artykuły:

- [Szczegółowy opis funkcji Zapobieganie wykonywania danych (DEP)](https://support.microsoft.com/en-us/help/875352/a-detailed-description-of-the-data-execution-prevention-dep-feature-in)

- [Zapobieganie wykonywaniu danych](/windows/desktop/Memory/data-execution-prevention)

- [Zapobieganie wykonywaniu danych (Windows Embedded)](/previous-versions/windows/embedded/ms913190\(v=winembedded.5\))

### <a name="to-set-this-linker-option-in-visual-studio"></a>Aby ustawić tę opcję konsolidatora w programie Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **konsolidatora** > **wiersza polecenia** stronę właściwości.

1. Wpisz opcje w **dodatkowe opcje** pole. Wybierz **OK** lub **Zastosuj** do zastosowania zmiany.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)  
[Opcje konsolidatora](../../build/reference/linker-options.md)  
