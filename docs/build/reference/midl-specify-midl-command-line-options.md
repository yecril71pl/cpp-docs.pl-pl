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
ms.openlocfilehash: d2fa03920f60d7da4730bc46b23605ccfa13f6d7
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/08/2018
ms.locfileid: "48860390"
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

1. Wybierz **właściwości konfiguracji** > **konsolidatora** > **osadzone IDL** stronę właściwości.

1. Modyfikowanie **polecenia MIDL** właściwości.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MidlCommandFile%2A>.

## <a name="see-also"></a>Zobacz też

[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)<br/>
[Opcje konsolidatora](../../build/reference/linker-options.md)<br/>
[/IDLOUT (Nazwij wyjściowe pliki MIDL)](../../build/reference/idlout-name-midl-output-files.md)<br/>
[/IGNOREIDL (Nie przetwarzaj atrybutów w MIDL)](../../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)<br/>
[/TLBOUT (Nazywanie pliku .TLB)](../../build/reference/tlbout-name-dot-tlb-file.md)<br/>
[Kompilowanie programu opartego na atrybutach](../../windows/building-an-attributed-program.md)
