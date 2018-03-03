---
title: "/ ALIGN (wyrównanie sekcji) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 12/29/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
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
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4ca4572e84c7ad32be2d03a312f7bb7d8a3f3f29
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2018
---
# <a name="align-section-alignment"></a>/ALIGN (Wyrównanie sekcji)

## <a name="syntax"></a>Składnia

> **/ ALIGN**[**:**_numer_]

### <a name="arguments"></a>Argumenty

*numer*  
Wartość wyrównania w bajtach.

## <a name="remarks"></a>Uwagi

**/ALIGN** opcja określa wyrównanie każdej z sekcji w liniowej przestrzeni adresowej programu. *Numer* argument w bajtach i musi być potęgą liczby dwa. Wartość domyślna to 4K (4096). Konsolidator wygeneruje ostrzeżenie, jeśli wyrównanie tworzy nieprawidłowy obraz.

Jeśli piszesz aplikację, takie jak sterownik urządzenia, należy nie należy zmodyfikować wyrównania.

Istnieje możliwość modyfikowania wyrównanie sekcji z parametrem Wyrównaj do [/SECTION](../../build/reference/section-specify-section-attributes.md) opcji.

Wartość wyrównania, określonym przez użytkownika nie może być mniejszy niż największa wyrównanie sekcji.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Ustawianie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **konsolidatora** > **wiersza polecenia** strony właściwości.

1. Wybierz opcję w **dodatkowe opcje** pole. Wybierz **OK** lub **Zastosuj** do zastosowania zmiany.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)  
[Opcje konsolidatora](../../build/reference/linker-options.md)  
