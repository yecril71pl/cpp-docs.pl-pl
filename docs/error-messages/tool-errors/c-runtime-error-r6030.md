---
title: "C Runtime błąd r6030 środowiska języka | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- R6030
dev_langs:
- C++
helpviewer_keywords:
- R6030
ms.assetid: 0238a6c3-a033-4046-8adc-f8f99d961153
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7bc7c5db2b486ef051975c0e8d31d6c24ca5aa6a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="c-runtime-error-r6030"></a>R6030 środowiska języka C błąd w czasie wykonywania
Nie zainicjowano CRT  
  
> [!NOTE]
>  Jeśli wystąpią ten komunikat o błędzie podczas uruchamiania aplikacji aplikacji został wyłączony, ponieważ ma ona wystąpił problem wewnętrzny. Ten problem jest najczęściej spowodowane przez niektóre programy zabezpieczeń, lub rzadko, usterki w programie.  
>   
>  Możesz wypróbować następujące kroki, aby naprawić ten błąd:  
>   
>  -   Oprogramowanie zabezpieczające może być szczegółowych instrukcji dotyczących zmniejszenia ten problem. Sprawdź witryny sieci Web dostawcy oprogramowania zabezpieczeń, aby uzyskać szczegółowe informacje. Alternatywnie Sprawdź zaktualizowane wersje oprogramowania zabezpieczeń lub spróbuj zabezpieczeń innego oprogramowania.  
> -   Użyj **aplikacje i funkcje** lub **programy i funkcje** strony **Panelu sterowania** do naprawy lub ponownej instalacji programu.  
> -   Sprawdź **usługi Windows Update** w **Panelu sterowania** aktualizacji oprogramowania.  
> -   Sprawdź, czy zaktualizowaną wersję aplikacji. Jeśli problem będzie się powtarzać, skontaktuj się z dostawcą aplikacji.  
  
 **Informacje dla programistów**  
  
 Ten błąd występuje, jeśli używasz C Runtime (CRT), ale kod uruchomienia CRT nie zostało wykonane. Istnieje możliwość ten błąd, jeśli przełącznik konsolidatora [/Entry](../../build/reference/entry-entry-point-symbol.md) służy do zastępowania domyślnej początkowy adres, zwykle **mainCRTStartup**, **wmainCRTStartup** dla konsoli EXE, **WinMainCRTStartup** lub **wWinMainCRTStartup** dla systemu Windows wywołanie pliku EXE lub **_DllMainCRTStartup** dla biblioteki DLL. Jeśli nie jest jedną z powyższych funkcji wywoływana podczas uruchamiania, nie można zainicjować C Runtime. Te funkcje uruchamiania zwykle są nazywane domyślnie po link do biblioteki C runtime i przy użyciu normalnych **głównego**, **wmain**, **WinMain**, lub  **DllMain** punktów wejścia.  
  
 Istnieje również możliwość ten błąd, gdy inny program używa techniki iniekcji kodu pułapki pewne wywołania biblioteki DLL. Niektóre programy zabezpieczające niepożądanych użyć tej metody. W wersjach programu Visual C++ przed Visual Studio 2015 można używać biblioteki CRT statycznie połączone, aby rozwiązać ten problem, ale nie jest to zalecane ze względu na aktualizacje zabezpieczeń i aplikacji. Naprawienia tego problemu może wymagać akcji przez użytkownika końcowego.