---
title: /FIXED (Stałe adresy podstawowe)
ms.date: 11/04/2016
f1_keywords:
- /fixed
- VC.Project.VCLinkerTool.FixedBaseAddress
helpviewer_keywords:
- preferred base address for loading program
- /FIXED linker option
- -FIXED linker option
- FIXED linker option
ms.assetid: 929bba5e-b7d8-40ed-943e-056aa3710fc5
ms.openlocfilehash: ccb89b7dfed78ddebf73aaf6e2a1a8529b065042
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57423043"
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

## <a name="see-also"></a>Zobacz także

[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)<br/>
[Opcje konsolidatora](../../build/reference/linker-options.md)
