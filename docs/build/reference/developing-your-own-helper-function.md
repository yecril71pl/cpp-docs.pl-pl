---
title: Tworzenie własnej funkcji Pomocnik | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- helper functions
ms.assetid: a845429d-68b1-4e14-aa88-f3f5343bd490
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e6b8e397fecc8f14140cd7c86217421d5aa1a749
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="developing-your-own-helper-function"></a>Tworzenie własnej funkcji Pomocnik
Możesz podać wersji procedury w celu przetwarzania specyficznego dla opartych na nazwach biblioteki DLL lub importowania. Istnieją dwie metody w ten sposób: kodowania własnych, najlepiej jest oparta na podany kod lub tylko Przechwytywanie przekazana wersja przy użyciu punkty zaczepienia powiadomień szczegółowe wcześniej.  
  
 Kod własne  
 Jest to dość proste, ponieważ zasadniczo służy podany kod przyjąć nowego. Oczywiście muszą stosować się do konwencji wywoływania i zwraca go do osadzenia generowanych przez konsolidator, musi zwracać wskaźnika prawidłowego funkcji. Raz w kodzie, możesz to zrobić bardzo dużo dowolne w celu zaspokojenia wywołania lub wykorzystanie wywołania.  
  
 Używać do uruchamiania przetwarzania punktu zaczepienia powiadomień  
 Będzie ona prawdopodobnie łatwiej wystarczy podać nowe wskaźnika do funkcji punktów zaczepienia powiadomień dostarczone przez użytkownika, która odbiera takie same wartości jak pomocnika domyślnej na dliStartProcessing powiadomień. W tym momencie funkcji punktów zaczepienia zasadniczo mogą pełnić nowej funkcji pomocnika, jak pomyślnie powrotu do pomocniczego domyślne pomijał wszystkie dalsze przetwarzanie w pomocnika domyślne.  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa konsolidatora dla bibliotek DLL załadowanych z opóźnieniem](../../build/reference/linker-support-for-delay-loaded-dlls.md)