---
title: "C błąd w czasie wykonywania R6025 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: R6025
dev_langs: C++
helpviewer_keywords: R6025
ms.assetid: afa06d98-9c36-445b-b3e7-b6409bc8e779
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 06fd7aa6458a3c7e89d80146ec20a0e3f7587b4b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="c-runtime-error-r6025"></a>C R6025 błąd w czasie wykonywania
Wywołanie czystej funkcji wirtualnej  
  
> [!NOTE]
>  Jeśli wystąpią ten komunikat o błędzie podczas uruchamiania aplikacji aplikacji został wyłączony, ponieważ ma ona wystąpił problem wewnętrzny. Najczęstszą przyczyną tego błędu jest to błąd w aplikacji lub uszkodzenie instalacji.  
>   
>  Możesz wypróbować następujące kroki, aby naprawić ten błąd:  
>   
>  -   Użyj **aplikacje i funkcje** lub **programy i funkcje** strony **Panelu sterowania** do naprawy lub ponownej instalacji programu.  
> -   Sprawdź **usługi Windows Update** w **Panelu sterowania** aktualizacji oprogramowania.  
> -   Sprawdź, czy zaktualizowaną wersję aplikacji. Jeśli problem będzie się powtarzać, skontaktuj się z dostawcą aplikacji.  
  
 **Informacje dla programistów**  
  
 Brak obiektu utworzeniu wystąpienia obsłużyć wywołanie czystej funkcji wirtualnej.  
  
 Ten błąd jest spowodowany przez wywołanie funkcji wirtualnej abstrakcyjna klasa podstawowa za pomocą wskaźnika, który jest tworzony przez rzutowanie na typ klasy pochodnej, ale faktycznie wskaźnika do klasy podstawowej. Taka sytuacja może wystąpić, kiedy następuje rzutowanie z **void\***  na wskaźnik do klasy, gdy **void\***  został utworzony podczas konstruowania klasy podstawowej.  
  
 Aby uzyskać więcej informacji, zobacz [pomocy technicznej firmy Microsoft](http://go.microsoft.com/fwlink/?LinkId=75220) witryny sieci Web.