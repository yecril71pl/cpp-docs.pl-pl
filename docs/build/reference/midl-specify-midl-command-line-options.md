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
ms.openlocfilehash: ca172428943d2446490eeb10741966f5e8c9ea85
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492720"
---
# <a name="midl-specify-midl-command-line-options"></a>/MIDL (Określ opcje wiersza polecenia MIDL)

Określa plik odpowiedzi dla opcji wiersza polecenia MIDL

## <a name="syntax"></a>Składnia

> **/MIDL:\@** <em>plik</em>

## <a name="arguments"></a>Argumenty

*rozszerzeniem*<br/>
Nazwa pliku, który zawiera [Opcje wiersza polecenia MIDL](/windows/win32/Midl/general-midl-command-line-syntax).

## <a name="remarks"></a>Uwagi

Wszystkie opcje konwersji pliku IDL do pliku TLB muszą zostać umieszczone w *pliku*; Opcji wiersza polecenia MIDL nie można określić w wierszu polecenia konsolidatora. Jeśli/MIDL nie zostanie określony, kompilator MIDL będzie wywoływany tylko z nazwą pliku IDL i nie ma żadnych innych opcji.

Plik powinien zawierać jedną opcję wiersza polecenia MIDL na wiersz.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [ C++ Ustawianie właściwości kompilatora i Build w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz stronę właściwości **Konfiguracja** > **konsolidator** > **osadzony** właściwości.

1. Zmodyfikuj właściwość **MIDL Commands** .

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MidlCommandFile%2A>.

## <a name="see-also"></a>Zobacz także

[Dokumentacja konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)<br/>
[/IDLOUT (Nazwij wyjściowe pliki MIDL)](idlout-name-midl-output-files.md)<br/>
[/IGNOREIDL (Nie przetwarzaj atrybutów w MIDL)](ignoreidl-don-t-process-attributes-into-midl.md)<br/>
[/TLBOUT (Nazywanie pliku .TLB)](tlbout-name-dot-tlb-file.md)<br/>
[Kompilowanie programu opartego na atrybutach](../../windows/building-an-attributed-program.md)
