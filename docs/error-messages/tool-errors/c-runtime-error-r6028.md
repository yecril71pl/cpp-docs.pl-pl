---
title: C błąd w czasie wykonywania R6028 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6028
dev_langs:
- C++
helpviewer_keywords:
- R6028
ms.assetid: 81e99079-4388-4244-a4f7-4641c508871c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b978d1d9165fd48be9d0ce31aa72092fc660dbd9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33297826"
---
# <a name="c-runtime-error-r6028"></a>C R6028 błąd w czasie wykonywania
nie można zainicjować sterty  
  
> [!NOTE]
>  Jeśli wystąpią ten komunikat o błędzie podczas uruchamiania aplikacji aplikacji został wyłączony, ponieważ wystąpił problem wewnętrzny pamięci. Istnieje wiele możliwych przyczyn tego błędu, ale często spowodowane przez warunek bardzo małej ilości pamięci, usterki w programie lub uszkodzenie sprzętu sterowniki.  
>   
>  Możesz wypróbować następujące kroki, aby naprawić ten błąd:  
>   
>  -   Zamknij inne uruchomione aplikacje lub uruchom ponownie komputer, aby zwolnić pamięć.  
> -   Użyj **aplikacje i funkcje** lub **programy i funkcje** strony **Panelu sterowania** do naprawy lub ponownej instalacji programu.  
> -   Jeśli aplikacja pracy przed Ostatnia instalacja innej aplikacji lub sterownika, użyj **aplikacje i funkcje** lub **programy i funkcje** strony **Panelu sterowania** do usunięcia Nowa aplikacja lub sterowników i spróbuj ponownie aplikację.  
> -   Witrynie sieci Web z dostawcą sprzętu lub **usługi Windows Update** w **Panelu sterowania** aktualizacji oprogramowania i sterowników.  
> -   Sprawdź, czy zaktualizowaną wersję aplikacji. Jeśli problem będzie się powtarzać, skontaktuj się z dostawcą aplikacji.  
  
 **Informacje dla programistów**  
  
 Ten błąd występuje, gdy system operacyjny nie może utworzyć puli pamięci dla aplikacji. W szczególności C Runtime (CRT) wywołał funkcję Win32 `HeapCreate`, który zwrócił wartość NULL, informujący o niepowodzeniu.  
  
 Jeśli ten błąd występuje podczas uruchamiania aplikacji, system może nie być w stanie spełnić żądań sterty, ponieważ ładowane są uszkodzone sterowniki. Sprawdź witrynę Windows Update lub witrynę dostawcy sprzętu, aby uzyskać zaktualizowane sterowniki.