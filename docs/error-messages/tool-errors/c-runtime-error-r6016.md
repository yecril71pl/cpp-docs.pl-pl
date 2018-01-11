---
title: "C błąd w czasie wykonywania R6016 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: R6016
dev_langs: C++
helpviewer_keywords: R6016
ms.assetid: 7bd3f274-d9c4-4bc4-8252-80bf168c4c3a
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 451ff01b201b110ac5f05140e3b8581f1a8c2e28
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="c-runtime-error-r6016"></a>C R6016 błąd w czasie wykonywania
za mało miejsca dla danych wątku  
  
> [!NOTE]
>  Jeśli wystąpią ten komunikat o błędzie podczas uruchamiania aplikacji aplikacji został wyłączony, ponieważ wystąpił problem wewnętrzny pamięci. Istnieje wiele możliwych przyczyn tego błędu, ale często spowodowane przez warunek bardzo małej ilości pamięci z błędem w aplikacji, lub na usterkę w dodatku lub rozszerzenia używane przez aplikację.  
>   
>  Możesz wypróbować następujące kroki, aby naprawić ten błąd:  
>   
>  -   Zamknij inne uruchomione aplikacje lub uruchom ponownie komputer, aby zwolnić pamięć.  
> -   Użyj **aplikacje i funkcje** lub **programy i funkcje** strony **Panelu sterowania** do naprawy lub ponownej instalacji aplikacji.  
> -   Użyj **aplikacje i funkcje** lub **programy i funkcje** strony **Panelu sterowania** do usunięcia, napraw lub ponownie zainstalować dodatki i rozszerzenia używane przez aplikację.  
> -   Sprawdź **usługi Windows Update** w **Panelu sterowania** aktualizacji oprogramowania.  
> -   Sprawdź, czy zaktualizowaną wersję aplikacji. Jeśli problem będzie się powtarzać, skontaktuj się z dostawcą aplikacji.  
  
 **Informacje dla programistów**  
  
 Ten błąd występuje, ponieważ program nie odebrała za mało pamięci systemu operacyjnego, aby ukończyć [_beginthread —](../../c-runtime-library/reference/beginthread-beginthreadex.md) lub `_beginthreadex` wywołania lub lokalnego magazynu nie została zainicjowana przez wątek `_beginthread` lub `_beginthreadex`.  
  
 W momencie rozpoczynania nowego wątku biblioteka musi utworzyć wewnętrzną bazę danych dla tego wątku. Jeśli baza danych nie może zostać rozszerzona przy użyciu pamięci dostarczonej przez system operacyjny, wątek się nie rozpoczyna, a proces wywołujący się zatrzymuje. Może się to zdarzyć, gdy proces utworzył zbyt wiele wątków lub gdy pamięć lokalna wątku została wyczerpana.  
  
 Firma Microsoft zaleca, aby używać pliku wykonywalnego, który wywołuje biblioteki C runtime (CRT) `_beginthreadex` tworzenia wątku zamiast interfejsu API systemu Windows dla `CreateThread`. `_beginthreadex`Inicjuje wewnętrzne statycznych Magazyn używany przez wiele funkcji CRT w lokalny magazyn wątków. Jeśli używasz `CreateThread` można utworzyć wątku, CRT może zakończyć proces o R6016, gdy połączenie jest nawiązywane w przypadku funkcji CRT, która wymaga zainicjowane pamięci statycznej wewnętrznej.