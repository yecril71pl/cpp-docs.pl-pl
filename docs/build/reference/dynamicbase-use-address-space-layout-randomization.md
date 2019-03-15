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
ms.openlocfilehash: a3495de3ec72bcac78cdee2f5f3265864e7a2932
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57807757"
---
# <a name="dynamicbase-use-address-space-layout-randomization"></a>/DYNAMICBASE (Korzystaj z randomizacji układu przestrzeni adresowej)

Określa, czy ma być generowany obraz wykonywalny, który może być losowo przebazowanych w czasie ładowania przy użyciu funkcji randomizacji (ASLR) adres miejsca układu systemu Windows, która została po raz pierwszy dostępny w Windows Vista.

## <a name="syntax"></a>Składnia

> **/ DYNAMICBASE**[**: NO**]

## <a name="remarks"></a>Uwagi

**Opcja/DynamicBase** opcja modyfikuje nagłówek *obrazu pliku wykonywalnego*, pliku .dll lub .exe, aby wskazać, czy aplikacja powinna być losowo przebazowanych w czasie ładowania i umożliwia wirtualnego adresu losowe alokacji, który ma wpływ na lokalizację w pamięci wirtualnej sterty, stosy i alokacjami systemu operacyjnego. **Opcja/DynamicBase** opcja dotyczy zarówno 32-bitowych i 64-bitowych obrazów. Obsługiwany jest ASLR w systemach Windows Vista i nowszych systemach operacyjnych. Opcja jest ignorowana przez starszych systemów operacyjnych.

Domyślnie **opcja/DynamicBase** jest włączona. Aby wyłączyć tę opcję, należy użyć **: No**. **Opcja/DynamicBase** opcja jest wymagana dla [/highentropyva](highentropyva-support-64-bit-aslr.md) opcję, aby mieć wpływ.

### <a name="to-set-this-linker-option-in-visual-studio"></a>Aby ustawić tę opcję konsolidatora w programie Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **konsolidatora** > **zaawansowane** stronę właściwości.

1. Modyfikowanie **wybierane adresu podstawowego** właściwości.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.RandomizedBaseAddress%2A>.

## <a name="see-also"></a>Zobacz także

- [Odwołania konsolidatora MSVC](linking.md)
- [Opcje konsolidatora MSVC](linker-options.md)
- [/HIGHENTROPYVA](highentropyva-support-64-bit-aslr.md)
- [Poziom ochrony oprogramowania niezależnego dostawcy oprogramowania Windows](https://msdn.microsoft.com/library/bb430720.aspx)