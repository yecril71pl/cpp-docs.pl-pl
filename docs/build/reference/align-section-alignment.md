---
title: /ALIGN (Wyrównanie sekcji)
ms.date: 12/29/2017
f1_keywords:
- VC.Project.VCLinkerTool.Alignment
- /align
helpviewer_keywords:
- sections, specifying alignment
- ALIGN linker option
- /ALIGN linker option
- -ALIGN linker option
- section alignment
- sections
ms.openlocfilehash: b68ec42db9c927fe8f56dad8f5670059359a1843
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50665793"
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
