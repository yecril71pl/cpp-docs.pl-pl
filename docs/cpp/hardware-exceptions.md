---
title: Wyjątki sprzętowe
ms.date: 11/04/2016
helpviewer_keywords:
- exceptions [C++], hardware
- errors [C++], low-level
- errors [C++], hardware
- hardware exceptions [C++]
- low level errors
ms.assetid: 06ac6f01-a8cf-4426-bb12-1688315ae1cd
ms.openlocfilehash: 59b74f47cd86d94b50ab9213b3e517c2b08db696
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246550"
---
# <a name="hardware-exceptions"></a>Wyjątki sprzętowe

Do większości standardowych wyjątków rozpoznawanych przez system operacyjny należą wyjątki zdefiniowane przez sprzęt. System Windows rozpoznaje kilka wyjątków oprogramowania niskiego poziomu, ale są one zazwyczaj najlepiej obsługiwane przez system operacyjny.

System Windows mapuje błędy sprzętowe różnych procesorów na kody wyjątków w tej sekcji. W niektórych przypadkach procesor może wygenerować tylko podzbiór tych wyjątków. System Windows wstępnie przetwarza informacje dotyczące wyjątku i zgłasza odpowiedni kod wyjątku.

Wyjątki sprzętowe rozpoznawane przez system Windows zestawiono w poniższej tabeli:

|Kod wyjątku|Przyczyna wyjątku|
|--------------------|------------------------|
|STATUS_ACCESS_VIOLATION|Odczyt lub zapis do niedostępnej lokalizacji pamięci.|
|STATUS_BREAKPOINT|Napotkanie punktu przerwania zdefiniowanego przez sprzęt; używane tylko przez debugery.|
|STATUS_DATATYPE_MISALIGNMENT|Odczyt lub zapis danych na adres, który jest nieodpowiednio wyrównany; na przykład jednostki 16-bitowe muszą być wyrównane do 2-bajtowych granic. (Nie dotyczy procesorów Intel 80*x*86).|
|STATUS_FLOAT_DIVIDE_BY_ZERO|Dzielenie liczb typu zmiennoprzecinkowego przez 0.0.|
|STATUS_FLOAT_OVERFLOW|Przekroczenie maksymalnego dodatniego wykładnika typu zmiennoprzecinkowego.|
|STATUS_FLOAT_UNDERFLOW|Przekroczenie wielkości najmniejszego ujemnego wykładnika typu zmiennoprzecinkowego.|
|STATUS_FLOATING_RESEVERED_OPERAND|Użycie zastrzeżonego formatu zmiennoprzecinkowego (nieprawidłowe użycie formatu).|
|STATUS_ILLEGAL_INSTRUCTION|Podjęcie próby wykonania kodu instrukcji nie zdefiniowanej przez procesor.|
|STATUS_PRIVILEGED_INSTRUCTION|Wykonywanie instrukcji niedozwolonej w bieżącym trybie komputera.|
|STATUS_INTEGER_DIVIDE_BY_ZERO|Dzielenie liczby całkowitej przez 0.|
|STATUS_INTEGER_OVERFLOW|Podjęcie próby wykonania operacji, która wykracza poza zakres liczby całkowitej.|
|STATUS_SINGLE_STEP|Wykonywanie pojedynczej instrukcji w trybie pracy krokowej; używane tylko przez debugery.|

Wiele wyjątków wymienionych w powyższej tabeli jest przeznaczonych do obsługi przez debugery, system operacyjny lub inny kod niskiego poziomu. Z wyjątkiem błędów liczb całkowitych i zmiennoprzecinkowych, kod nie powinien obsługiwać tych błędów. Zatem zazwyczaj należy korzystać z filtru obsługi wyjątków w celu ignorowania wyjątków (obliczania do 0). W przeciwnym razie można uniemożliwić prawidłową odpowiedź mechanizmom niskiego poziomu. Można jednak podjąć odpowiednie środki ostrożności przed potencjalnym efektem tych błędów niskiego poziomu, [pisząc programy obsługi zakończenia](../cpp/writing-a-termination-handler.md).

## <a name="see-also"></a>Zobacz także

[Pisanie procedury obsługi wyjątków](../cpp/writing-an-exception-handler.md)<br/>
[Obsługa wyjątków strukturalnych (C/C++)](../cpp/structured-exception-handling-c-cpp.md)