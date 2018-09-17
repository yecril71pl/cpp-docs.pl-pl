---
title: -TLBID (Określ identyfikator ID zasobu dla TypeLib) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /tlbid
- VC.Project.VCLinkerTool.TypeLibraryResourceID
dev_langs:
- C++
helpviewer_keywords:
- tlb files, specifying resource ID
- -TLBID linker option
- .tlb files, specifying resource ID
- /TLBID linker option
- TLBID linker option
- type libraries, specifying resource ID
ms.assetid: 434b28a2-4656-4d52-ac82-8b18bf486fb2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e34e4d27c374fddd7710431e3a09f6a9ccfc802d
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45701317"
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