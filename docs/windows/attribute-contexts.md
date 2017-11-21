---
title: Konteksty atrybutu | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords: attributes [C++], contexts
ms.assetid: 3086351f-77a8-4048-99e9-3b6b041b9437
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: fceb15c713eee25c4ae04ef2a095737e587170a0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="attribute-contexts"></a>Konteksty atrybutu
Atrybuty C++ można opisać za pomocą czterech pola podstawowe: element docelowy, mogą być stosowane do (**dotyczy**), jeśli są one powtarzalne, czy nie (**Repeatable**), wymagane obecności innych atrybutów ( **Wymagane atrybuty**), a niezgodności z innymi atrybutami (**nieprawidłowe atrybuty**). Te pola są wyświetlane w towarzyszący tabeli w temacie Odwołanie do każdego atrybutu. Poniżej opisano każdy z tych pól.  
  
## <a name="applies-to"></a>Dotyczy:  
 To pole zawiera opis różnych elementów języka C++, które prawne elementów docelowych dla określonego atrybutu. Na przykład jeśli atrybut określa "class" w **dotyczy** pola, oznacza to, że atrybut można stosować tylko prawne klasę C++. Jeśli ten atrybut jest stosowany do funkcji członkowskiej klasy, spowoduje błąd składni.  
  
 Aby uzyskać więcej informacji, zobacz [atrybuty w zależności od użycia](../windows/attributes-by-usage.md).  
  
## <a name="repeatable"></a>Powtarzalne  
 To pole określa, czy można wielokrotnie zastosować atrybutu, do tej samej wartości docelowej. Większość atrybuty nie są powtarzalne.  
  
## <a name="required-attributes"></a>Wymaganych atrybutów  
 To pole zawiera inne atrybuty, które muszą być obecna (co oznacza, że są stosowane do tego samego obiektu docelowego) dla określonego atrybutu działać prawidłowo. Jest on nietypowe dla atrybutu do wpisów dla tego pola.  
  
## <a name="invalid-attributes"></a>Nieprawidłowe atrybuty  
 To pole zawiera inne atrybuty, które są niezgodne z określonego atrybutu. Jest on nietypowe dla atrybutu do wpisów dla tego pola.  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty C++ — dokumentacja](../windows/cpp-attributes-reference.md)