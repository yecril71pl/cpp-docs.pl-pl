---
title: /MIDL (Określ opcje wiersza polecenia MIDL)
ms.date: 09/05/2018
f1_keywords:
- /midl
- VC.Project.VCLinkerTool.MidlCommandFile
helpviewer_keywords:
- -MIDL linker option
- MIDL
- /MIDL linker option
- MIDL linker option
- MIDL, command line options
ms.assetid: 22dc259e-b34c-4ed3-a380-4beb734482c1
ms.openlocfilehash: 584958ac51bdc491ad1bdd16117ecaad6e000ec7
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57814192"
---
# <a name="midl-specify-midl-command-line-options"></a>/MIDL (Określ opcje wiersza polecenia MIDL)

Określa plik odpowiedzi opcji wiersza polecenia MIDL

## <a name="syntax"></a>Składnia

> **/MIDL:\@**<em>file</em>

## <a name="arguments"></a>Argumenty

*Plik*<br/>
Nazwa pliku, który zawiera [opcje wiersza polecenia MIDL](/windows/desktop/Midl/general-midl-command-line-syntax).

## <a name="remarks"></a>Uwagi

Wszystkie opcje konwersji w pliku IDL z plikiem TLB musi być podany w *pliku*; Nie można określić opcje wiersza polecenia MIDL w wierszu polecenia konsolidatora. Jeśli /MIDL nie zostanie określony, kompilator MIDL zostanie wywołany za pomocą tylko nazwę pliku IDL i inne opcje.

Ten plik powinien zawierać jedną opcję wiersza polecenia MIDL na wiersz.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **konsolidatora** > **osadzone IDL** stronę właściwości.

1. Modyfikowanie **polecenia MIDL** właściwości.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MidlCommandFile%2A>.

## <a name="see-also"></a>Zobacz także

[Odwołania konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)<br/>
[/IDLOUT (Nazwij wyjściowe pliki MIDL)](idlout-name-midl-output-files.md)<br/>
[/IGNOREIDL (Nie przetwarzaj atrybutów w MIDL)](ignoreidl-don-t-process-attributes-into-midl.md)<br/>
[/TLBOUT (Nazywanie pliku .TLB)](tlbout-name-dot-tlb-file.md)<br/>
[Kompilowanie programu opartego na atrybutach](../../windows/building-an-attributed-program.md)
