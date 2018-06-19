---
title: C błąd w czasie wykonywania R6032 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6032
dev_langs:
- C++
helpviewer_keywords:
- R6032
ms.assetid: 52092a63-cc51-444a-bfc3-fad965a3558e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1f82690dd9b8f7c224db473b15627b632dcc96d8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33297875"
---
# <a name="c-runtime-error-r6032"></a>C R6032 błąd w czasie wykonywania
Brak wystarczającej ilości miejsca dla informacji o ustawieniach regionalnych  
  
> [!NOTE]
>  Jeśli wystąpią ten komunikat o błędzie podczas uruchamiania aplikacji aplikacji został wyłączony, ponieważ wystąpił problem wewnętrzny pamięci. Istnieje kilka możliwych przyczyn tego błędu, ale często spowodowane przez warunek bardzo małej ilości pamięci lub usterki w programie.  
>   
>  Możesz wypróbować następujące kroki, aby naprawić ten błąd:  
>   
>  -   Zamknij inne uruchomione aplikacje lub uruchom ponownie komputer, aby zwolnić pamięć.  
> -   Użyj **aplikacje i funkcje** lub **programy i funkcje** strony **Panelu sterowania** do naprawy lub ponownej instalacji programu.  
> -   Sprawdź **usługi Windows Update** w **Panelu sterowania** aktualizacji oprogramowania.  
> -   Sprawdź, czy zaktualizowaną wersję aplikacji. Jeśli problem będzie się powtarzać, skontaktuj się z dostawcą aplikacji.  
  
 **Informacje dla programistów**  
  
 Środowisko uruchomieniowe przechowuje informacje dotyczące ustawień regionalnych na każdy wątek, aby mógł on przetwarzać wywołania funkcji zależne od ustawień regionalnych. Jeśli alokacji pamięci dla tych informacji nie powiedzie się, środowiska uruchomieniowego nie może kontynuować, ponieważ zbyt wiele urządzeń podstawowych zależą od niej.