---
title: / HIGHENTROPYVA (64-bitowej obsługi ASLR) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 06/12/2018
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
ms.assetid: fe35f9f7-d28e-4694-9aeb-a79db06168e0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 66fe8f20631d576264eab836f822a414c1244d5b
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43223400"
---
# <a name="highentropyva-support-64-bit-aslr"></a>/HIGHENTROPYVA (Adres 64-bitowej obsługi ASLR)

Określa, czy obraz wykonywalny obsługuje z randomizacji układu przestrzeni adresowej 64-bitowej o wysokiej entropii (ASLR).

## <a name="syntax"></a>Składnia

> **/ HIGHENTROPYVA**[**: NO**]

## <a name="remarks"></a>Uwagi

**/ HIGHENTROPYVA** modyfikuje nagłówek *obrazu pliku wykonywalnego*, pliku .dll lub pliku .exe, aby wskazać, czy ASLR może używać miejsca na cały adres 64-bitowych. Gdy ta opcja jest ustawiona na wykonawczą i wszystkie moduły, w których jest zależna, system operacyjny, który obsługuje 64-bitowy ASLR może przemieścić segmenty wykonawczego obrazu w czasie ładowania, używając niestandardowych adresów w 64-bitowej wirtualnej przestrzeni adresowej. Ta duża przestrzeń na sprawia, że utrudnia osobie atakującej intruzowi zgadnąć lokalizację konkretnego regionu pamięci.

Domyślnie **/highentropyva** jest włączone dla 64-bitowych obrazów wykonywalnych. Ta opcja wymaga [/largeaddressaware](largeaddressaware-handle-large-addresses.md), który jest również domyślnie włączone dla 64-bitowych obrazów. **/ HIGHENTROPYVA** nie ma zastosowania do wykonywalnych obrazów 32-bitowych, gdzie konsolidator ignoruje opcję. Aby jawnie wyłączyć tę opcję, należy użyć **/HIGHENTROPYVA:NO**.

Aby uzyskać **/highentropyva** efekty w czasie ładowania [opcja/DynamicBase](dynamicbase-use-address-space-layout-randomization.md) musi być także włączona. **/ DYNAMICBASE** jest domyślnie włączona i jest wymagany do włączenia ASLR w systemach Windows Vista i nowszych systemach operacyjnych. Wcześniejszych wersjach Windows ignorują tę flagę.

### <a name="to-set-this-linker-option-in-visual-studio"></a>Aby ustawić tę opcję konsolidatora w programie Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **konsolidatora** > **wiersza polecenia** stronę właściwości.

1. W **dodatkowe opcje**, wprowadź `/HIGHENTROPYVA` lub `/HIGHENTROPYVA:NO`.

## <a name="see-also"></a>Zobacz także

- [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)
- [Opcje konsolidatora](../../build/reference/linker-options.md)
- [/DYNAMICBASE](dynamicbase-use-address-space-layout-randomization.md)
- [/LARGEADDRESSAWARE](largeaddressaware-handle-large-addresses.md)
- [Poziom ochrony oprogramowania niezależnego dostawcy oprogramowania Windows](https://msdn.microsoft.com/library/bb430720.aspx)
