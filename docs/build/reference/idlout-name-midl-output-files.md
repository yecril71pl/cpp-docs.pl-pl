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
ms.openlocfilehash: 3816bb85cb3c711075e3fefeec2d706c2f8cc2ff
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62291579"
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

Kompilator MIDL jest wywoływana przez konsolidator MSVC podczas łączenia projektów, które mają [modułu](../../windows/module-cpp.md) atrybutu.

/ IDLOUT określa również nazwy plików skojarzonych z kompilator MIDL inne pliki wyjściowe:

- *Nazwa pliku*.tlb

- *Nazwa pliku*_p.c

- *Nazwa pliku*_i.c

- *Nazwa pliku*.h

*Nazwa pliku* jest parametrem, który jest przekazywany do/idlout. Jeśli [/tlbout](tlbout-name-dot-tlb-file.md) określono pliku .tlb otrzyma jego nazwę w/tlbout *filename*.

Jeśli określisz/idlout ani/tlbout konsolidator utworzy vc70.tlb vc70.idl, vc70_p.c, vc70_i.c i vc70.h.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Kliknij przycisk **konsolidatora** folderu.

1. Kliknij przycisk **osadzone IDL** stronę właściwości.

1. Modyfikowanie **scalania nazwa pliku IDL Base** właściwości.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MergedIDLBaseFileName%2A>.

## <a name="see-also"></a>Zobacz także

[Dokumentacja konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)<br/>
[/IGNOREIDL (Nie przetwarzaj atrybutów w MIDL)](ignoreidl-don-t-process-attributes-into-midl.md)<br/>
[/MIDL (Określ opcje wiersza polecenia MIDL)](midl-specify-midl-command-line-options.md)<br/>
[Kompilowanie programu opartego na atrybutach](../../windows/building-an-attributed-program.md)
