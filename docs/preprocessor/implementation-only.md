---
title: implementation_only — atrybut importowania
ms.date: 08/29/2019
f1_keywords:
- implementation_only
helpviewer_keywords:
- implementation_only attribute
ms.assetid: d8cabc86-4425-45a0-9587-d57536980088
ms.openlocfilehash: 08144b3c815350acfe6a856b36d2d88085d1c04d
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218975"
---
# <a name="implementation_only-import-attribute"></a>implementation_only — atrybut importowania

**C++Specjalne**

Pomija generowanie `.tlh` podstawowego pliku nagłówkowego biblioteki typów.

## <a name="syntax"></a>Składnia

> **#import** *Biblioteka typów* **implementation_only**

## <a name="remarks"></a>Uwagi

Ten plik zawiera wszystkie deklaracje używane do ujawniania zawartości biblioteki typów. Plik `.tli` nagłówkowy wraz z implementacjami funkcji składowych otoki zostanie wygenerowany i uwzględniony w kompilacji.

Gdy ten atrybut jest określony, zawartość `.tli` nagłówka znajduje się w tej samej przestrzeni nazw co zazwyczaj jest używana `.tlh` w nagłówku. Ponadto funkcje składowe nie są zadeklarowane jako inline.

Atrybut **implementation_only** jest przeznaczony do użycia w połączeniu z atrybutem [no_implementation](../preprocessor/no-implementation.md) w celu zachowania implementacji z prekompilowanego pliku nagłówkowego (pch). `#import` Instrukcja`no_implementation` z atrybutem jest umieszczana w regionie źródłowym użytym do utworzenia PCH. Wyniki PCH są używane przez wiele plików źródłowych. Instrukcja z atrybutem implementation_only jest następnie używana poza regionem PCH. `#import` Musisz użyć tej instrukcji tylko raz w jednym z plików źródłowych. Generuje wszystkie wymagane funkcje składowe otoki bez dodatkowych ponownych kompilacji dla każdego pliku źródłowego.

> [!NOTE]
> Atrybut **implementation_only** w jednej `#import` instrukcji musi być używany w połączeniu z inną `#import` instrukcją o tej samej bibliotece typów z `no_implementation` atrybutem. W przeciwnym razie błędy kompilatora są generowane. Dzieje się tak, ponieważ definicje klas otoki `#import` generowane przez instrukcję `no_implementation` z atrybutem są wymagane do kompilowania implementacji wygenerowanych przez atrybut **implementation_only** .

**ZAKOŃCZENIE C++ określonych**

## <a name="see-also"></a>Zobacz także

[Atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)
