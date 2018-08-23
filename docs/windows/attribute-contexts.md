---
title: Konteksty atrybutu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++], contexts
ms.assetid: 3086351f-77a8-4048-99e9-3b6b041b9437
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7635f49a494648f18bcd59eb8d212cc76d1f1539
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42600803"
---
# <a name="attribute-contexts"></a>Konteksty atrybutu
Atrybuty C++ można opisać za pomocą cztery pola podstawowe: element docelowy, mogą być stosowane do (**dotyczy**), jeśli są one powtarzalne, czy nie (**Repeatable**), wymagane obecność innych atrybutów ( **Atrybuty wymagane**) i niezgodności z innymi atrybutami (**nieprawidłowe atrybuty**). Te pola są wymienione w towarzyszącej mu tabeli, w artykule dotyczącym każdego atrybutu. Poniżej opisano każde z tych pól.
  
## <a name="applies-to"></a>Dotyczy:
 To pole zawiera opis różnych elementów języka C++, które prawne elementów docelowych dla określonego atrybutu. Na przykład jeśli atrybut "class" Określa **dotyczy** pola, oznacza to, że ten atrybut można dotyczą wyłącznie prawne klasy języka C++. Jeśli ten atrybut jest stosowany do funkcji składowej klasy, spowoduje błąd składni.
  
 Aby uzyskać więcej informacji, zobacz [atrybuty w zależności od użycia](../windows/attributes-by-usage.md).
  
## <a name="repeatable"></a>Powtarzalne
 To pole określa, czy można wielokrotnie zastosować atrybutu, do tej samej wartości docelowej. Większość atrybutów nie są powtarzalne.
  
## <a name="required-attributes"></a>Wymaganych atrybutów
 To pole zawiera inne atrybuty, które muszą być obecne (co oznacza, że są stosowane do tej samej wartości docelowej) dla określonego atrybutu działać prawidłowo. Jest nietypowy dla atrybutu powoduje, że wszystkie wpisy dla tego pola.
  
## <a name="invalid-attributes"></a>Nieprawidłowe atrybuty
 To pole zawiera atrybuty, które nie są zgodne z określonego atrybutu. Jest nietypowy dla atrybutu powoduje, że wszystkie wpisy dla tego pola.
  
## <a name="see-also"></a>Zobacz też
 [Dokumentacja atrybutów (C++)](../windows/cpp-attributes-reference.md)