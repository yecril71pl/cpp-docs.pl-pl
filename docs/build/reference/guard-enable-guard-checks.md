---
title: -GUARD (Włącz sprawdzanie Guard) | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 6d05dd4f9d213c3d2729459486a9d0cfdbd79110
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="guard-enable-guard-checks"></a>/GUARD (włączenie sprawdzeń za pomocą wyrażenia Guard)
Określa pomoc techniczną dla kontroli zabezpieczenia przepływu sterowania w obrazu wykonywalnego.  
  
## <a name="syntax"></a>Składnia  
  
```  
/GUARD:{CF|NO}  
```  
  
## <a name="remarks"></a>Uwagi  
 Kiedy/GUARD: CF jest określona, konsolidator modyfikuje nagłówka .dll lub .exe wskazująca obsługę Sprawdzanie czasu wykonania sterowania przepływem Guard (CFG). Konsolidator dodaje również dane adresów docelowych przepływu wymaganego formantu do nagłówka. / GUARD: CF jest domyślnie wyłączona. Można ją jawnie wyłączyć przy użyciu /GUARD:NO. Było skuteczne, wymaga również/GUARD: CF [/DYNAMICBASE (randomizacji układu przestrzeni adresowej Użyj)](../../build/reference/dynamicbase-use-address-space-layout-randomization.md) — opcja konsolidatora, które jest domyślnie włączone.  
  
 Podczas kompilowania kodu źródłowego przy użyciu [/GUARD: CF](../../build/reference/guard-enable-control-flow-guard.md) opcja, kompilator analizuje przepływu sterowania, sprawdzając wszystkie pośrednie wywołania dla adresów możliwy element docelowy. Kompilator wstawia kod, aby sprawdzić, czy adres docelowy instrukcji pośrednie wywołanie znajduje się na liście adresów docelowych znane w czasie wykonywania. Sprawdź systemy operacyjne obsługujące CFG Zatrzymaj program, który zakończy się niepowodzeniem CFG runtime. Dzięki temu utrudnia osobie atakującej wykonanie złośliwego kodu za pomocą uszkodzenia danych można zmienić celu wywołania.  
  
 Należy określić opcję/GUARD: CF kompilatora i konsolidator, aby utworzyć obrazy wykonywalne włączone CFG. Kod skompilowane, ale nie są połączone za pomocą/GUARD: CF generuje koszt kontroli środowiska uruchomieniowego, ale nie włączaj ochrony CFG. Jeśli określono opcję/GUARD: CF do `cl` polecenie, aby skompilować i łącze w jednym kroku, kompilator przekazuje flagę do konsolidatora. Gdy **ochrona przepływu sterowania** właściwość jest ustawiona w programie Visual Studio, opcja/GUARD: CF jest przekazywana do kompilatorze i konsolidatorze. Gdy plików obiektu i bibliotek zostały skompilowane oddzielnie, opcja musi być jawnie określona w `link` polecenia.  
  
### <a name="to-set-this-linker-option-in-visual-studio"></a>Aby ustawić tę opcję konsolidatora w programie Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Rozwiń węzeł **właściwości konfiguracji**, **konsolidatora**, **wiersza polecenia**.  
  
3.  W **dodatkowe opcje**, wprowadź `/GUARD:CF`.  
  
## <a name="see-also"></a>Zobacz też  
 [/ GUARD (Włącz ochronę przepływu sterowania)](../../build/reference/guard-enable-control-flow-guard.md)   
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)