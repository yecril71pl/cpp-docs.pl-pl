---
title: R6025 błąd środowiska uruchomieniowego języka C | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6025
dev_langs:
- C++
helpviewer_keywords:
- R6025
ms.assetid: afa06d98-9c36-445b-b3e7-b6409bc8e779
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b774c5f99387ca4403941d1461593bef8801e5de
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43220635"
---
# <a name="c-runtime-error-r6025"></a>R6025 błąd środowiska uruchomieniowego języka C
Wywołanie czystych funkcji wirtualnych  
  
> [!NOTE]
>  Jeśli napotkasz ten komunikat o błędzie podczas działania aplikacji, aplikacji został zamknięty, ponieważ ma on wewnętrzny problem. Najbardziej typową przyczyną tego błędu jest to błąd w aplikacji lub uszkodzenie instalacji.  
>   
>  Możesz wypróbować następujące kroki, aby naprawić ten błąd:  
>   
>  -   Użyj **aplikacje i funkcje** lub **programy i funkcje** strony w **Panelu sterowania** naprawić lub zainstalować ponownie program.  
> -   Sprawdź **Windows Update** w **Panelu sterowania** aktualizacji oprogramowania.  
> -   Sprawdź, czy zaktualizowaną wersję aplikacji. Jeśli problem będzie się powtarzać, skontaktuj się z dostawcą aplikacji.  
  
 **Informacje dla programistów**  
  
 Żaden obiekt nie został uruchomiony obsłużyć wywołania czystą funkcję wirtualną.  
  
 Ten błąd jest spowodowany przez wywołanie funkcji wirtualnej w abstrakcyjna klasa bazowa, za pomocą wskaźnika, który jest tworzony przez rzutowanie na typ klasy pochodnej, ale jest właściwie wskaźnikiem do klasy bazowej. Taka sytuacja może wystąpić, gdy rzutowanie z **void** <strong>\*</strong> na wskaźnik do klasy podczas **void** <strong>\*</strong> został tworzone podczas tworzenia klasy bazowej.  
  
 Aby uzyskać więcej informacji, zobacz [pomocy technicznej firmy Microsoft](http://go.microsoft.com/fwlink/p/?linkid=75220) witryny sieci Web.