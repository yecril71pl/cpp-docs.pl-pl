---
title: / ALIGN (wyrównanie sekcji) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 12/29/2017
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.Alignment
- /align
dev_langs:
- C++
helpviewer_keywords:
- sections, specifying alignment
- ALIGN linker option
- /ALIGN linker option
- -ALIGN linker option
- section alignment
- sections
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cb92d4b16be7903004831ffb25e2891f498a8989
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45718253"
---
# <a name="align-section-alignment"></a>/ALIGN (Wyrównanie sekcji)

## <a name="syntax"></a>Składnia

> **/ ALIGN**[**:**_numer_]

### <a name="arguments"></a>Argumenty

*Numer*<br/>
Wartość wyrównania w bajtach.

## <a name="remarks"></a>Uwagi

**/ALIGN** opcja określa wyrównanie każdej sekcji w liniowej przestrzeni adresowej programu. *Numer* argument w bajtach i musi być potęgą liczby dwa. Wartość domyślna to 4K (4096). Konsolidator generuje ostrzeżenie, jeśli wyrównanie generuje nieprawidłowy obraz.

Chyba, że piszesz aplikację taką jak sterownika urządzenia, nie należy do modyfikowania wyrównania.

Istnieje możliwość modyfikowania wyrównania sekcji przy użyciu parametrów wyrównanie do [/SECTION](../../build/reference/section-specify-section-attributes.md) opcji.

Wartość wyrównania, który określisz nie może być mniejszy niż największa wyrównanie sekcji.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [ustawienie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **konsolidatora** > **wiersza polecenia** stronę właściwości.

1. Wpisz opcje w **dodatkowe opcje** pole. Wybierz **OK** lub **Zastosuj** do zastosowania zmiany.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)<br/>
[Opcje konsolidatora](../../build/reference/linker-options.md)
