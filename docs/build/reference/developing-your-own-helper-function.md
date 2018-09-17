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
ms.openlocfilehash: d95434c51bdfca07e48714c8c1e13bcdb64dc02f
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45716004"
---
# <a name="developing-your-own-helper-function"></a>Tworzenie własnej funkcji Pomocnik

Można podać własną wersję procedury w celu przetwarzania specyficznego na podstawie nazw biblioteki DLL lub importuje. Istnieją dwie metody to zrobić: kodowanie własny, prawdopodobnie oparte na podany kod lub jedynie Przechwytywanie przekazana wersja przy użyciu punkty zaczepienia powiadomień, szczegółowo wcześniej.

## <a name="code-your-own"></a>Własnego kodu

Jest to dość proste, ponieważ zasadniczo służy podany kod należy przyjąć nowego. Oczywiście muszą stosować się do konwencji wywoływania, a jeśli zwróci ona sekcje Thunk generowanych przez konsolidator, aplikacja musi zwracać wskaźnik odpowiednich funkcji. Jeden raz w kodzie, możesz tworzyć właściwie dowolnie aby spełniał wywołania lub uzyskiwać dostęp do najważniejszych wywołania.

## <a name="use-the-start-processing-notification-hook"></a>Użyj rozpoczęcia przetwarzania punktu zaczepienia powiadomień

Prawdopodobnie będzie łatwiej wystarczy podać nowy wskaźnik do funkcji punktów zaczepienia powiadomień dostarczone przez użytkownika, która otrzymuje te same wartości pomocnika domyślne na dliStartProcessing powiadomień. W tym momencie funkcja podłączania można zasadniczo stają się nową funkcję pomocnika pomyślne wróć do domyślnego elementu pomocniczego pomijał wszystkie dalsze przetwarzanie w Pomocniku domyślne.

## <a name="see-also"></a>Zobacz też

[Obsługa konsolidatora dla bibliotek DLL załadowanych z opóźnieniem](../../build/reference/linker-support-for-delay-loaded-dlls.md)