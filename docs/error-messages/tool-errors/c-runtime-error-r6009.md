---
title: "C błąd w czasie wykonywania R6009 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- R6009
dev_langs:
- C++
helpviewer_keywords:
- R6009
ms.assetid: edfb1f8b-3807-48f4-a994-318923b747ae
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 137bb74bcc091721633fe22fc9c56ef6ce99a535
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="c-runtime-error-r6009"></a>C R6009 błąd w czasie wykonywania
Brak wystarczającej ilości miejsca dla środowiska  
  
> [!NOTE]
>  Jeśli wystąpią ten komunikat o błędzie podczas uruchamiania aplikacji aplikacji został wyłączony, ponieważ wystąpił problem wewnętrzny pamięci. Istnieje kilka możliwych przyczyn tego błędu, ale często jest to spowodowane warunek bardzo małej ilości pamięci, zbyt dużej ilości pamięci, zmienne środowiskowe lub usterki w programie.  
>   
>  Możesz wypróbować następujące kroki, aby naprawić ten błąd:  
>   
>  -   Zamknij inne uruchomione aplikacje lub uruchom ponownie komputer, aby zwolnić pamięć.  
> -   Użyj **aplikacje i funkcje** lub **programy i funkcje** strony **Panelu sterowania** do naprawy lub ponownej instalacji programu.  
> -   Sprawdź **usługi Windows Update** w **Panelu sterowania** aktualizacji oprogramowania.  
> -   Sprawdź, czy zaktualizowaną wersję aplikacji. Jeśli problem będzie się powtarzać, skontaktuj się z dostawcą aplikacji.  
  
 **Informacje dla programistów**  
  
 Znaleziono wystarczającej ilości pamięci, aby załadować program, ale nie ma wystarczającej ilości pamięci do utworzenia **envp —** tablicy.  Przyczyną może być bardzo niedobór pamięci lub środowiska zbyt duże użycie zmiennej. Weź pod uwagę jedną z następujących rozwiązań:  
  
-   Zwiększ ilość pamięci dostępnej dla programu.  
  
-   Zmniejsz liczbę i rozmiar argumenty wiersza polecenia.  
  
-   Zmniejsz rozmiar środowiska, usuwając zbędne zmienne.