---
title: -guard (Włącz ochrona przepływu sterowania) | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: b5c60ff444189e9e6b7919b43649b75722ee7249
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32377407"
---
# <a name="guard-enable-control-flow-guard"></a>/guard (włącz ochronę przepływu sterowania)
Włącz generowanie kompilatora kontroli zabezpieczeń Guard przepływu sterowania.  
  
## <a name="syntax"></a>Składnia  
  
```  
/guard:cf[-]  
```  
  
## <a name="remarks"></a>Uwagi  
 **/GUARD: CF** opcja powoduje, że kompilator, aby przeanalizować przepływ kontroli dla pośredniego rozmów w czasie kompilacji, a następnie Wstaw kod, aby zweryfikować elementy docelowe w czasie wykonywania. Domyślnie **/GUARD: CF** jest wyłączony, a musi być jawnie włączone. Aby jawnie wyłączyć tę opcję, należy użyć **/guard:cf-**.  
  
 Gdy **/GUARD: CF** zostanie określona opcja sterowania przepływem zabezpieczenia (CFG), kompilatorze i konsolidatorze wstawiania runtime dodatkowe kontrole zabezpieczeń wykrywanie prób złamania kodu. Podczas kompilowania kodu i łącząc, wszystkie pośrednie wywołania w kodzie są analizowane można znaleźć każdej lokalizacji poprawnie działający kod może nawiązać połączenie. Te informacje są przechowywane w strukturach dodatkowe w nagłówkach Twoje pliki binarne. Kompilator injects również wyboru przed co pośrednie wywołanie w kodzie, które zapewnia, że element docelowy stanowi jedną z lokalizacji zweryfikowane. Jeśli sprawdzenie zakończy się niepowodzeniem w czasie wykonywania na system operacyjny obsługujący CFG, system operacyjny zamyka program.  
  
 Typowe ataków na oprogramowanie korzysta z usterki w programie obsługi danych wejściowych extreme lub nieoczekiwany. Starannie przygotowanego danych wejściowych do aplikacji może spowodować zastąpienie lokalizacji, która zawiera wskaźnik do kodu wykonywalnego. Może to służyć do przekierowania przepływu sterowania do kodu kontrolowane przez osobę atakującą. Sprawdzanie czasu wykonania CFG nie rozwiązują usterki uszkodzenie danych w pliku wykonywalnego. One zamiast utrudnić atakujący może użyć ich do wykonania dowolnego kodu. CFG to narzędzie środki zaradcze, które zapobiega wywołania do lokalizacji innych niż punkty wejścia funkcji w kodzie. Podobnie jak jest funkcja Zapobieganie wykonywaniu danych (DEP) [/GS](../../build/reference/gs-buffer-security-check.md) stosu kontroli, i [/DYNAMICBASE](../../build/reference/dynamicbase-use-address-space-layout-randomization.md) i [/highentropyva](../../build/reference/highentropyva-support-64-bit-aslr.md) adresów randomizacji układu przestrzeni (ASLR) niższy szanse, że kod staje się wykorzystać wektora.  
  
 **/GUARD: CF** opcji muszą być przekazywane do obu kompilatora i konsolidatora do kompilacji kodu, który używa CFG wykorzystać technika środki zaradcze. Jeśli Twoje dane binarne jest zbudowany przy użyciu pojedynczej `cl` polecenia kompilatora przekazuje opcji do konsolidatora. Jeśli kompilowanie i łączenie oddzielnie, można ustawić opcji, w kompilatorze i konsolidatorze poleceń. Wymagany jest również /DYNAMICBASE — opcja konsolidatora. Aby sprawdzić, czy z danych binarnych zawiera dane CFG, użyj `dumpbin /headers /loadconfig` polecenia. Mają włączoną CFG plików binarnych `Guard` na liście właściwości plik EXE lub DLL i flagi Guard obejmują `CF Instrumented` i `FID table present`.  
  
 **/GUARD: CF** opcja jest niezgodna z [/zi](../../build/reference/z7-zi-zi-debug-information-format.md) (informacje debugowania Edytuj i Kontynuuj) lub [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) (kompilacja języka wspólnego środowiska uruchomieniowego).  
  
 Kodu skompilowanego za pomocą **/GUARD: CF** może odnosić się do bibliotek i obiektu pliki, które nie są kompilowane przy użyciu opcji. Tylko tego kodu, gdy są również połączone za pomocą **/GUARD: CF** opcji i obsługujący CFG system operacyjny, ma CFG ochrony. Ponieważ skompilowany bez opcji Kod lokacji nie zatrzyma ataku, zaleca się użycie opcji kod, który można skompilować. Brak małych środowisko uruchomieniowe koszt CFG kontroli, ale analizy kompilatora próbuje zoptymalizować optymalizacji kontrole przechodzi pośrednich, które mogą być sprawdzone bezpieczne.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Wybierz **właściwości konfiguracji**, **C/C++**, **generowanie kodu**.  
  
3.  Wybierz **ochrona przepływu sterowania** właściwości.  
  
4.  Za pomocą kontrolki rozwijanej wybierz **tak** umożliwiające ochrona przepływu sterowania lub **nr** je wyłączyć.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)