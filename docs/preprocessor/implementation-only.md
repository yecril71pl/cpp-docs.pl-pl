---
title: implementation_only
ms.date: 11/04/2016
f1_keywords:
- implementation_only
helpviewer_keywords:
- implementation_only attribute
ms.assetid: d8cabc86-4425-45a0-9587-d57536980088
ms.openlocfilehash: c1435ca74ac2b5a73c308592b1affe6fca097d1b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383961"
---
# <a name="implementationonly"></a>implementation_only
**Określonego język C++**

Powoduje pominięcie generowania pliku nagłówku .tlh (główny plik nagłówka).

## <a name="syntax"></a>Składnia

```
implementation_only
```

## <a name="remarks"></a>Uwagi

Ten plik zawiera wszystkie deklaracje używany do udostępnienia zawartość biblioteki typów. .Tli pliku nagłówka, z implementacjami funkcje Członkowskie otoki, zostanie wygenerowany i uwzględniony w kompilacji.

Jeśli ten atrybut jest określony, zawartość nagłówka .tli znajduje się w tej samej przestrzeni nazw jest zwykle używana w nagłówku .tlh. Ponadto funkcje elementów członkowskich nie są deklarowane jako wbudowane.

**Implementation_only —** atrybut jest przeznaczony do użycia w połączeniu z [no_implementation —](../preprocessor/no-implementation.md) atrybutu jako sposób na utrzymanie implementacje z pliku wstępnie skompilowanego nagłówka (PCH). `#import` Instrukcję, określając `no_implementation` atrybut jest umieszczany w regionie źródłowym użyty do utworzenia PCH. Wynikowy PCH jest używany przez wiele plików źródłowych. `#import` Instrukcję, określając **implementation_only —** atrybutu jest następnie używany poza regionem PCH. Jest wymagane, aby użyć tej instrukcji tylko raz w jednym z plików źródłowych. Spowoduje to wygenerowanie wszystkie funkcje składowe wymagane otoki bez dodatkowych ponownej kompilacji dla każdego pliku źródłowego.

> [!NOTE]
> **Implementation_only —** atrybutu w jednym `#import` instrukcja musi być używany w połączeniu z innego `#import` instrukcji tego samego wpisz biblioteki, za pomocą `no_implementation` atrybutu. W przeciwnym razie zostaną wygenerowane błędy kompilatora. Jest to spowodowane definicje klas otoki wygenerowane przez `#import` instrukcję, określając `no_implementation` atrybutu są wymagane do kompilowania wdrożoną przez **implementation_only —** atrybutu.

**KONIEC określonego języka C++**

## <a name="see-also"></a>Zobacz także

[atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import Directive](../preprocessor/hash-import-directive-cpp.md)