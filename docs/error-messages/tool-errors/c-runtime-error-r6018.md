---
title: C błąd w czasie wykonywania R6018 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6018
dev_langs:
- C++
helpviewer_keywords:
- R6018
ms.assetid: f6dd40d1-a119-4d8b-b39e-97350ea23349
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4946e3a8341963ee1a1ca2c3ad65d64cfbad8080
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33302831"
---
# <a name="c-runtime-error-r6018"></a>C R6018 błąd w czasie wykonywania
Błąd nieoczekiwany sterty  
  
> [!NOTE]
>  Jeśli wystąpią ten komunikat o błędzie podczas uruchamiania aplikacji aplikacji został wyłączony, ponieważ ma ona wystąpił problem wewnętrzny. Istnieje kilka możliwych przyczyn tego błędu, ale często jest to spowodowane usterką w kodzie aplikacji.  
>   
>  Możesz wypróbować następujące kroki, aby naprawić ten błąd:  
>   
>  -   Użyj **aplikacje i funkcje** lub **programy i funkcje** strony **Panelu sterowania** do naprawy lub ponownej instalacji programu.  
> -   Sprawdź **usługi Windows Update** w **Panelu sterowania** aktualizacji oprogramowania.  
> -   Sprawdź, czy zaktualizowaną wersję aplikacji. Jeśli problem będzie się powtarzać, skontaktuj się z dostawcą aplikacji.  
  
 **Informacje dla programistów**  
  
 Program napotkał nieoczekiwany błąd podczas wykonywania operacji zarządzania pamięcią.  
  
 Ten błąd zazwyczaj występuje, jeśli program przypadkowo zmienia danych sterty czasu wykonywania. Jednak to może również być spowodowane wewnętrznego błędu środowiska uruchomieniowego lub kod systemu operacyjnego.  
  
 Aby rozwiązać ten problem, sprawdź usterki uszkodzenie sterty w kodzie. Aby uzyskać dodatkowe informacje i przykłady, zobacz [szczegóły dotyczące sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details). Następnie sprawdź, że używasz najnowszej pakietów redystrybucyjnych dla danego wdrożenia aplikacji. Aby uzyskać informacje, zobacz [wdrożenia w programie Visual C++](../../ide/deployment-in-visual-cpp.md).