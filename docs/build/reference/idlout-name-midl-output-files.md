---
title: /IDLOUT (Nazwij wyjściowe pliki MIDL)
ms.date: 11/04/2016
f1_keywords:
- /idlout
- VC.Project.VCLinkerTool.MergedIDLBaseFileName
helpviewer_keywords:
- MIDL, output file names
- .idl files, path
- MIDL
- /IDLOUT linker option
- IDL files, path
- -IDLOUT linker option
- IDLOUT linker option
ms.assetid: 10d00a6a-85b4-4de1-8732-e422c6931509
ms.openlocfilehash: b21e8eb266de9a0baa0512a82acb0ae8a9f650a5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50500428"
---
# <a name="idlout-name-midl-output-files"></a>/IDLOUT (Nazwij wyjściowe pliki MIDL)

```
/IDLOUT:[path\]filename
```

## <a name="parameters"></a>Parametry

*Ścieżka*<br/>
Specyfikacja bezwzględną lub ścieżką względną. Określając ścieżkę, możesz mieć wpływ na lokalizację pliku .idl; wszystkie inne pliki są umieszczane w katalogu projektu.

*Nazwa pliku*<br/>
Określa nazwę pliku .idl, utworzony przez kompilator MIDL. Przyjęto, że brak rozszerzenia pliku; Określ *filename*.idl, jeśli chcesz, aby rozszerzenie .idl.

## <a name="remarks"></a>Uwagi

Opcja/idlout Określa nazwę i rozszerzenie pliku .idl.

Kompilator MIDL jest wywoływana przez konsolidator Visual C++, gdy łączenie projektów, które mają [modułu](../../windows/module-cpp.md) atrybutu.

/ IDLOUT określa również nazwy plików skojarzonych z kompilator MIDL inne pliki wyjściowe:

- *Nazwa pliku*.tlb

- *Nazwa pliku*_p.c

- *Nazwa pliku*_i.c

- *Nazwa pliku*.h

*Nazwa pliku* jest parametrem, który jest przekazywany do/idlout. Jeśli [/tlbout](../../build/reference/tlbout-name-dot-tlb-file.md) określono pliku .tlb otrzyma jego nazwę w/tlbout *filename*.

Jeśli określisz/idlout ani/tlbout konsolidator utworzy vc70.tlb vc70.idl, vc70_p.c, vc70_i.c i vc70.h.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [ustawienie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).

1. Kliknij przycisk **konsolidatora** folderu.

1. Kliknij przycisk **osadzone IDL** stronę właściwości.

1. Modyfikowanie **scalania nazwa pliku IDL Base** właściwości.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MergedIDLBaseFileName%2A>.

## <a name="see-also"></a>Zobacz też

[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)<br/>
[Opcje konsolidatora](../../build/reference/linker-options.md)<br/>
[/IGNOREIDL (Nie przetwarzaj atrybutów w MIDL)](../../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)<br/>
[/MIDL (Określ opcje wiersza polecenia MIDL)](../../build/reference/midl-specify-midl-command-line-options.md)<br/>
[Kompilowanie programu opartego na atrybutach](../../windows/building-an-attributed-program.md)