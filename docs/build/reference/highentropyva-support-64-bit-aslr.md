---
title: /HIGHENTROPYVA (Adres 64-bitowej obsługi ASLR)
ms.date: 06/12/2018
ms.assetid: fe35f9f7-d28e-4694-9aeb-a79db06168e0
ms.openlocfilehash: 8f8601d89e8456461aac3d91f9fd2cfda216d7f5
ms.sourcegitcommit: 31a443c9998cf5cfbaff00fcf815b133f55b2426
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/14/2020
ms.locfileid: "86373843"
---
# <a name="highentropyva-support-64-bit-aslr"></a>/HIGHENTROPYVA (Adres 64-bitowej obsługi ASLR)

Określa, czy obraz wykonywalny obsługuje generowanie losowe układu przestrzeni adresowej o wysokiej entropii 64 (ASLR).

## <a name="syntax"></a>Składnia

> **/HIGHENTROPYVA**[**: No**]

## <a name="remarks"></a>Uwagi

**/HIGHENTROPYVA** modyfikuje nagłówek *obrazu wykonywalnego*, pliku. dll lub pliku. exe, aby wskazać, czy ASLR może korzystać z całej 64-bitowej przestrzeni adresowej. Gdy ta opcja jest ustawiona dla pliku wykonywalnego i wszystkich modułów, od których jest zależna, system operacyjny obsługujący 64-bitowy ASLR może odtworzyć segmenty obrazu wykonywalnego w czasie ładowania przy użyciu losowych adresów w 64-bitowej wirtualnej przestrzeni adresowej. Ta duża przestrzeń adresowa utrudnia osobie atakującej odpuszczenie lokalizacji określonego obszaru pamięci.

Domyślnie **/HIGHENTROPYVA** jest włączona dla 64-bitowych obrazów plików wykonywalnych. Ta opcja wymaga [/LARGEADDRESSAWARE](largeaddressaware-handle-large-addresses.md), który jest również domyślnie włączony dla obrazów 64-bitowych. **/HIGHENTROPYVA** nie ma zastosowania do 32-bitowych obrazów wykonywalnych, gdzie konsolidator ignoruje opcję. Aby jawnie wyłączyć tę opcję, użyj **/HIGHENTROPYVA: No**.

Aby **/HIGHENTROPYVA** miał efekt w czasie ładowania, należy również włączyć funkcję [/DYNAMICBASE](dynamicbase-use-address-space-layout-randomization.md) . **/DYNAMICBASE** jest domyślnie włączony i jest wymagany do włączenia ASLR w systemie Windows Vista i nowszych systemach operacyjnych. Starsze wersje systemu Windows ignorują tę flagę.

### <a name="to-set-this-linker-option-in-visual-studio"></a>Aby ustawić tę opcję konsolidatora w programie Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać więcej informacji, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz stronę właściwości **Konfiguracja właściwości**  >  **Linker**  >  **wiersza polecenia** konsolidatora.

1. W obszarze **Opcje dodatkowe**wprowadź `/HIGHENTROPYVA` lub `/HIGHENTROPYVA:NO` .

## <a name="see-also"></a>Zobacz też

- [Dokumentacja konsolidatora MSVC](linking.md)
- [MSVC Opcje konsolidatora](linker-options.md)
- [/DYNAMICBASE](dynamicbase-use-address-space-layout-randomization.md)
- [/LARGEADDRESSAWARE](largeaddressaware-handle-large-addresses.md)
- [Ochrona przed oprogramowaniem ISV systemu Windows](https://docs.microsoft.com/previous-versions/bb430720(v=msdn.10))
