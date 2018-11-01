---
title: /DYNAMICBASE (Korzystaj z randomizacji układu przestrzeni adresowej)
ms.date: 06/12/2018
f1_keywords:
- VC.Project.VCLinkerTool.RandomizedBaseAddress
helpviewer_keywords:
- -DYNAMICBASE linker option
- /DYNAMICBASE linker option
- DYNAMICBASE linker option
ms.assetid: 6c0ced8e-fe9c-4b63-b956-eb8a55fbceb2
ms.openlocfilehash: 47d23ac6f9234e095a1733a8d4078840318cce4b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50512401"
---
# <a name="dynamicbase-use-address-space-layout-randomization"></a>/DYNAMICBASE (Korzystaj z randomizacji układu przestrzeni adresowej)

Określa, czy ma być generowany obraz wykonywalny, który może być losowo przebazowanych w czasie ładowania przy użyciu funkcji randomizacji (ASLR) adres miejsca układu systemu Windows, która została po raz pierwszy dostępny w Windows Vista.

## <a name="syntax"></a>Składnia

> **/ DYNAMICBASE**[**: NO**]

## <a name="remarks"></a>Uwagi

**Opcja/DynamicBase** opcja modyfikuje nagłówek *obrazu pliku wykonywalnego*, pliku .dll lub .exe, aby wskazać, czy aplikacja powinna być losowo przebazowanych w czasie ładowania i umożliwia wirtualnego adresu losowe alokacji, który ma wpływ na lokalizację w pamięci wirtualnej sterty, stosy i alokacjami systemu operacyjnego. **Opcja/DynamicBase** opcja dotyczy zarówno 32-bitowych i 64-bitowych obrazów. Obsługiwany jest ASLR w systemach Windows Vista i nowszych systemach operacyjnych. Opcja jest ignorowana przez starszych systemów operacyjnych.

Domyślnie **opcja/DynamicBase** jest włączona. Aby wyłączyć tę opcję, należy użyć **: No**. **Opcja/DynamicBase** opcja jest wymagana dla [/highentropyva](highentropyva-support-64-bit-aslr.md) opcję, aby mieć wpływ.

### <a name="to-set-this-linker-option-in-visual-studio"></a>Aby ustawić tę opcję konsolidatora w programie Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **konsolidatora** > **zaawansowane** stronę właściwości.

1. Modyfikowanie **wybierane adresu podstawowego** właściwości.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.RandomizedBaseAddress%2A>.

## <a name="see-also"></a>Zobacz także

- [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)
- [Opcje konsolidatora](../../build/reference/linker-options.md)
- [/HIGHENTROPYVA](highentropyva-support-64-bit-aslr.md)
- [Poziom ochrony oprogramowania niezależnego dostawcy oprogramowania Windows](https://msdn.microsoft.com/library/bb430720.aspx)