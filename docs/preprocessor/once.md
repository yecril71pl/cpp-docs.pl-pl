---
title: once
ms.date: 11/04/2016
f1_keywords:
- vc-pragma.once
- once_CPP
helpviewer_keywords:
- once pragma
- pragmas, once
ms.assetid: c7517556-6403-4b16-8898-f2aa0a6f685f
ms.openlocfilehash: 6061fe77960aa64e2dcb39db05897ef0e7fb5f2e
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59039887"
---
# <a name="once"></a>once
Określa, że plik zostanie uwzględniony (otwarte) tylko raz przez kompilator podczas kompilowania pliku kodu źródłowego.

## <a name="syntax"></a>Składnia

```
#pragma once
```

## <a name="remarks"></a>Uwagi

Korzystanie z `#pragma once` może zmniejszyć czasy kompilacji, ponieważ kompilator nie będą otwierane i odczytania pliku po pierwszym `#include` pliku w jednostce translacji. Jest to określane jako *optymalizacji obejmują wiele*. Jest efekt jest podobny do `#include guard` idiom, który używa definicji makro preprocesora aby uniemożliwić dołączanie wielu zawartość pliku. Pomaga to również zapobieganie naruszeń *reguły jednej definicji*— wymagania, że wszystkie szablony, typy, funkcje i obiekty mają nie więcej niż jedną definicję w kodzie.

Na przykład:

```
// header.h
#pragma once
// Code placed here is included only once per translation unit
```

Firma Microsoft zaleca `#pragma once` dyrektywy dla nowego kodu, ponieważ nie charakteryzują się globalnej przestrzeni nazw za pomocą symbol preprocesora. Wymaga mniej wpisując, jest mniej rozprasza uwagę i nie może powodować konflikty symbol — błędy spowodowane pliki nagłówkowe różnych korzystania z tego samego symbol preprocesora jako wartość guard. Nie jest częścią standardu języka C++, ale jest zaimplementowana portably przez kilka typowych kompilatory.

Nie posiada zalet korzystania z obu #include guard idiom i `#pragma once` w tym samym pliku. Kompilator rozpoznaje #include guard idiom i implementuje wielokrotność obejmują optymalizacji w taki sam sposób jak `#pragma once` dyrektywy, jeśli nie kodu bez komentarza lub dyrektywy preprocesora obejmuje przed lub po standardowy formularz idiom:

```
// header.h
// Demonstration of the #include guard idiom.
// Note that the defined symbol can be arbitrary.
#ifndef HEADER_H_     // equivalently, #if !defined HEADER_H_
#define HEADER_H_
// Code placed here is included only once per translation unit
#endif // HEADER_H_
```

Firma Microsoft zaleca `#include guard` idiom, gdy kod musi być przenośny do kompilatory, które nie implementują `#pragma once` dyrektywy, aby zachować spójność z istniejącego kodu, lub gdy obejmują wiele optymalizacji jest niemożliwe. Taka sytuacja może wystąpić w złożonych projektów podczas gdy aliasów systemu plików lub aliasem użytkownika zawiera ścieżki zapobiec kompilator identyfikuje identyczne pliki dołączane przez ścieżkę kanonicznej.

Należy zachować ostrożność nie należy używać `#pragma once` lub `#include guard` idiom w plikach nagłówkowych, opracowane w celu uwzględnienia wiele razy przy użyciu symboli preprocesora Aby kontrolować ich skutki. Na przykład w tym projekcie zobacz \<assert.h > pliku nagłówka. Również należy uważać, aby zarządzać ścieżki, aby uniknąć tworzenia wielu ścieżek do załączone pliki, które może zniweczyć cały dołączanych optymalizacji dla obu obejmują wiele `#include guard`s i `#pragma once`.

## <a name="see-also"></a>Zobacz także

[Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)