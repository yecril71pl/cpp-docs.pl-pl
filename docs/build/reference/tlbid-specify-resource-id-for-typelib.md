---
title: /TLBID (Określ identyfikator ID zasobu dla TypeLib)
ms.date: 11/04/2016
f1_keywords:
- /tlbid
- VC.Project.VCLinkerTool.TypeLibraryResourceID
helpviewer_keywords:
- tlb files, specifying resource ID
- -TLBID linker option
- .tlb files, specifying resource ID
- /TLBID linker option
- TLBID linker option
- type libraries, specifying resource ID
ms.assetid: 434b28a2-4656-4d52-ac82-8b18bf486fb2
ms.openlocfilehash: 1a86c753aa94302e7f4d26c53fee2f63175d33c7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50519291"
---
# <a name="tlbid-specify-resource-id-for-typelib"></a>/TLBID (Określ identyfikator ID zasobu dla TypeLib)

```
/TLBID:id
```

## <a name="arguments"></a>Argumenty

*id*<br/>
Określone przez użytkownika wartość dla biblioteki typów, utworzone przez konsolidator. Zastępuje domyślny identyfikator zasobu 1.

## <a name="remarks"></a>Uwagi

Podczas kompilowania program, który używa atrybutów, konsolidator utworzy bibliotekę typów. Konsolidator przypisze 1 identyfikator zasobu biblioteki typów.

Jeśli tego Identyfikatora zasobu powoduje konflikt z jednym z istniejących zasobów, można określić inny identyfikator /TLBID. Zakres wartości, które można przekazać do `id` to od 1 do 65535.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [ustawienie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).

1. Kliknij przycisk **konsolidatora** folderu.

1. Kliknij przycisk **osadzone IDL** stronę właściwości.

1. Modyfikowanie **identyfikator zasobu biblioteki typów** właściwości.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

1. Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TypeLibraryResourceID%2A>.

## <a name="see-also"></a>Zobacz też

[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)<br/>
[Opcje konsolidatora](../../build/reference/linker-options.md)