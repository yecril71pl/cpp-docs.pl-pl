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
ms.openlocfilehash: d8d2e6a859c68af473d49dc04b76f0a15056aa56
ms.sourcegitcommit: faa42c8a051e746d99dcebe70fd4bbaf3b023ace
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2019
ms.locfileid: "57809473"
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

Istnieje możliwość modyfikowania wyrównania sekcji przy użyciu parametrów wyrównanie do [/SECTION](section-specify-section-attributes.md) opcji.

Wartość wyrównania, który określisz nie może być mniejszy niż największa wyrównanie sekcji.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **konsolidatora** > **wiersza polecenia** stronę właściwości.

1. Wpisz opcje w **dodatkowe opcje** pole. Wybierz **OK** lub **Zastosuj** do zastosowania zmiany.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[Odwołania konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)
