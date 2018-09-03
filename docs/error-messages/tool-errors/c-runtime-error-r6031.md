---
title: C błąd w czasie wykonywania R6031 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6031
dev_langs:
- C++
helpviewer_keywords:
- R6031
ms.assetid: 805d4cd1-cb2f-43fe-87e6-e7bd5b7329c5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 66d75fb0095b1de0fe1572d8c946823a89791740
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33303949"
---
# <a name="c-runtime-error-r6031"></a>C R6031 błąd w czasie wykonywania
Próba zainicjowania CRT więcej niż raz. To wskazuje na usterkę w aplikacji.  
  
> [!NOTE]
>  Jeśli wystąpią ten komunikat o błędzie podczas uruchamiania aplikacji aplikacji został wyłączony, ponieważ ma ona wystąpił problem wewnętrzny. Może to być spowodowane błędów w aplikacji lub błąd w dodatku lub rozszerzenia, które korzysta z aplikacji.  
>   
>  Możesz wypróbować następujące kroki, aby naprawić ten błąd:  
>   
>  -   Użyj **aplikacje i funkcje** lub **programy i funkcje** strony **Panelu sterowania** do naprawy lub ponownej instalacji programu.  
> -   Użyj **aplikacje i funkcje** lub **programy i funkcje** strony **Panelu sterowania** do usunięcia, napraw lub ponownie zainstalować programy dodatków lub rozszerzeń używanych przez aplikację.  
> -   Sprawdź **usługi Windows Update** w **Panelu sterowania** aktualizacji oprogramowania.  
> -   Sprawdź, czy zaktualizowaną wersję aplikacji. Jeśli problem będzie się powtarzać, skontaktuj się z dostawcą aplikacji.  
  
 **Informacje dla programistów**  
  
 Diagnostyka wskazuje, że instrukcje MSIL wykonywały podczas blokady modułu ładującego. Aby uzyskać więcej informacji, zobacz [inicjowanie zestawów mieszanych](../../dotnet/initialization-of-mixed-assemblies.md).