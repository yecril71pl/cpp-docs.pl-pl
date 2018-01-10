---
title: "C błąd w czasie wykonywania R6026 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: R6026
dev_langs: C++
helpviewer_keywords: R6026
ms.assetid: 7ea751f8-fc20-46ab-99ef-84c95ca0b6b4
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a0baa9806476534bd877f8177d20bbe9da80d3da
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="c-runtime-error-r6026"></a>C R6026 błąd w czasie wykonywania
Brak wystarczającej ilości miejsca dla stdio — inicjowanie  
  
> [!NOTE]
>  Jeśli wystąpią ten komunikat o błędzie podczas uruchamiania aplikacji aplikacji został wyłączony, ponieważ wystąpił problem wewnętrzny pamięci. Istnieje kilka możliwych przyczyn tego błędu, ale zazwyczaj spowodowane warunek bardzo małej ilości pamięci. Może być również spowodowane przez usterkę w aplikacji, uszkodzenie bibliotek języka Visual C++, których używa lub sterownika.  
>   
>  Możesz wypróbować następujące kroki, aby naprawić ten błąd:  
>   
>  -   Zamknij inne uruchomione aplikacje lub uruchom ponownie komputer, aby zwolnić pamięć.  
> -   Użyj **aplikacje i funkcje** lub **programy i funkcje** strony **Panelu sterowania** do naprawy lub ponownej instalacji programu.  
> -   Jeśli aplikacja pracy przed Ostatnia instalacja innej aplikacji lub sterownika, użyj **aplikacje i funkcje** lub **programy i funkcje** strony **Panelu sterowania** do usunięcia Nowa aplikacja lub sterowników i spróbuj ponownie aplikację.  
> -   Użyj **aplikacje i funkcje** lub **programy i funkcje** strony **Panelu sterowania** do naprawy lub ponownej instalacji wszystkich kopii programu Microsoft Visual C++ Redistributable.  
> -   Sprawdź **usługi Windows Update** w **Panelu sterowania** aktualizacji oprogramowania.  
> -   Sprawdź, czy zaktualizowaną wersję aplikacji. Jeśli problem będzie się powtarzać, skontaktuj się z dostawcą aplikacji.  
  
 **Informacje dla programistów**  
  
 Ten błąd występuje, gdy nie ma wystarczającej ilości pamięci do zainicjować standard obsługi operacji We/Wy w środowisku wykonawczym C. Ten błąd zazwyczaj występuje podczas uruchamiania aplikacji. Upewnij się, że aplikacji i sterowników i bibliotek DLL, który ładuje nie uszkodzenie sterty przy uruchamianiu.