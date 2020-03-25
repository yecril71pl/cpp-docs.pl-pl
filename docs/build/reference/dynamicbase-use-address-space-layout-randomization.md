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
ms.openlocfilehash: 66d6232ed43f9c842ebbb0e22b57c509cf610afa
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170062"
---
# <a name="dynamicbase-use-address-space-layout-randomization"></a>/DYNAMICBASE (Korzystaj z randomizacji układu przestrzeni adresowej)

Określa, czy generować obraz wykonywalny, który może być losowo zmieniany w czasie ładowania przy użyciu funkcji losowego układu przestrzeni adresowej (ASLR) systemu Windows, która była początkowo dostępna w systemie Windows Vista.

## <a name="syntax"></a>Składnia

> **/DYNAMICBASE**[ **: No**]

## <a name="remarks"></a>Uwagi

Opcja **/DYNAMICBASE** modyfikuje nagłówek *obrazu wykonywalnego*, pliku DLL lub exe, aby wskazać, czy aplikacja powinna być losowo zmieniana w czasie ładowania, i umożliwia losowe generowanie alokacji adresów wirtualnych, co ma wpływ na lokalizację pamięci wirtualnej sterty, stosy i inne alokacje systemu operacyjnego. Opcja **/DYNAMICBASE** dotyczy zarówno obrazów 32-bitowych, jak i 64-bitowych. ASLR jest obsługiwana w systemach operacyjnych Windows Vista i nowszych. Ta opcja jest ignorowana przez wcześniejsze systemy operacyjne.

Domyślnie **/DYNAMICBASE** jest włączona. Aby wyłączyć tę opcję, użyj **/DYNAMICBASE: No**. Opcja **/DYNAMICBASE** jest wymagana, aby opcja [/HIGHENTROPYVA](highentropyva-support-64-bit-aslr.md) miała efekt.

### <a name="to-set-this-linker-option-in-visual-studio"></a>Aby ustawić tę opcję konsolidatora w programie Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać więcej informacji, [Zobacz C++ Ustawianie właściwości kompilatora i Build w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **Właściwości konfiguracji** > **konsolidator** > strony właściwości **Zaawansowane** .

1. Modyfikuj Właściwość **losowy adres podstawowy** .

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz: <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.RandomizedBaseAddress%2A>.

## <a name="see-also"></a>Zobacz też

- [Dokumentacja konsolidatora MSVC](linking.md)
- [Opcje konsolidatora MSVC](linker-options.md)
- [/HIGHENTROPYVA](highentropyva-support-64-bit-aslr.md)
- [Ochrona przed oprogramowaniem ISV systemu Windows](https://msdn.microsoft.com/library/bb430720.aspx)
