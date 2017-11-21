---
title: "C błąd w czasie wykonywania R6024 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: R6024
dev_langs: C++
helpviewer_keywords: R6024
ms.assetid: 0fb11c0f-9b81-4cab-81bd-4785742946a5
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2d032bbcb6e28d78f5e43b9c12499c6d47ca0310
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="c-runtime-error-r6024"></a>C R6024 błąd w czasie wykonywania
Brak wystarczającej ilości miejsca dla tabeli _onexit — / funkcji atexit  
  
> [!NOTE]
>  Jeśli wystąpią ten komunikat o błędzie podczas uruchamiania aplikacji aplikacji został wyłączony, ponieważ wystąpił problem wewnętrzny pamięci. Zazwyczaj przyczyną tego błędu, stan bardzo małej ilości pamięci lub rzadko, usterki w programie lub uszkodzeniem bibliotek języka Visual C++, których używa.  
>   
>  Możesz wypróbować następujące kroki, aby naprawić ten błąd:  
>   
>  -   Zamknij inne uruchomione aplikacje lub uruchom ponownie komputer, aby zwolnić pamięć.  
> -   Użyj **aplikacje i funkcje** lub **programy i funkcje** strony **Panelu sterowania** do naprawy lub ponownej instalacji programu.  
> -   Użyj **aplikacje i funkcje** lub **programy i funkcje** strony **Panelu sterowania** do naprawy lub ponownej instalacji wszystkich kopii programu Microsoft Visual C++ Redistributable.  
> -   Sprawdź **usługi Windows Update** w **Panelu sterowania** aktualizacji oprogramowania.  
> -   Sprawdź, czy zaktualizowaną wersję aplikacji. Jeśli problem będzie się powtarzać, skontaktuj się z dostawcą aplikacji.  
  
 **Informacje dla programistów**  
  
 Ten błąd występuje, ponieważ nie było Brak pamięci dla `_onexit` lub `atexit` funkcji. Ten błąd jest spowodowany przez niedostatecznej ilości pamięci. Można rozważyć wstępnie przydzielania buforów przy uruchamianiu aplikacji ułatwiających zapisywania danych użytkownika i wykonywanie czystej aplikacji zakończyć w warunkach ilości pamięci.