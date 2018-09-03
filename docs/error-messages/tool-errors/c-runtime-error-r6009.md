---
title: C błąd w czasie wykonywania R6009 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6009
dev_langs:
- C++
helpviewer_keywords:
- R6009
ms.assetid: edfb1f8b-3807-48f4-a994-318923b747ae
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2c44c08ec3b52cc53e1b29a0ecf23606c3ec06a4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33296851"
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