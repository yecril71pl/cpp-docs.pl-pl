---
title: once, pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.once
- once_CPP
helpviewer_keywords:
- once pragma
- pragmas, once
ms.assetid: c7517556-6403-4b16-8898-f2aa0a6f685f
ms.openlocfilehash: 643ad83b672f7b632925383972751a966256eb41
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220537"
---
# <a name="once-pragma"></a>once, pragma

Określa, że kompilator zawiera plik nagłówka tylko raz, podczas kompilowania pliku kodu źródłowego.

## <a name="syntax"></a>Składnia

> **#pragma raz**

## <a name="remarks"></a>Uwagi

Użycie programu `#pragma once` może skrócić czasy kompilacji, ponieważ kompilator nie otwiera i ponownie odczytuje plik po pierwszym `#include` pliku w jednostce translacji. Jest to tzw. *Optymalizacja wielokrotnego*dołączania. Działa podobnie jak w przypadku funkcji *include Guard* idiom, która używa definicji makr preprocesora, aby uniemożliwić wielokrotne dołączanie zawartości pliku. Pomaga również w zapobieganiu naruszeniom *jednej reguły definicji*, wymaganiu, że wszystkie szablony, typy, funkcje i obiekty nie mają więcej niż jednej definicji w kodzie.

Na przykład:

```cpp
// header.h
#pragma once
// Code placed here is included only once per translation unit
```

Zalecamy zastosowanie dyrektywy `#pragma once` dla nowego kodu, ponieważ nie powoduje to zanieczyszczenia globalnej przestrzeni nazw za pomocą symbolu preprocesora. Wymaga mniejszej ilości tekstu, jest mniej rozpraszania i nie może powodować *kolizji symboli*, błędy spowodowane, gdy różne pliki nagłówkowe używają tego samego symbolu preprocesora jako wartości ochrony. Nie jest częścią C++ standardu, ale jest implementowany przez kilka typowych kompilatorów.

Nie ma możliwości użycia zarówno funkcji include Guard idiom, jak i `#pragma once` w tym samym pliku. Kompilator rozpoznaje funkcję include Guard idiom i implementuje optymalizację wielokrotnego dołączania w taki sam sposób jak `#pragma once` dyrektywa, jeśli żaden kod niebędący komentarzem lub dyrektywa preprocesora nie jest wcześniejsza niż lub po standardowym formularzu idiom:

```cpp
// header.h
// Demonstration of the #include guard idiom.
// Note that the defined symbol can be arbitrary.
#ifndef HEADER_H_     // equivalently, #if !defined HEADER_H_
#define HEADER_H_
// Code placed here is included only once per translation unit
#endif // HEADER_H_
```

Zaleca się dołączenie ochrony idiom, gdy kod musi być przenośny do kompilatorów, które `#pragma once` nie implementują dyrektywy, aby zachować spójność z istniejącym kodem lub gdy Optymalizacja wielokrotnego dołączania jest niemożliwa. Może wystąpić w złożonych projektach, gdy aliasy systemu plików lub ścieżki dołączania mają uniemożliwiać kompilatorowi zidentyfikowanie identycznych plików dołączanych według ścieżki kanonicznej.

Należy uważać, aby nie `#pragma once` używać lub include Guard idiom w plikach nagłówkowych przeznaczonych do dołączenia wielokrotnie, które używają symboli preprocesora do sterowania ich wpływem. Aby zapoznać się z przykładem tego projektu, \<zapoznaj się z plikiem nagłówkowym Assert. h >. Należy również uważać, aby zarządzać ścieżkami dołączania, aby uniknąć tworzenia wielu ścieżek do dołączonych plików, co może obsłużyć optymalizację `#pragma once`obejmującą wiele dodatków.

## <a name="see-also"></a>Zobacz także

[Dyrektywy pragma i słowo kluczowe __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
