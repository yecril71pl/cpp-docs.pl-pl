---
title: /IGNOREIDL (nie&#39;t Przetwarzaj atrybutów w MIDL)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.IgnoreEmbeddedIDL
- /ignoreidl
helpviewer_keywords:
- IGNOREIDL linker option
- -IGNOREIDL linker option
- /IGNOREIDL linker option
ms.assetid: 29514098-6a1c-4317-af2f-1dc268972780
ms.openlocfilehash: eac6209e0c34562254117d6ab9db5f47545037ea
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91506894"
---
# <a name="ignoreidl-don39t-process-attributes-into-midl"></a>/IGNOREIDL (nie&#39;t Przetwarzaj atrybutów w MIDL)

```
/IGNOREIDL
```

## <a name="remarks"></a>Uwagi

Opcja/IGNOREIDL określa, że żadne [atrybuty IDL](../../windows/attributes/idl-attributes.md) w kodzie źródłowym nie powinny być przetwarzane do pliku. idl.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. Kliknij folder **konsolidator** .

1. Kliknij stronę właściwości **osadzony IDL** .

1. Zmodyfikuj właściwość **Ignoruj OSADZONE IDL** .

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz: <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreEmbeddedIDL%2A>.

## <a name="see-also"></a>Zobacz też

[Dokumentacja konsolidatora MSVC](linking.md)<br/>
[MSVC Opcje konsolidatora](linker-options.md)<br/>
[/IDLOUT (Nazwij MIDL pliki wyjściowe)](idlout-name-midl-output-files.md)<br/>
[/TLBOUT (Name. Plik TLB)](tlbout-name-dot-tlb-file.md)<br/>
[/MIDL (Określ opcje wiersza polecenia MIDL)](midl-specify-midl-command-line-options.md)<br/>
[Kompilowanie programu opartego na atrybutach](../../windows/attributes/cpp-attributes-com-net.md)
