---
title: "C błąd w czasie wykonywania R6033 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- R6033
dev_langs:
- C++
helpviewer_keywords:
- R6033
ms.assetid: f9cffdc9-81bd-4a64-a698-02762cbd82c9
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9f2ef73d3cb82a65c8114d2e7f921b47ffd45d65
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="c-runtime-error-r6033"></a>C R6033 błąd w czasie wykonywania
Próba użycia MSIL kod z tego zestawu podczas inicjowania kodu natywnego. To wskazuje na usterkę w aplikacji. Jest to najprawdopodobniej wynikiem wywołania skompilowany MSIL (/ clr) funkcja z natywnego konstruktora lub z funkcji DllMain.  
  
> [!NOTE]
>  Jeśli wystąpią ten komunikat o błędzie podczas uruchamiania aplikacji aplikacji został wyłączony, ponieważ ma ona wystąpił problem wewnętrzny. Ten błąd może być spowodowany błędem w aplikacji lub na usterkę w dodatku lub rozszerzenia, która jest używana.  
>   
>  Możesz wypróbować następujące kroki, aby naprawić ten błąd:  
>   
>  -   Użyj **aplikacje i funkcje** lub **programy i funkcje** strony **Panelu sterowania** do naprawy lub ponownej instalacji programu.  
> -   Użyj **aplikacje i funkcje** lub **programy i funkcje** strony **Panelu sterowania** do usunięcia, napraw lub ponownie zainstalować wszystkie rozszerzenia lub dodatków.  
> -   Sprawdź **usługi Windows Update** w **Panelu sterowania** aktualizacji oprogramowania.  
> -   Sprawdź, czy zaktualizowaną wersję aplikacji. Jeśli problem będzie się powtarzać, skontaktuj się z dostawcą aplikacji.  
  
 **Informacje dla programistów**  
  
 Diagnostyka wskazuje, że instrukcje MSIL wykonywały podczas blokady modułu ładującego. Może to wystąpić, jeśli natywnych języka C++ ma być kompilowane przy użyciu flagi/CLR. Tylko użyć flagi/CLR dla modułów, które zawierają kodu zarządzanego. Aby uzyskać więcej informacji, zobacz [inicjowanie zestawów mieszanych](../../dotnet/initialization-of-mixed-assemblies.md).