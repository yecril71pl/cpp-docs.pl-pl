---
title: '&lt;stdexcept&gt;'
ms.date: 11/04/2016
f1_keywords:
- <stdexcept>
helpviewer_keywords:
- stdexcept header
ms.assetid: 495c10b1-1e60-4514-9f8f-7fda11a2f522
ms.openlocfilehash: d4028d57a6e8898f85a37d9731e7e8d4cda19a2f
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68453724"
---
# <a name="ltstdexceptgt"></a>&lt;stdexcept&gt;

Definiuje kilka klas standardowych używanych do raportowania wyjątków. Klasy tworzą hierarchię pochodną wszystkie pochodne od [wyjątku](../standard-library/exception-class.md) klasy i zawierają dwa typy ogólne wyjątków: Błędy logiczne i błędy czasu wykonywania. Błędy logiczne są spowodowane błędami programisty. Pochodzą one z klasy bazowej logic_error i obejmują:

- `domain_error`

- `invalid_argument`

- `length_error`

- `out_of_range`

Błędy w czasie wykonywania występują z powodu błędów w funkcjach biblioteki lub w systemie czasu wykonywania. Pochodzą one z klasy bazowej runtime_error i obejmują:

- `overflow_error`

- `range_error`

- `underflow_error`

### <a name="classes"></a>Klasy

|Class|Opis|
|-|-|
|[domain_error, klasa](../standard-library/domain-error-class.md)|Klasa służy jako klasa bazowa dla wszystkich wyjątków zgłoszonych w celu zgłaszania błędu domeny.|
|[invalid_argument, klasa](../standard-library/invalid-argument-class.md)|Klasa służy jako klasa bazowa dla wszystkich wyjątków zgłoszonych w celu zgłoszenia nieprawidłowego argumentu.|
|[length_error, klasa](../standard-library/length-error-class.md)|Klasa służy jako klasa bazowa dla wszystkich wyjątków zgłoszonych w celu zgłoszenia próby wygenerowania obiektu zbyt długo.|
|[logic_error, klasa](../standard-library/logic-error-class.md)|Klasa służy jako klasa bazowa dla wszystkich wyjątków zgłoszonych w celu zgłaszania błędów, które są wykrywalne przed wykonaniem programu, na przykład naruszenia logicznych warunków wstępnych.|
|[out_of_range, klasa](../standard-library/out-of-range-class.md)|Klasa służy jako klasa bazowa dla wszystkich wyjątków zgłoszonych w celu zgłoszenia argumentu, który jest poza prawidłowym zakresem.|
|[overflow_error, klasa](../standard-library/overflow-error-class.md)|Klasa służy jako klasa bazowa dla wszystkich wyjątków zgłoszonych do zgłaszania przepełnienia arytmetycznego.|
|[range_error, klasa](../standard-library/range-error-class.md)|Klasa służy jako klasa bazowa dla wszystkich wyjątków zgłoszonych w celu zgłaszania błędu zakresu.|
|[runtime_error, klasa](../standard-library/runtime-error-class.md)|Klasa służy jako klasa bazowa dla wszystkich wyjątków zgłoszonych w celu zgłaszania błędów, które mogą być wykrywalne tylko wtedy, gdy program jest wykonywany.|
|[underflow_error, klasa](../standard-library/underflow-error-class.md)|Klasa służy jako klasa bazowa dla wszystkich wyjątków zgłoszonych do zgłaszania niedopełnienia arytmetycznego.|

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
