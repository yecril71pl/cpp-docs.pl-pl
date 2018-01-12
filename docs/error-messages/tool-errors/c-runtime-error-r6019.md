---
title: "C błąd w czasie wykonywania R6019 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: R6019
dev_langs: C++
helpviewer_keywords: R6019
ms.assetid: 8129923e-7db2-40ee-9602-def9365f8d28
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9c0e027907476eeacf10515556544160e402cd0e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="c-runtime-error-r6019"></a>C R6019 błąd w czasie wykonywania
Nie można otworzyć konsoli urządzenia  
  
> [!NOTE]
>  Jeśli wystąpią ten komunikat o błędzie podczas uruchamiania aplikacji aplikacji został wyłączony, ponieważ próbowano uzyskać dostęp z konsoli, ale nie ma wystarczających uprawnień. Istnieje kilka możliwych przyczyn tego błędu, ale zwykle jest to spowodowane należy uruchomić program jako administrator lub jest to błąd w programie.  
>   
>  Możesz wypróbować następujące kroki, aby naprawić ten błąd:  
>   
>  -   Uruchom program jako administrator.  
> -   Użyj **aplikacje i funkcje** lub **programy i funkcje** strony **Panelu sterowania** do naprawy lub ponownej instalacji programu.  
> -   Sprawdź **usługi Windows Update** w **Panelu sterowania** aktualizacji oprogramowania.  
> -   Sprawdź, czy zaktualizowaną wersję aplikacji. Jeśli problem będzie się powtarzać, skontaktuj się z dostawcą aplikacji.  
  
 **Informacje dla programistów**  
  
 Ten błąd występuje, ponieważ aplikacja o nazwie funkcji konsoli, ale system operacyjny nie przyznała dostępu do konsoli. Z wyjątkiem w trybie debugowania, funkcje konsoli zazwyczaj nie są dozwolone w aplikacji ze Sklepu Windows. Jeśli aplikacja wymaga uprawnień administratora do uruchomienia, upewnij się, że jest zainstalowana do uruchamiania jako administrator, domyślnie.