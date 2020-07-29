---
title: /guard (włącz ochronę przepływu sterowania)
ms.date: 11/04/2016
f1_keywords:
- /guard
- VC.Project.VCCLCompilerTool.ControlFlowGuard
ms.assetid: be495323-f59f-4cf3-a6b6-8ee69e6a19dd
ms.openlocfilehash: 8661f94e0ee35f8d5e2c8caba1fc01bbf4072876
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87190692"
---
# <a name="guard-enable-control-flow-guard"></a>/guard (włącz ochronę przepływu sterowania)

Włącz funkcję generowania kompilatora kontroli zabezpieczeń funkcji przepływu sterowania.

## <a name="syntax"></a>Składnia

```
/guard:cf[-]
```

## <a name="remarks"></a>Uwagi

Opcja **/Guard: CF** powoduje, że kompilator analizuje przepływ sterowania dla pośrednich celów wywołań w czasie kompilacji, a następnie wstawia kod w celu zweryfikowania obiektów docelowych w czasie wykonywania. Domyślnie **/Guard: CF** jest wyłączone i musi być jawnie włączony. Aby jawnie wyłączyć tę opcję, użyj **/Guard: CF-**.

**Program Visual Studio 2017 lub nowszy**: Ta opcja umożliwia dodanie funkcji Guard dla **`switch`** instrukcji, które generują tabele skoku.

Gdy jest określona opcja **/Guard: CF** Control Flow Guard (cfg), kompilator i konsolidator Wstaw dodatkowe środowisko uruchomieniowe sprawdza zabezpieczenia w celu wykrycia prób złamania zabezpieczeń kodu. Podczas kompilowania i łączenia wszystkie wywołania pośrednie w kodzie są analizowane w celu znalezienia każdej lokalizacji, do której kod może dotrzeć, gdy zostanie prawidłowo uruchomiony. Te informacje są przechowywane w dodatkowych strukturach w nagłówkach plików binarnych. Kompilator wprowadza również kontrolę przed każdym pośrednim wywołaniem w kodzie, który gwarantuje, że obiekt docelowy jest jedną z zweryfikowanych lokalizacji. Jeśli sprawdzenie zakończy się niepowodzeniem w czasie wykonywania w systemie operacyjnym z obsługą CFG, system operacyjny zamknie program.

Typowy atak na oprogramowanie wykorzystuje usterki w obsłudze skrajnych lub nieoczekiwanych danych wejściowych. Starannie spreparowane dane wejściowe do aplikacji mogą zastąpić lokalizację, która zawiera wskaźnik do kodu wykonywalnego. Może służyć do przekierowania przepływu sterowania do kodu kontrolowanego przez osobę atakującą. Testy środowiska uruchomieniowego CFG nie rozwiązują usterek uszkodzenia danych w pliku wykonywalnym. Zamiast tego utrudniają osobom atakującym korzystanie z dowolnego kodu. CFG to narzędzie ograniczenia, które uniemożliwia wywołania do lokalizacji innych niż punkty wejścia funkcji w kodzie. Jest to podobne do sposobu, w jaki funkcja zapobiegania wykonywaniu danych (DEP), sprawdzenia stosu [/GS](gs-buffer-security-check.md) i [/DYNAMICBASE](dynamicbase-use-address-space-layout-randomization.md) i [/HIGHENTROPYVAe](highentropyva-support-64-bit-aslr.md) generowanie losowe układu przestrzeni adresowej (ASLR) zmniejszają prawdopodobieństwo, że kod stał się wektorem wykorzystującym luki w zabezpieczeniach.

Opcja **/Guard: CF** musi być przenoszona do kompilatora i konsolidatora, aby kompilować kod wykorzystujący technikę zapobiegania korzystaniu z usługi cfg. Jeśli dane binarne są kompilowane przy użyciu jednego `cl` polecenia, kompilator przekazuje opcję do konsolidatora. Jeśli kompilujesz i łączysz oddzielnie, opcja musi być ustawiona zarówno dla kompilatora, jak i konsolidatora. Opcja konsolidatora/DYNAMICBASE jest również wymagana. Aby sprawdzić, czy plik binarny zawiera dane CFG, użyj `dumpbin /headers /loadconfig` polecenia. Pliki binarne z włączoną funkcją CFG zawierają `Guard` listę właściwości exe lub dll, a flagi ochrony obejmują `CF Instrumented` i `FID table present` .

Opcja **/Guard: CF** jest niezgodna z [/Zi](z7-zi-zi-debug-information-format.md) (Edytuj i Kontynuuj debugowanie informacji) lub [/CLR](clr-common-language-runtime-compilation.md) (Kompilacja środowiska uruchomieniowego języka wspólnego).

Kod skompilowany za pomocą **/Guard: CF** może być połączony z bibliotekami i plikami obiektów, które nie są kompilowane przy użyciu opcji. Tylko ten kod, gdy jest również połączony przy użyciu opcji **/Guard: CF** i uruchamiany w systemie operacyjnym z obsługą cfg, ma ochronę cfg. Ponieważ kod skompilowany bez opcji nie będzie zatrzymywać ataku, zalecamy użycie opcji we wszystkich skompilowanym kodzie. Istnieje niewielki koszt środowiska uruchomieniowego dla testów CFG, ale analiza kompilatora próbuje zoptymalizować testy dotyczące pośrednich uskoków, które mogą być udowodnione jako bezpieczne.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **Właściwości konfiguracji**, **C/C++**, **generowanie kodu**.

1. Wybierz właściwość **Ochrona przepływu sterowania** .

1. W kontrolce menu rozwijanego wybierz opcję **tak** , aby włączyć ochronę przepływu sterowania, lub przycisk **nie** , aby go wyłączyć.

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
