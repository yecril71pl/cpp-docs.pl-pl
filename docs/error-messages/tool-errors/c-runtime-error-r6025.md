---
title: C błąd w czasie wykonywania R6025 | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: abdbdbf918462dfb83eff07190c32af1f1b3d015
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33302029"
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
  
 Aby uzyskać więcej informacji, zobacz [pomocy technicznej firmy Microsoft](http://go.microsoft.com/fwlink/p/?linkid=75220) witryny sieci Web.