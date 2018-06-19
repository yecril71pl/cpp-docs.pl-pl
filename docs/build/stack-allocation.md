---
title: Alokacja stosu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 098e51f2-eda6-40d0-b149-0b618aa48b47
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: caa6d435db98c7177cbf55b866bb8e5a4a110c1d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32380605"
---
# <a name="stack-allocation"></a>Alokacja stosu
Funkcja prologu jest odpowiedzialny za przydzielania miejsca na stosie dla zmiennych lokalnych, zapisane rejestrowania, stosu parametry i parametry rejestru.  
  
 Parametr obszar jest zawsze w dolnej części stosu (nawet jeśli jest używany alloca), dzięki czemu zawsze będzie sąsiadujące adres zwrotny podczas wszystkie wywołania funkcji. Zawiera co najmniej cztery wpisy, ale zawsze wystarczającej ilości miejsca dla wszystkich parametrów wymagane przez funkcję, która może zostać wywołana. Należy pamiętać, że jest zawsze przydzielone miejsce dla parametrów rejestru nawet wtedy, gdy parametry się nigdy nie są podłączony do stosu; wywoływany jest gwarantowana przydzielone miejsce jego parametrów. Adresy domowe są wymagane dla argumentów rejestru, dlatego ciągły obszar jest dostępna w przypadku, gdy wywoływana funkcja musi przyjąć adresu listy argumentów (va_list) lub poszczególnych argumentów. Ten obszar zapewnia również wygodne miejsce do zapisania rejestru argumentów podczas wykonywania thunk i jako opcji debugowania (na przykład ułatwia argumenty łatwe do odnalezienia podczas debugowania, jeśli są one przechowywane na adresy domowe w kodzie prologu). Nawet wtedy, gdy wywoływana funkcja ma mniej niż 4 parametry, te lokalizacje 4 stosu skutecznie własnością wywołana funkcja i mogą być używane przez wywołanej funkcji do innych celów, oprócz zapisywania parametru wartości rejestru.  W związku z tym wywołujący może nie zostać zapisana informacje w tym regionie stosu w wywołaniu funkcji.  
  
 Jeśli miejsce jest przydzielane dynamicznie (alloca) w funkcji, następnie nieulotnej rejestru muszą być używane jako wskaźnika ramki, aby oznaczyć base stałej części stosu i rejestru musi być zapisany i zainicjowany w prologu. Należy pamiętać, że użycie alloca wywołania do tej samej wywoływany z tego samego obiektu wywołującego może mieć różne adresy domowe ich parametry rejestru.  
  
 Stos zostanie zachowany 16-bajtowych wyrównane, z wyjątkiem w prologu (na przykład po spoczywa adres zwrotny) oraz z wyjątkiem wskazanych w [typy funkcji](../build/function-types.md) dla klasy funkcji ramki.  
  
 Poniżej znajduje się, że przykład układu stosu, gdzie wywołania funkcji A niebędący liściem funkcji prologu funkcji B. A zawiera już przydzielone miejsce dla wszystkich parametrów rejestru i stosu wymagane przez B w dolnej części stosu. Wywołanie wypchnięcia adres zwrotny i prologu B przydziela miejsce dla jego zmiennych lokalnych, nieulotnej rejestrów i miejsce wymagane do jej do wywołania funkcji. Jeśli B używa alloca, miejsce jest przydzielane od lokalnego rejestru zmiennej/nieulotnej Zapisz obszaru i obszaru stosu parametru.  
  
 ![Przykład konwersji AMD](../build/media/vcamd_conv_ex_5.png "vcAmd_conv_ex_5")  
  
 Gdy funkcja B wywołuje innej funkcji, adres zwrotny spoczywa poniżej adres domowy dla RCX.  
  
## <a name="see-also"></a>Zobacz też  
 [Wykorzystanie stosu](../build/stack-usage.md)