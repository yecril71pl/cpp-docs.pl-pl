---
title: pgosweep | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- pgosweep program
- profile-guided optimizations, pgosweep
ms.assetid: f39dd3b7-1cd9-4c3b-8e8b-fb794744b757
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 78ae6c36011e3c10359988cf2c501514d1bcf70a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="pgosweep"></a>pgosweep
Używane w Optymalizacja sterowana profilem, aby zapisać wszystkie dane profilu z uruchomiony program plik .pgc.  
  
## <a name="syntax"></a>Składnia  
  
```  
pgosweep [options] image pgcfile  
```  
  
#### <a name="parameters"></a>Parametry  
 `options`  
 Opcjonalny parametr, który może być puste. Prawidłowe wartości dla `options` są następujące:  
  
-   **/?** lub **/Help,** wyświetla komunikat pomocy.  
  
-   **/noreset,** zachowuje liczba w strukturach danych w czasie wykonywania.  
  
 `image`  
 Pełna ścieżka pliku .exe lub .dll, który został utworzony przy użyciu /LTCG:PGINSTRUMENT — opcja kompilatora.  
  
 `pgcfile`  
 Plik .pgc, w którym to polecenie będzie zapisywać dane liczby.  
  
## <a name="remarks"></a>Uwagi  
 To polecenie działa programów, które nie zostały skompilowane /LTCG:PGINSTRUMENT — opcja kompilatora. Przerywa uruchomiony program, a zapisuje dane profilu do nowego pliku .pgc. Domyślnie polecenie resetuje licznik po zakończeniu każdej operacji zapisu. Jeśli określisz **/noreset** opcji polecenia zapisać wartości, ale nie ich ponownie w uruchomiony program. Ta opcja udostępnia zduplikowane dane Jeśli później pobrać dane profilu.  
  
 Alternatywnego wykorzystania `pgosweep` pobieranie informacji o profilu tylko dla środowiska uruchomieniowego aplikacji. Na przykład można uruchomić `pgosweep` wkrótce po uruchomić aplikację i odrzucić tego pliku. Spowoduje to usunięcie profilu dane skojarzone z kosztami uruchomienia. Następnie można uruchomić `pgosweep` przed zakończeniem aplikacji. Zebrane dane ma teraz informacje o profilu tylko w czasie wykonywania.  
  
 Jeśli nazwa pliku .pgc (`pgcfile`) można użyć standardowego formatu, który jest *appname! n*.pgc. Jeśli używasz tego formatu, kompilator znajdzie te dane w fazie /LTCG:PGO. Jeśli nie używasz standardowego formatu, należy użyć [pgomgr](../../build/reference/pgomgr.md) można scalić plików PGC.  
  
## <a name="example"></a>Przykład  
  
```  
pgosweep myapp.exe myapp!1.pgc  
```  
  
 W tym przykładzie `pgosweep` zapisuje informacji o bieżącym profilu dla myapp.exe myapp!1.pgc.  
  
## <a name="see-also"></a>Zobacz też  
 [Narzędzia do ręcznej optymalizacji sterowanej profilem](../../build/reference/tools-for-manual-profile-guided-optimization.md)