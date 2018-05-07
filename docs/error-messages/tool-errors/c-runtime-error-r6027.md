---
title: C błąd w czasie wykonywania R6027 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6027
dev_langs:
- C++
helpviewer_keywords:
- R6027
ms.assetid: c06a62b3-08d9-4bf5-bcad-8340ec552f69
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cc38d664a6c9e2e2be0c360709ed6b39b1014b05
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="c-runtime-error-r6027"></a>C R6027 błąd w czasie wykonywania
Brak wystarczającej ilości miejsca do zainicjowania lowio  
  
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
  
 Ten błąd występuje, gdy nie ma wystarczającej ilości wolnego dostępnej pamięci, aby zainicjować obsługi operacji We/Wy niskiego poziomu, w środowisku wykonawczym C. Ten błąd zazwyczaj występuje podczas uruchamiania aplikacji. Upewnij się, że aplikacji i sterowników i bibliotek DLL, który ładuje nie uszkodzenie sterty przy uruchamianiu.