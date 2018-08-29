---
title: -guard (Włącz ochronę przepływu sterowania) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /guard
- VC.Project.VCCLCompilerTool.ControlFlowGuard
dev_langs:
- C++
ms.assetid: be495323-f59f-4cf3-a6b6-8ee69e6a19dd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6c65bafc14f5ef29db89ddc0a4647193231f7e19
ms.sourcegitcommit: f7703076b850c717c33d72fb0755fbb2215c5ddc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/28/2018
ms.locfileid: "43131673"
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
  
 Typowych ataków na oprogramowanie korzysta z błędów podczas obsługi extreme lub nieoczekiwany danych wejściowych. Dokładnie przygotowane dane wejściowe do aplikacji może spowodować zastąpienie lokalizacji, która zawiera wskaźnik do kodu wykonywalnego. To może służyć do przekierowania przepływ sterowania kodu kontrolowane przez osobę atakującą. Testy środowiska uruchomieniowego CFG nie rozwiązują błędy uszkodzenia danych w plik wykonywalny. Zamiast tego ułatwiają one utrudnia osobie atakującej umożliwia wykonanie dowolnego kodu. CFG jest narzędziem środki zaradcze, które uniemożliwia wywołania lokalizacjach innych niż punkty wejścia funkcji w kodzie. Jest on podobny do jak zapobieganie wykonywaniu danych (DEP) [/GS](../../build/reference/gs-buffer-security-check.md) stosu kontroli, i [opcja/DynamicBase](../../build/reference/dynamicbase-use-address-space-layout-randomization.md) i [/highentropyva](../../build/reference/highentropyva-support-64-bit-aslr.md) adresów randomizacji układu przestrzeni (ASLR) niższy potencjalnych zwycięzców, kod staje się wykorzystać wektora.  
  
 **/GUARD: CF** opcji muszą zostać przekazane do obu kompilator i konsolidator, aby tworzyć kod, który używa CFG wykorzystać środki zaradcze techniki. Jeśli plik binarny został utworzony przy użyciu pojedynczej `cl` polecenia kompilatora przekazuje opcję do konsolidatora. Jeśli kompilujesz i łączysz oddzielnie, można ustawić opcji, w kompilatorze i konsolidatorze poleceń. Wymagany jest również opcja/DynamicBase — opcja konsolidatora. Aby sprawdzić, czy plik binarny zawiera dane CFG, użyj `dumpbin /headers /loadconfig` polecenia. Ma włączoną CFG pliki binarne `Guard` na liście właściwości pliku EXE lub DLL i flagi Guard obejmują `CF Instrumented` i `FID table present`.  
  
 **/GUARD: CF** opcja jest niezgodna z [/zi](../../build/reference/z7-zi-zi-debug-information-format.md) (informacje debugowania Edytuj i Kontynuuj) lub [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) (kompilacja języka wspólnego środowiska uruchomieniowego).  
  
 Kod skompilowany przy użyciu **/GUARD: CF** mogą być połączone z biblioteki i pliki, które nie są kompilowane przy użyciu opcji obiektu. Tylko ten kod, gdy również łączone za pomocą **/GUARD: CF** opcji i uruchamiania w systemach operacyjnych obsługujących CFG, CFG ochroną. Ponieważ kod skompilowany bez opcji nie powoduje wstrzymania ataku, firma Microsoft zaleca użycie opcji na cały kod, który można skompilować. Istnieje mały środowiska uruchomieniowego, koszt CFG kontroli, ale analiza kompilator próbuje optymalizują kontrole przechodzi pośrednie, które mogą być sprawdzone bezpieczne.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Wybierz **właściwości konfiguracji**, **C/C++**, **generowanie kodu**.  
  
3.  Wybierz **ochrony przepływu sterowania** właściwości.  
  
4.  W kontrolce listy rozwijanej wybierz **tak** można włączyć ochrony przepływu sterowania lub **nie** go wyłączyć.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)