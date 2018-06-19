---
title: Safeint — funkcje | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- functions, SafeInt
ms.assetid: fdc208e5-5d8a-41a9-8271-567fd438958d
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 97edd25abca3c9e80a35745165eedc93cc13a9b9
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33889310"
---
# <a name="safeint-functions"></a>SafeInt — Funkcje
Safeint — biblioteka zawiera kilka funkcji, których można użyć bez tworzenia wystąpienia [safeint — klasa](../windows/safeint-class.md). Jeśli chcesz chronić jednej operacji matematycznych z liczbą całkowitą przepełnienia, możesz użyć tych funkcji. Jeśli chcesz chronić wiele operacji matematycznych, należy utworzyć `SafeInt` obiektów. Jest bardziej wydajne, można utworzyć `SafeInt` obiektów niż można używać tych funkcji wiele razy.  
  
 Te funkcje umożliwiają porównanie lub wykonywania operacji matematycznych na dwa różne typy parametrów bez konieczności najpierw przekonwertować je do tego samego typu.  
  
 Każda z tych funkcji ma dwa typy szablonu: `T` i `U`. Każdego z tych typów może być typu Boolean, znak lub typ całkowity. Typy całkowite mogą być podpisane lub niepodpisane i rozmiarze z 8 bitów na 64-bitowy.  
  
## <a name="in-this-section"></a>W tej sekcji  
  
|Funkcja|Opis|  
|--------------|-----------------|  
|[SafeAdd](../windows/safeadd.md)|Dodaje dwie liczby i chroni przed przepełnienia.|  
|[SafeCast](../windows/safecast.md)|Rzutuje jeden typ parametru do innego typu.|  
|[SafeDivide](../windows/safedivide.md)|Dzieli dwie liczby i chroni przed dzielenia przez zero.|  
|[SafeEquals](../windows/safeequals.md), [SafeGreaterThan](../windows/safegreaterthan.md), [SafeGreaterThanEquals](../windows/safegreaterthanequals.md), [SafeLessThan](../windows/safelessthan.md), [SafeLessThanEquals](../windows/safelessthanequals.md), [ SafeNotEquals](../windows/safenotequals.md)|Porównanie dwóch liczb. Funkcje te pozwalają porównać dwa różne typy liczby bez zmiany ich typów.|  
|[SafeModulus](../windows/safemodulus.md)|Wykonuje operację modulo na dwóch liczb.|  
|[SafeMultiply](../windows/safemultiply.md)|Razem mnoży dwie liczby i chroni przed przepełnienia.|  
|[SafeSubtract](../windows/safesubtract.md)|Odejmuje dwie liczby i chroni przed przepełnienia.|  
  
## <a name="related-sections"></a>Sekcje pokrewne  
  
|Sekcja|Opis|  
|-------------|-----------------|  
|[SafeInt, klasa](../windows/safeint-class.md)|`SafeInt` Klasy.|  
|[SafeIntException, klasa](../windows/safeintexception-class.md)|Klasy wyjątków specyficzne dla Biblioteka SafeInt.|