---
title: -GUARD (włączenie sprawdzeń za Guard) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
ms.assetid: 72758e23-70ac-4616-94d7-d767477406d1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 71dc4a3a1f2c08d3bac2fcf5c474768f438feccd
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46394989"
---
# <a name="guard-enable-guard-checks"></a>/GUARD (włączenie sprawdzeń za pomocą wyrażenia Guard)

Określa obsługę kontroli ochrony przepływu sterowania w obrazu pliku wykonywalnego.

## <a name="syntax"></a>Składnia

```
/GUARD:{CF|NO}
```

## <a name="remarks"></a>Uwagi

Kiedy/GUARD: CF jest określona, konsolidator modyfikuje nagłówek .dll i .exe, aby wskazać, obsługa testy środowiska uruchomieniowego kontroli Flow Guard (CFG). Konsolidator dodaje także dane adresu docelowego przepływu wymaganej kontrolki z nagłówkiem. Domyślnie/GUARD: CF jest wyłączona. Jego można jawnie wyłączyć za pomocą /GUARD:NO. Zaczęła obowiązywać, wymaga również/GUARD: CF [opcja/DynamicBase (randomizacji układu przestrzeni adresowej Użyj)](../../build/reference/dynamicbase-use-address-space-layout-randomization.md) — opcja konsolidatora, która jest domyślnie włączone.

Podczas kompilowania kodu źródłowego za pomocą [/GUARD: CF](../../build/reference/guard-enable-control-flow-guard.md) opcja, kompilator analizuje przepływ sterowania, sprawdzając wszystkie wywołania pośredniego dla adresów możliwe miejsce docelowe. Kompilator wstawi kod, aby sprawdzić, czy adres docelowy instrukcji pośrednie wywołanie jest na liście adresów docelowych znane w czasie wykonywania. Sprawdź systemy operacyjne obsługujące CFG Zatrzymaj program, który zakończy się niepowodzeniem w środowisku uruchomieniowym CFG. Dzięki temu utrudnia osobie atakującej wykonać złośliwy kod za pomocą uszkodzenia danych, aby zmienić cel wywołania.

Opcja/GUARD: CF musi być określona kompilatora i konsolidatora do utworzenia włączone CFG obrazów pliku wykonywalnego. Kod skompilowany, ale nie jest połączona za pomocą/GUARD: CF wiąże się koszt testy środowiska uruchomieniowego, ale nie umożliwia ochrony CFG. Gdy są określone opcji/GUARD: CF `cl` polecenie, aby skompilować i łącze w jednym kroku, kompilator przekazuje flagę do konsolidatora. Gdy **ochrony przepływu sterowania** właściwość jest ustawiona w programie Visual Studio, opcja/GUARD: CF jest przekazywany do kompilatora i konsolidatora. Gdy oddzielnie zostały skompilowane pliki obiektów i bibliotek, opcja musi być jawnie określona w `link` polecenia.

### <a name="to-set-this-linker-option-in-visual-studio"></a>Aby ustawić tę opcję konsolidatora w programie Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Rozwiń **właściwości konfiguracji**, **konsolidatora**, **wiersza polecenia**.

1. W **dodatkowe opcje**, wprowadź `/GUARD:CF`.

## <a name="see-also"></a>Zobacz też

[/guard (Włącz ochronę przepływu sterowania)](../../build/reference/guard-enable-control-flow-guard.md)<br/>
[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)<br/>
[Opcje konsolidatora](../../build/reference/linker-options.md)