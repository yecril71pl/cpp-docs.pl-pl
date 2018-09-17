---
title: -FIXED (stały adres podstawowy) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /fixed
- VC.Project.VCLinkerTool.FixedBaseAddress
dev_langs:
- C++
helpviewer_keywords:
- preferred base address for loading program
- /FIXED linker option
- -FIXED linker option
- FIXED linker option
ms.assetid: 929bba5e-b7d8-40ed-943e-056aa3710fc5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 697f6ccfd98059175311cd04e4e82038877b2110
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45723401"
---
# <a name="fixed-fixed-base-address"></a>/FIXED (Stałe adresy podstawowe)

```
/FIXED[:NO]
```

## <a name="remarks"></a>Uwagi

Informuje system operacyjny, aby załadować program tylko pod swoim preferowanym adresem bazowym. Jeśli preferowany adres podstawowy jest niedostępny, system operacyjny nie ładuje pliku. Aby uzyskać więcej informacji, zobacz [uwzględniają (adres podstawowy)](../../build/reference/base-base-address.md).

/ Fixed: no jest ustawieniem domyślnym dla DLL, a/Fixed jest domyślne ustawienie dla innych typów projektów.

Po określeniu/Fixed, łącze nie generuje sekcji relokacji w programie. W czasie wykonywania Jeśli system operacyjny nie jest w stanie załadować programu pod podanym adresem go generuje komunikat o błędzie i nie ładuje programu.

Określ/Fixed: No, aby generować sekcję relokacji w programie.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Wybierz **konsolidatora** folderu.

1. Wybierz **wiersza polecenia** stronę właściwości.

1. Wpisz opcje nazwy i ustawienia w **dodatkowe opcje** pole.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz też

[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)<br/>
[Opcje konsolidatora](../../build/reference/linker-options.md)