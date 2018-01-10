---
title: "C błąd w czasie wykonywania R6008 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: R6008
dev_langs: C++
helpviewer_keywords: R6008
ms.assetid: f0f304fc-709a-4843-bc7e-bad1ae0d1649
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 86b64f97768359b95d2c5e2003cfb5b95a2aac71
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="c-runtime-error-r6008"></a>C R6008 błąd w czasie wykonywania
Brak wystarczającej ilości miejsca dla argumentów  
  
> [!NOTE]
>  Jeśli wystąpią ten komunikat o błędzie podczas uruchamiania aplikacji aplikacji został wyłączony, ponieważ wystąpił problem wewnętrzny pamięci. Istnieje kilka możliwych przyczyn tego błędu, ale często jest to spowodowane warunek bardzo małej ilości pamięci, zbyt dużej ilości pamięci, zmienne środowiskowe lub usterki w programie.  
>   
>  Możesz wypróbować następujące kroki, aby naprawić ten błąd:  
>   
>  -   Zamknij inne uruchomione aplikacje lub uruchom ponownie komputer, aby zwolnić pamięć.  
> -   Zmniejsz liczbę i rozmiar argumenty wiersza polecenia do aplikacji.  
> -   Użyj **aplikacje i funkcje** lub **programy i funkcje** strony **Panelu sterowania** do naprawy lub ponownej instalacji programu.  
> -   Sprawdź **usługi Windows Update** w **Panelu sterowania** aktualizacji oprogramowania.  
> -   Sprawdź, czy zaktualizowaną wersję aplikacji. Jeśli problem będzie się powtarzać, skontaktuj się z dostawcą aplikacji.  
  
 **Informacje dla programistów**  
  
 Znaleziono wystarczającej ilości pamięci, aby załadować program, ale nie ma wystarczającej ilości pamięci do utworzenia **ARGV —** tablicy. Może to być spowodowane przez warunki bardzo małej ilości pamięci lub zbyt duże wiersze polecenia lub użycie zmiennej środowiskowej. Weź pod uwagę jedną z następujących rozwiązań:  
  
-   Zwiększ ilość pamięci dostępnej dla programu.  
  
-   Zmniejsz liczbę i rozmiar argumenty wiersza polecenia.  
  
-   Zmniejsz rozmiar środowiska, usuwając zbędne zmienne.