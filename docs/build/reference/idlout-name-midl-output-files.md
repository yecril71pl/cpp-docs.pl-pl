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
ms.openlocfilehash: 8dc26a0564a979c918d1eb1eb85e63e9c73caba0
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91506933"
---
# <a name="idlout-name-midl-output-files"></a>/IDLOUT (Nazwij wyjściowe pliki MIDL)

```
/IDLOUT:[path\]filename
```

## <a name="parameters"></a>Parametry

*ścieżka*<br/>
Specyfikacja ścieżki absolutnej lub względnej. Określenie ścieżki ma wpływ tylko na lokalizację pliku. idl; wszystkie inne pliki są umieszczane w katalogu projektu.

*Nazwa pliku*<br/>
Określa nazwę pliku IDL utworzonego przez kompilator MIDL. Nie założono rozszerzenia pliku; Określ *nazwę pliku*. idl, jeśli chcesz mieć rozszerzenie IDL.

## <a name="remarks"></a>Uwagi

Opcja/IDLOUT określa nazwę i rozszerzenie pliku. idl.

Kompilator MIDL jest wywoływany przez konsolidator MSVC podczas łączenia projektów, które mają atrybut [modułu](../../windows/attributes/module-cpp.md) .

/IDLOUT określa również nazwy plików innych plików wyjściowych skojarzonych z kompilatorem MIDL:

- *filename*. tlb

- *Nazwa pliku*_p. c

- *Nazwa pliku*_i. c

- *nazwa_pliku*. h

*Nazwa pliku* jest parametrem przekazywanym do/IDLOUT. Jeśli [/TLBOUT](tlbout-name-dot-tlb-file.md) jest określony, plik. tlb otrzyma nazwę z *pliku*/TLBOUT.

Jeśli określisz nie/IDLOUT ani/TLBOUT, konsolidator utworzy vc70. tlb, vc70. idl, vc70_p. c, vc70_i. c i vc70. h.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. Kliknij folder **konsolidator** .

1. Kliknij stronę właściwości **osadzony IDL** .

1. Zmodyfikuj **podstawową Właściwość nazwy pliku scalania IDL** .

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz: <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MergedIDLBaseFileName%2A>.

## <a name="see-also"></a>Zobacz też

[Dokumentacja konsolidatora MSVC](linking.md)<br/>
[MSVC Opcje konsolidatora](linker-options.md)<br/>
[/IGNOREIDL (nie Przetwarzaj atrybutów w MIDL)](ignoreidl-don-t-process-attributes-into-midl.md)<br/>
[/MIDL (Określ opcje wiersza polecenia MIDL)](midl-specify-midl-command-line-options.md)<br/>
[Kompilowanie programu opartego na atrybutach](../../windows/attributes/cpp-attributes-com-net.md)
