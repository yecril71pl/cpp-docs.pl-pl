---
title: "Tworzenie własnej funkcji Pomocnik | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- helper functions
ms.assetid: a845429d-68b1-4e14-aa88-f3f5343bd490
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 76172804cc271a740244d06e791db35d534c69e7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="developing-your-own-helper-function"></a>Tworzenie własnej funkcji Pomocnik
Możesz podać wersji procedury w celu przetwarzania specyficznego dla opartych na nazwach biblioteki DLL lub importowania. Istnieją dwie metody w ten sposób: kodowania własnych, najlepiej jest oparta na podany kod lub tylko Przechwytywanie przekazana wersja przy użyciu punkty zaczepienia powiadomień szczegółowe wcześniej.  
  
 Kod własne  
 Jest to dość proste, ponieważ zasadniczo służy podany kod przyjąć nowego. Oczywiście muszą stosować się do konwencji wywoływania i zwraca go do osadzenia generowanych przez konsolidator, musi zwracać wskaźnika prawidłowego funkcji. Raz w kodzie, możesz to zrobić bardzo dużo dowolne w celu zaspokojenia wywołania lub wykorzystanie wywołania.  
  
 Używać do uruchamiania przetwarzania punktu zaczepienia powiadomień  
 Będzie ona prawdopodobnie łatwiej wystarczy podać nowe wskaźnika do funkcji punktów zaczepienia powiadomień dostarczone przez użytkownika, która odbiera takie same wartości jak pomocnika domyślnej na dliStartProcessing powiadomień. W tym momencie funkcji punktów zaczepienia zasadniczo mogą pełnić nowej funkcji pomocnika, jak pomyślnie powrotu do pomocniczego domyślne pomijał wszystkie dalsze przetwarzanie w pomocnika domyślne.  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa konsolidatora dla bibliotek DLL załadowanych z opóźnieniem](../../build/reference/linker-support-for-delay-loaded-dlls.md)