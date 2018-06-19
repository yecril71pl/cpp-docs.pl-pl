---
title: C błąd w czasie wykonywania R6016 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6016
dev_langs:
- C++
helpviewer_keywords:
- R6016
ms.assetid: 7bd3f274-d9c4-4bc4-8252-80bf168c4c3a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f366ceff24ce65e6f7869f9709f547651687c327
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33306939"
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
  
 Firma Microsoft zaleca, aby używać pliku wykonywalnego, który wywołuje biblioteki C runtime (CRT) `_beginthreadex` tworzenia wątku zamiast interfejsu API systemu Windows dla `CreateThread`. `_beginthreadex` Inicjuje wewnętrzne statycznych Magazyn używany przez wiele funkcji CRT w lokalny magazyn wątków. Jeśli używasz `CreateThread` można utworzyć wątku, CRT może zakończyć proces o R6016, gdy połączenie jest nawiązywane w przypadku funkcji CRT, która wymaga zainicjowane pamięci statycznej wewnętrznej.