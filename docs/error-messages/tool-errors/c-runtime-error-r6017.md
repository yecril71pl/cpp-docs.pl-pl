---
title: "C błąd w czasie wykonywania R6017 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: R6017
dev_langs: C++
helpviewer_keywords: R6017
ms.assetid: df3ec5f5-6771-4648-ba06-0e26c6a1cc6a
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6a4e4b1be6bb6323702b72d99be88824d456243b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="c-runtime-error-r6017"></a>C R6017 błąd w czasie wykonywania
Błąd nieoczekiwany blokady wielowątkowe  
  
> [!NOTE]
>  Jeśli wystąpią ten komunikat o błędzie podczas uruchamiania aplikacji aplikacji został wyłączony, ponieważ ma ona wystąpił problem wewnętrzny. Istnieje kilka możliwych przyczyn tego błędu, ale często jest to spowodowane usterką w kodzie aplikacji.  
>   
>  Możesz wypróbować następujące kroki, aby naprawić ten błąd:  
>   
>  -   Użyj **aplikacje i funkcje** lub **programy i funkcje** strony **Panelu sterowania** do naprawy lub ponownej instalacji programu.  
> -   Sprawdź **usługi Windows Update** w **Panelu sterowania** aktualizacji oprogramowania.  
> -   Sprawdź, czy zaktualizowaną wersję aplikacji. Jeśli problem będzie się powtarzać, skontaktuj się z dostawcą aplikacji.  
  
 **Informacje dla programistów**  
  
 Proces Odebrano nieoczekiwany błąd podczas próby uzyskania dostępu C runtime wielowątkowe blokady dla zasobu systemowego. Ten błąd występuje zazwyczaj, jeśli proces przypadkowo zmienia danych sterty środowiska wykonawczego. Jednak to może również być spowodowane błąd wewnętrzny w bibliotece środowiska uruchomieniowego lub kod systemu operacyjnego.  
  
 Aby rozwiązać ten problem, sprawdź usterki uszkodzenie sterty w kodzie. Aby uzyskać dodatkowe informacje i przykłady, zobacz [szczegóły dotyczące sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details). Następnie sprawdź, że używasz najnowszej pakietów redystrybucyjnych dla danego wdrożenia aplikacji. Aby uzyskać informacje, zobacz [wdrożenia w programie Visual C++](../../ide/deployment-in-visual-cpp.md).