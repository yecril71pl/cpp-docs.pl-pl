---
title: /HIGHENTROPYVA (Adres 64-bitowej obsługi ASLR)
ms.date: 06/12/2018
ms.assetid: fe35f9f7-d28e-4694-9aeb-a79db06168e0
ms.openlocfilehash: 5ecbbf8bbd8e74f80f2f5b2d7df0d2ef544112fc
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57822005"
---
# <a name="highentropyva-support-64-bit-aslr"></a>/HIGHENTROPYVA (Adres 64-bitowej obsługi ASLR)

Określa, czy obraz wykonywalny obsługuje z randomizacji układu przestrzeni adresowej 64-bitowej o wysokiej entropii (ASLR).

## <a name="syntax"></a>Składnia

> **/HIGHENTROPYVA**[**:NO**]

## <a name="remarks"></a>Uwagi

**/ HIGHENTROPYVA** modyfikuje nagłówek *obrazu pliku wykonywalnego*, pliku .dll lub pliku .exe, aby wskazać, czy ASLR może używać miejsca na cały adres 64-bitowych. Gdy ta opcja jest ustawiona na wykonawczą i wszystkie moduły, w których jest zależna, system operacyjny, który obsługuje 64-bitowy ASLR może przemieścić segmenty wykonawczego obrazu w czasie ładowania, używając niestandardowych adresów w 64-bitowej wirtualnej przestrzeni adresowej. Ta duża przestrzeń na sprawia, że utrudnia osobie atakującej intruzowi zgadnąć lokalizację konkretnego regionu pamięci.

Domyślnie **/highentropyva** jest włączone dla 64-bitowych obrazów wykonywalnych. Ta opcja wymaga [/largeaddressaware](largeaddressaware-handle-large-addresses.md), który jest również domyślnie włączone dla 64-bitowych obrazów. **/ HIGHENTROPYVA** nie ma zastosowania do wykonywalnych obrazów 32-bitowych, gdzie konsolidator ignoruje opcję. Aby jawnie wyłączyć tę opcję, należy użyć **/HIGHENTROPYVA:NO**.

Aby uzyskać **/highentropyva** efekty w czasie ładowania [opcja/DynamicBase](dynamicbase-use-address-space-layout-randomization.md) musi być także włączona. **/ DYNAMICBASE** jest domyślnie włączona i jest wymagany do włączenia ASLR w systemach Windows Vista i nowszych systemach operacyjnych. Wcześniejszych wersjach Windows ignorują tę flagę.

### <a name="to-set-this-linker-option-in-visual-studio"></a>Aby ustawić tę opcję konsolidatora w programie Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **konsolidatora** > **wiersza polecenia** stronę właściwości.

1. W **dodatkowe opcje**, wprowadź `/HIGHENTROPYVA` lub `/HIGHENTROPYVA:NO`.

## <a name="see-also"></a>Zobacz także

- [Odwołania konsolidatora MSVC](linking.md)
- [Opcje konsolidatora MSVC](linker-options.md)
- [/DYNAMICBASE](dynamicbase-use-address-space-layout-randomization.md)
- [/LARGEADDRESSAWARE](largeaddressaware-handle-large-addresses.md)
- [Poziom ochrony oprogramowania niezależnego dostawcy oprogramowania Windows](https://msdn.microsoft.com/library/bb430720.aspx)
