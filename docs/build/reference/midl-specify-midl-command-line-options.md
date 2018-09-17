---
title: -MIDL (Określ opcje wiersza polecenia MIDL) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/05/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /midl
- VC.Project.VCLinkerTool.MidlCommandFile
dev_langs:
- C++
helpviewer_keywords:
- -MIDL linker option
- MIDL
- /MIDL linker option
- MIDL linker option
- MIDL, command line options
ms.assetid: 22dc259e-b34c-4ed3-a380-4beb734482c1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ce4c5159a66963268ae83e0c0adfdc082dfcc81c
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45706943"
---
# <a name="midl-specify-midl-command-line-options"></a>/MIDL (Określ opcje wiersza polecenia MIDL)

Określa plik odpowiedzi opcji wiersza polecenia MIDL

## <a name="syntax"></a>Składnia

> **/ MIDL:\@**<em>pliku</em>

## <a name="arguments"></a>Argumenty

*Plik*<br/>
Nazwa pliku, który zawiera [opcje wiersza polecenia MIDL](/windows/desktop/Midl/general-midl-command-line-syntax).

## <a name="remarks"></a>Uwagi

Wszystkie opcje konwersji w pliku IDL z plikiem TLB musi być podany w *pliku*; Nie można określić opcje wiersza polecenia MIDL w wierszu polecenia konsolidatora. Jeśli /MIDL nie zostanie określony, kompilator MIDL zostanie wywołany za pomocą tylko nazwę pliku IDL i inne opcje.

Ten plik powinien zawierać jedną opcję wiersza polecenia MIDL na wiersz.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [ustawienie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).

2. Wybierz **właściwości konfiguracji** > **konsolidatora** > **osadzone IDL** stronę właściwości.

3. Modyfikowanie **polecenia MIDL** właściwości.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MidlCommandFile%2A>.

## <a name="see-also"></a>Zobacz też

[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)<br/>
[Opcje konsolidatora](../../build/reference/linker-options.md)<br/>
[/ IDLOUT (nazwij wyjściowe pliki MIDL)](../../build/reference/idlout-name-midl-output-files.md)
[/IGNOREIDL (nie Przetwarzaj atrybutów w MIDL)](../../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)
 [ /tlbout (nazwa. Plik TLB)](../../build/reference/tlbout-name-dot-tlb-file.md)
[kompilowanie programu opartego na atrybutach](../../windows/building-an-attributed-program.md)