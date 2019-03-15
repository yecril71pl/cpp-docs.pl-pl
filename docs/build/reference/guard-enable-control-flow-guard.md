---
title: /guard (włącz ochronę przepływu sterowania)
ms.date: 11/04/2016
f1_keywords:
- /guard
- VC.Project.VCCLCompilerTool.ControlFlowGuard
ms.assetid: be495323-f59f-4cf3-a6b6-8ee69e6a19dd
ms.openlocfilehash: e6a8a1545b97976cbe82d1c81b0e70c3dac3a266
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57807406"
---
# <a name="guard-enable-control-flow-guard"></a>/guard (włącz ochronę przepływu sterowania)

Włączanie generowania kompilatora kontroli zabezpieczeń ochrony przepływu sterowania.

## <a name="syntax"></a>Składnia

```
/guard:cf[-]
```

## <a name="remarks"></a>Uwagi

**/GUARD: CF** opcja powoduje, że kompilator, aby analizować przepływ kontroli dla pośredniego rozmów w czasie kompilacji, a następnie Wstaw kod, aby sprawdzić elementy docelowe w czasie wykonywania. Domyślnie **/GUARD: CF** jest wyłączona i musi być jawnie włączone. Aby jawnie wyłączyć tę opcję, należy użyć **/guard:cf-**.

**Visual Studio 2017 i nowszym**: Ta opcja dodaje osłony dla **Przełącz** instrukcji, które generują przejść tabel.

Gdy **/GUARD: CF** kontroli przepływu je przed nieprzewidzianymi (CFG) opcja jest określona, kompilatora i konsolidatora wstawiania dodatkowych testów środowiska uruchomieniowego zabezpieczeń wykryć próby naruszenia bezpieczeństwa kodu. Podczas kompilowania i łączenia, wszystkie pośrednie wywołania w kodzie są analizowane można znaleźć w każdej lokalizacji, która poprawnie działający kod może nawiązać połączenie. Te informacje są przechowywane w strukturach dodatkowe w nagłówkach plików binarnych. Kompilator wprowadza również wyboru przed każde wywołanie pośrednie w kodzie, który gwarantuje, że obiekt docelowy jest zweryfikowanym lokalizacji. Jeśli sprawdzenie zakończy się niepowodzeniem w czasie wykonywania w systemie operacyjnym CFG-aware, system operacyjny zamyka program.

Typowych ataków na oprogramowanie korzysta z błędów podczas obsługi extreme lub nieoczekiwany danych wejściowych. Dokładnie przygotowane dane wejściowe do aplikacji może spowodować zastąpienie lokalizacji, która zawiera wskaźnik do kodu wykonywalnego. To może służyć do przekierowania przepływ sterowania kodu kontrolowane przez osobę atakującą. Testy środowiska uruchomieniowego CFG nie rozwiązują błędy uszkodzenia danych w plik wykonywalny. Zamiast tego ułatwiają one utrudnia osobie atakującej umożliwia wykonanie dowolnego kodu. CFG jest narzędziem środki zaradcze, które uniemożliwia wywołania lokalizacjach innych niż punkty wejścia funkcji w kodzie. Jest on podobny do jak zapobieganie wykonywaniu danych (DEP) [/GS](gs-buffer-security-check.md) stosu kontroli, i [opcja/DynamicBase](dynamicbase-use-address-space-layout-randomization.md) i [/highentropyva](highentropyva-support-64-bit-aslr.md) adresów randomizacji układu przestrzeni (ASLR) niższy potencjalnych zwycięzców, kod staje się wykorzystać wektora.

**/GUARD: CF** opcji muszą zostać przekazane do obu kompilator i konsolidator, aby tworzyć kod, który używa CFG wykorzystać środki zaradcze techniki. Jeśli plik binarny został utworzony przy użyciu pojedynczej `cl` polecenia kompilatora przekazuje opcję do konsolidatora. Jeśli kompilujesz i łączysz oddzielnie, można ustawić opcji, w kompilatorze i konsolidatorze poleceń. Wymagany jest również opcja/DynamicBase — opcja konsolidatora. Aby sprawdzić, czy plik binarny zawiera dane CFG, użyj `dumpbin /headers /loadconfig` polecenia. Ma włączoną CFG pliki binarne `Guard` na liście właściwości pliku EXE lub DLL i flagi Guard obejmują `CF Instrumented` i `FID table present`.

**/GUARD: CF** opcja jest niezgodna z [/zi](z7-zi-zi-debug-information-format.md) (informacje debugowania Edytuj i Kontynuuj) lub [/CLR](clr-common-language-runtime-compilation.md) (kompilacja języka wspólnego środowiska uruchomieniowego).

Kod skompilowany przy użyciu **/GUARD: CF** mogą być połączone z biblioteki i pliki, które nie są kompilowane przy użyciu opcji obiektu. Tylko ten kod, gdy również łączone za pomocą **/GUARD: CF** opcji i uruchamiania w systemach operacyjnych obsługujących CFG, CFG ochroną. Ponieważ kod skompilowany bez opcji nie powoduje wstrzymania ataku, firma Microsoft zaleca użycie opcji na cały kod, który można skompilować. Istnieje mały środowiska uruchomieniowego, koszt CFG kontroli, ale analiza kompilator próbuje optymalizują kontrole przechodzi pośrednie, które mogą być sprawdzone bezpieczne.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji**, **C/C++**, **generowanie kodu**.

1. Wybierz **ochrony przepływu sterowania** właściwości.

1. W kontrolce listy rozwijanej wybierz **tak** można włączyć ochrony przepływu sterowania lub **nie** go wyłączyć.

## <a name="see-also"></a>Zobacz także

[MSVC Compiler Options](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
