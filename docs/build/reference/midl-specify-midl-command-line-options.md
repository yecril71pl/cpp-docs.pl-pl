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
ms.openlocfilehash: 3f1b6526f51e5aaa48008792361d3e63249d9f16
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91502850"
---
# <a name="midl-specify-midl-command-line-options"></a>/MIDL (Określ opcje wiersza polecenia MIDL)

Określa plik odpowiedzi dla opcji wiersza polecenia MIDL

## <a name="syntax"></a>Składnia

> **/MIDL: \@ ** <em>plik</em>

## <a name="arguments"></a>Argumenty

*rozszerzeniem*<br/>
Nazwa pliku, który zawiera [Opcje wiersza polecenia MIDL](/windows/win32/Midl/general-midl-command-line-syntax).

## <a name="remarks"></a>Uwagi

Wszystkie opcje konwersji pliku IDL do pliku TLB muszą zostać umieszczone w *pliku*; Opcji wiersza polecenia MIDL nie można określić w wierszu polecenia konsolidatora. Jeśli/MIDL nie zostanie określony, kompilator MIDL będzie wywoływany tylko z nazwą pliku IDL i nie ma żadnych innych opcji.

Plik powinien zawierać jedną opcję wiersza polecenia MIDL na wiersz.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz stronę właściwości **Konfiguracja**  >  **konsolidator**  >  **osadzony** właściwości.

1. Zmodyfikuj właściwość **MIDL Commands** .

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz: <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MidlCommandFile%2A>.

## <a name="see-also"></a>Zobacz też

[Dokumentacja konsolidatora MSVC](linking.md)<br/>
[MSVC Opcje konsolidatora](linker-options.md)<br/>
[/IDLOUT (Nazwij MIDL pliki wyjściowe)](idlout-name-midl-output-files.md)<br/>
[/IGNOREIDL (nie Przetwarzaj atrybutów w MIDL)](ignoreidl-don-t-process-attributes-into-midl.md)<br/>
[/TLBOUT (Name. Plik TLB)](tlbout-name-dot-tlb-file.md)<br/>
[Kompilowanie programu opartego na atrybutach](../../windows/attributes/cpp-attributes-com-net.md)
