---
title: /HIGHENTROPYVA (Adres 64-bitowej obsługi ASLR)
ms.date: 06/12/2018
ms.assetid: fe35f9f7-d28e-4694-9aeb-a79db06168e0
ms.openlocfilehash: 929d6aa71010c1f303bf7a1ce64109a01b8792e4
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/15/2020
ms.locfileid: "86404128"
---
# <a name="highentropyva-support-64-bit-aslr"></a>/HIGHENTROPYVA (Adres 64-bitowej obsługi ASLR)

Określa, czy obraz wykonywalny obsługuje generowanie losowe układu przestrzeni adresowej o wysokiej entropii 64 (ASLR).

## <a name="syntax"></a>Składnia

> **`/HIGHENTROPYVA`**[**`:NO`**]

## <a name="remarks"></a>Uwagi

**`/HIGHENTROPYVA`** modyfikuje nagłówek pliku *obrazu wykonywalnego* (na przykład *`.dll`* *`.exe`* pliku lub), aby wskazać, czy ASLR może używać całej przestrzeni adresów 64-bitowej.  Aby mieć efekt, należy ustawić opcję zarówno dla pliku wykonywalnego, jak i wszystkich modułów, od których jest zależna. Następnie system operacyjny obsługujący 64-bitowy ASLR może odtworzyć segmenty obrazu wykonywalnego w czasie ładowania przy użyciu 64-bitowych losowych adresów wirtualnych. Ta duża przestrzeń adresowa utrudnia osobie atakującej odpuszczenie lokalizacji określonego obszaru pamięci.

Domyślnie program **`/HIGHENTROPYVA`** jest włączony dla obrazów wykonywalnych 64-bitowych. Ta opcja wymaga [`/LARGEADDRESSAWARE`](largeaddressaware-handle-large-addresses.md) , który jest również domyślnie włączony dla obrazów 64-bitowych. **`/HIGHENTROPYVA`** nie ma zastosowania do 32-bitowych obrazów wykonywalnych, gdzie konsolidator ignoruje opcję. Aby jawnie wyłączyć tę opcję, użyj **`/HIGHENTROPYVA:NO`** .

Aby **`/HIGHENTROPYVA`** program miał efekt w czasie ładowania, [`/DYNAMICBASE`](dynamicbase-use-address-space-layout-randomization.md) również musi być włączony. **`/DYNAMICBASE`** Program jest domyślnie włączony i jest wymagany do włączenia ASLR w systemie Windows Vista i nowszych systemach operacyjnych. Starsze wersje systemu Windows ignorują tę flagę.

### <a name="to-set-this-linker-option-in-visual-studio"></a>Aby ustawić tę opcję konsolidatora w programie Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać więcej informacji, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz stronę właściwości **Konfiguracja właściwości**  >  **Linker**  >  **wiersza polecenia** konsolidatora.

1. W obszarze **Opcje dodatkowe**wprowadź `/HIGHENTROPYVA` lub `/HIGHENTROPYVA:NO` .

## <a name="see-also"></a>Zobacz też

- [Dokumentacja konsolidatora MSVC](linking.md)
- [Opcje konsolidatora MSVC](linker-options.md)
- [`/DYNAMICBASE`](dynamicbase-use-address-space-layout-randomization.md)
- [`/LARGEADDRESSAWARE`](largeaddressaware-handle-large-addresses.md)
- [Ochrona przed oprogramowaniem ISV systemu Windows](https://docs.microsoft.com/previous-versions/bb430720(v=msdn.10))
