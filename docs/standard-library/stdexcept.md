---
title: '&lt;stdexcept&gt;'
ms.date: 11/04/2016
f1_keywords:
- <stdexcept>
helpviewer_keywords:
- stdexcept header
ms.assetid: 495c10b1-1e60-4514-9f8f-7fda11a2f522
ms.openlocfilehash: 8a8c99f2651d10d4fc2aff413a06256127f32d7d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50582796"
---
# <a name="ltstdexceptgt"></a>&lt;stdexcept&gt;

Definiuje kilka standardowych klas używane dla raportowania wyjątków. Klasy tworzą hierarchię pochodnym wszystkich pochodnych od klasy [wyjątek](../standard-library/exception-class.md) i obejmują dwa typy ogólne wyjątki: błędów logicznych i błędów czasu wykonywania. Błędy logiczne są spowodowane błędami programisty. One pochodzić od logic_error — klasa bazowa i obejmują:

- `domain_error`

- `invalid_argument`

- `length_error`

- `out_of_range`

Błędy środowiska wykonawczego wystąpić z powodu błędów w funkcji biblioteki lub działającego systemu. One pochodzić od runtime_error — klasa bazowa i obejmują:

- `overflow_error`

- `range_error`

- `underflow_error`

### <a name="classes"></a>Klasy

|Class|Opis|
|-|-|
|[domain_error, klasa](../standard-library/domain-error-class.md)|Klasa służy jako klasa bazowa dla wszystkich wyjątków generowanych, aby zgłosić błąd domeny.|
|[invalid_argument, klasa](../standard-library/invalid-argument-class.md)|Klasa służy jako klasa bazowa dla wszystkich wyjątków generowanych do zgłaszania nieprawidłowy argument.|
|[length_error, klasa](../standard-library/length-error-class.md)|Klasa służy jako klasa bazowa dla wszystkich wyjątków generowanych do zgłaszania próba wygenerowania zbyt długo, należy określić obiekt.|
|[logic_error, klasa](../standard-library/logic-error-class.md)|Klasa służy jako klasa bazowa dla wszystkich wyjątków generowanych do zgłaszania błędów prawdopodobnie wykrywalny, przed wykonaniem programu, takie jak naruszenia warunków wstępnych logiczne.|
|[out_of_range, klasa](../standard-library/out-of-range-class.md)|Klasa służy jako klasa bazowa dla wszystkich wyjątków generowanych do zgłaszania argument, który jest poza prawidłowym zakresem.|
|[overflow_error, klasa](../standard-library/overflow-error-class.md)|Klasa służy jako klasa bazowa dla wszystkich wyjątków generowanych do zgłaszania przepełnienie arytmetyczne.|
|[range_error, klasa](../standard-library/range-error-class.md)|Klasa służy jako klasa bazowa dla wszystkich wyjątków generowanych, aby zgłosić błąd zakresu.|
|[runtime_error, klasa](../standard-library/runtime-error-class.md)|Klasa służy jako klasa bazowa dla wszystkich wyjątków generowanych do zgłaszania błędów, wykrywalnych prawdopodobnie tylko wtedy, gdy program będzie działać.|
|[underflow_error, klasa](../standard-library/underflow-error-class.md)|Klasa służy jako klasa bazowa dla wszystkich wyjątków generowanych do zgłaszania arytmetyczne niedopełnienie.|

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
