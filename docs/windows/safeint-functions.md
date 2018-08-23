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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: cf9a35d2198c78290bb6e60adef40fc88fdf4879
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42604431"
---
# <a name="safeint-functions"></a>SafeInt — Funkcje

Biblioteka SafeInt udostępnia kilka funkcji, których można używać bez tworzenia wystąpienia obiektu [safeint — klasa](../windows/safeint-class.md). Jeśli chcesz chronić jednej operacji matematycznych przepełnienie liczby całkowitej, można użyć tych funkcji. Jeśli chcesz chronić wiele operacji matematycznych, należy utworzyć **SafeInt** obiektów. Jest bardziej wydajne, aby utworzyć **SafeInt** obiektów, niż można użyć tych funkcji wiele razy.

Te funkcje umożliwiają porównywania albo do wykonywania operacji matematycznych na dwa różne typy parametrów bez konieczności konwertowania ich najpierw do tego samego typu.

Każda z tych funkcji są dostępne dwa typy szablonów: `T` i `U`. Każdy z tych typów może być atrybut typu wartość logiczna, znak lub typu całkowitego. Typy całkowite mogą być podpisane lub niepodpisane i dowolnego rozmiaru, od 8 bitów na 64-bitowy.

## <a name="in-this-section"></a>W tej sekcji

|Funkcja|Opis|
|--------------|-----------------|
|[SafeAdd](../windows/safeadd.md)|Dodaje dwie liczby i chroni przed przepełnienia.|
|[SafeCast](../windows/safecast.md)|Rzutuje jeden typ parametru do innego typu.|
|[SafeDivide](../windows/safedivide.md)|Dzieli dwie liczby i chroni przed dzielenie przez zero.|
|[SafeEquals](../windows/safeequals.md), [SafeGreaterThan](../windows/safegreaterthan.md), [SafeGreaterThanEquals](../windows/safegreaterthanequals.md), [SafeLessThan](../windows/safelessthan.md), [SafeLessThanEquals](../windows/safelessthanequals.md), [ SafeNotEquals](../windows/safenotequals.md)|Porównuje dwie liczby. Te funkcje pozwalają porównać dwa różne typy liczb bez zmiany ich typy.|
|[SafeModulus](../windows/safemodulus.md)|Wykonuje operację modulo na dwóch liczb.|
|[SafeMultiply](../windows/safemultiply.md)|Mnoży dwie liczby ze sobą i chroni przed przepełnienia.|
|[SafeSubtract](../windows/safesubtract.md)|Odejmuje dwie liczby i chroni przed przepełnienia.|

## <a name="related-sections"></a>Sekcje pokrewne

|Sekcja|Opis|
|-------------|-----------------|
|[SafeInt, klasa](../windows/safeint-class.md)|**SafeInt** klasy.|
|[SafeIntException, klasa](../windows/safeintexception-class.md)|Biblioteka SafeInt specyficzne klasy wyjątku.|