---
title: -GENPROFILE, - FASTGENPROFILE (Generuj profilowania kompilacji Instrumentowanej) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- GENPROFILE
- FASTGENPROFILE
- /GENPROFILE
- /FASTGENPROFILE
helpviewer_keywords:
- GENPROFILE
- FASTGENPROFILE
ms.assetid: deff5ce7-46f5-448a-b9cd-a7a83a6864c6
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 028b31044d035def628785969a04c27af4699f65
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="genprofile-fastgenprofile-generate-profiling-instrumented-build"></a>/ Opcję GENPROFILE, /FASTGENPROFILE (Generuj profilowania Instrumentowanej kompilacji)
Określa Generowanie pliku .pgd przez konsolidator, aby obsługiwać Optymalizacja sterowana profilem — (PGO).  / Opcję GENPROFILE i /FASTGENPROFILE parametry różne domyślne. Użyj opcji/genprofile, aby preferował dokładności nad użyciem szybkość i pamięci podczas profilowania. Użyj /FASTGENPROFILE preferować mniejsze zużycie pamięci i szybkość nad dokładności.  
  
## <a name="syntax"></a>Składnia  
  
```  
/{GENPROFILE|FASTGENPROFILE}[:{COUNTER32|COUNTER64|EXACT|MEMMAX=#|MEMMIN=#|NOEXACT|NOPATH|NOTRACKEH|PATH|PGD=filename|TRACKEH}]   
```  
  
## <a name="remarks"></a>Uwagi  
 COUNTER32 &#124; COUNTER64  
 COUNTER32 umożliwia określenie, Użyj liczników sondowania 32-bitowe i COUNTER64, aby określić liczniki sondowania 64-bitowych. Po określeniu opcji/genprofile, wartość domyślna to COUNTER64. Po określeniu /FASTGENPROFILE, wartość domyślna to COUNTER32.  
  
 DOKŁADNE &#124; NOEXACT  
 Umożliwia określenie wątkowo zwiększa blokowanego dla sondy EXACT. NOEXACT Określa przyrost niechronione operacji dla sondy. Wartość domyślna to NOEXACT.  
  
 MEMMAX = wartość, MEMMIN = wartość  
 Użyj MEMMAX i MEMMIN, aby określić rozmiar rezerwacji maksymalne i minimalne danych szkoleniowych w pamięci. Wartość to ilość pamięci do zarezerwowania w bajtach.  Domyślnie te wartości są określane przez wewnętrzny heurystycznego.  
  
 ŚCIEŻKA &#124; NOPATH  
 Aby określić osobny zestaw liczników PGO dla każdej unikatowej ścieżki do funkcji, należy użyć ścieżki. NOPATH umożliwia określenie tylko jeden zestaw liczników dla każdej funkcji.   Po określeniu opcji/genprofile, wartość domyślna to ŚCIEŻKA. Po określeniu /FASTGENPROFILE, wartość domyślna to NOPATH.  
  
 TRACKEH &#124; NOTRACKEH  
 Określa, czy zachować dokładne liczby, gdy wyjątki zostaną zgłoszone podczas uczenia przy użyciu dodatkowych liczników. Użyj TRACKEH, aby określić dodatkowe liczniki dokładne Count. Umożliwia określenie jednego liczniki dla kodu, który nie korzysta z obsługi wyjątków lub nie napotka wyjątków w Twojej scenariusze szkoleniowe NOTRACKEH.  Po określeniu opcji/genprofile, wartość domyślna to TRACKEH. Po określeniu /FASTGENPROFILE, wartość domyślna to NOTRACKEH.  
  
 PGD = filename  
 Określa nazwę pliku podstawowego plik .pgd. Domyślnie konsolidator używa nazwy pliku obrazu podstawowego pliku wykonywalnego z rozszerzeniem .pgd.  
  
 Opcje opcji/genprofile i /FASTGENPROFILE Poinformuj konsolidator, aby wygenerować profilowania pliku Instrumentacji potrzebnych do obsługi aplikacji szkoleń dla optymalizacji sterowanych profilem (PGO). Informacje dotyczące profilowania generowane przez szkolenia aplikacji jest używany jako dane wejściowe do wykonania docelowe optymalizacji całego programu podczas kompilacji.   Można ustawić dodatkowe opcje do kontrolowania różnych funkcji profilowania wydajności podczas uczenia aplikacji i tworzy. Domyślne opcje określone przez opcji/genprofile zwrócić wyników najbardziej dokładna, zwłaszcza w przypadku dużych, złożonych aplikacji wielowątkowych. Opcja /FASTGENPROFILE używa różne ustawienia domyślne niższe zużycie pamięci i zwiększyć wydajność podczas uczenia kosztem dokładności.  
  
 Informacje dotyczące profilowania są przechwytywane, po uruchomieniu instrumentowanego aplikacji po utworzeniu przy użyciu opcji/genprofile z /FASTGENPROFILE. Te informacje jest używany przez konsolidator po określeniu opcji /USEPROFILE. Więcej informacji na temat sposobu uczenia aplikacji i uzyskać szczegółowe informacje dotyczące zebranych danych Zobacz profilowana Optymalizacja.  
  
 Należy także określić opcję/LTCG po określeniu opcji/genprofile lub /FASTGENPROFILE.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)   
 [/ LTCG (Generowanie łączonych kodów czasowych)](../../build/reference/ltcg-link-time-code-generation.md)