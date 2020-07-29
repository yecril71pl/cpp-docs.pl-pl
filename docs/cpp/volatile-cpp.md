---
title: volatile (C++)
ms.date: 05/07/2019
f1_keywords:
- volatile_cpp
helpviewer_keywords:
- interrupt handlers and volatile keyword [C++]
- volatile keyword [C++]
- volatile objects
- objects [C++], volatile
ms.assetid: 81db4a85-ed5a-4a2c-9a53-5d07a771d2de
ms.openlocfilehash: bbdd7d03d820b9fc0d541dbb31d55b641226f14e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213102"
---
# <a name="volatile-c"></a>volatile (C++)

Kwalifikator typu, którego można użyć do zadeklarowania, że obiekt może zostać zmodyfikowany w programie przez sprzęt.

## <a name="syntax"></a>Składnia

```
volatile declarator ;
```

## <a name="remarks"></a>Uwagi

Aby zmodyfikować sposób interpretacji tego słowa kluczowego przez kompilator, można użyć przełącznika kompilatora [/volatile](../build/reference/volatile-volatile-keyword-interpretation.md) .

Program Visual Studio interpretuje **`volatile`** słowo kluczowe inaczej w zależności od architektury docelowej. W przypadku ARM, jeśli nie określono opcji kompilatora **/volatile** , kompilator wykonuje tak, jakby określono **/volatile: ISO** . W przypadku architektur innych niż ARM, jeśli nie określono opcji kompilatora **/volatile** , kompilator wykonuje tak, jakby **/volatile: MS** zostały określone; w związku z tym, w przypadku architektur innych niż ARM zdecydowanie zaleca się określenie **/volatile: ISO**i użycie jawnych elementów pierwotnych synchronizacji i wewnętrznych kompilatorów podczas pracy z pamięcią udostępnioną przez wątki.

Kwalifikator może służyć **`volatile`** do zapewnienia dostępu do lokalizacji pamięci, które są używane przez procesy asynchroniczne, takie jak programy obsługi przerwań.

Gdy **`volatile`** jest używany w zmiennej, która ma także słowo kluczowe [__restrict](../cpp/extension-restrict.md) , **`volatile`** ma pierwszeństwo.

Jeśli **`struct`** element członkowski jest oznaczony jako **`volatile`** , **`volatile`** jest propagowany do całej struktury. Jeśli struktura nie ma długości, która może zostać skopiowana do bieżącej architektury przy użyciu jednej instrukcji, **`volatile`** może zostać całkowicie utracona w tej strukturze.

**`volatile`** Słowo kluczowe może nie mieć wpływu na pole, jeśli spełniony jest jeden z następujących warunków:

- Długość pola nietrwałego przekracza maksymalny rozmiar, który można skopiować do bieżącej architektury przy użyciu jednej instrukcji.

- Długość najbardziej zewnętrznego **`struct`** lub, jeśli jest to element członkowski prawdopodobnie zagnieżdżonej **`struct`** — przekracza maksymalny rozmiar, który można skopiować do bieżącej architektury przy użyciu jednej instrukcji.

Mimo że procesor nie porządkuje dostępu do pamięci z pamięcią podręczną, zmienne, które nie są buforowane, muszą być oznaczone jako, **`volatile`** Aby zagwarantować, że kompilator nie zmienia kolejności dostępu do pamięci.

Obiekty, które są zadeklarowane jako **`volatile`** nie są używane w niektórych optymalizacjach, ponieważ ich wartości mogą się zmieniać w dowolnym momencie.  System zawsze odczytuje bieżącą wartość obiektu nietrwałego, gdy jest żądany, nawet jeśli poprzednia instrukcja zażądała wartości z tego samego obiektu.  Ponadto wartość obiektu jest zapisywana natychmiast po przypisaniu.

## <a name="iso-compliant"></a>Zgodne ISO

Jeśli znasz słowo kluczowe nietrwałe języka C# lub znasz zachowanie **`volatile`** we wcześniejszych wersjach kompilatora języka Microsoft C++ (MSVC), pamiętaj, że słowo kluczowe standardowego języka c++ 11 ISO **`volatile`** jest inne i jest obsługiwane w MSVC, jeśli określono opcję kompilatora [/volatile: ISO](../build/reference/volatile-volatile-keyword-interpretation.md) . (W przypadku usługi ARM jest ona domyślnie określona). **`volatile`** Słowo kluczowe w standardowym kodzie ISO języka c++ 11 ma być używane tylko na potrzeby dostępu do sprzętu; nie należy używać go do komunikacji między wątkami. W przypadku komunikacji między wątkami należy używać mechanizmów takich jak [std:: \<T> ](../standard-library/atomic.md) informal z [standardowej biblioteki języka C++](../standard-library/cpp-standard-library-reference.md).

## <a name="end-of-iso-compliant"></a>Koniec zgodności z ISO

**Specyficzne dla firmy Microsoft**

Gdy używana jest opcja " **/volatile: MS** Compiler" — domyślnie, gdy architektury inne niż ARM są celem — kompilator generuje dodatkowy kod, aby zachować porządkowanie między odwołaniami do obiektów nietrwałych, a także do zarządzania kolejnością odwołań do innych obiektów globalnych. W szczególności:

- Zapis do obiektu nietrwałego (znanego również jako zapis nietrwały) ma semantykę wersji; oznacza to, że odwołanie do obiektu globalnego lub statycznego, który występuje przed zapisem do obiektu nietrwałego w sekwencji instrukcji, zostanie wykonane przed nietrwałym zapisem w skompilowanym pliku binarnym.

- Odczyt obiektu nietrwałego (znanego również jako nietrwały odczyt) uzyskuje semantykę; oznacza to, że odwołanie do obiektu globalnego lub statycznego, który występuje po odczytaniu pamięci lotnej w sekwencji instrukcji, nastąpi po tej nietrwałej odczytaniu w skompilowanym pliku binarnym.

Pozwala to na używanie obiektów lotnych do blokowania pamięci i wydań w aplikacjach wielowątkowych.

> [!NOTE]
> Gdy jest to oparte na rozszerzonej gwarancji, która jest dostarczana, gdy opcja kompilatora **/volatile: MS** jest używana, kod nie jest przenośny.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[const](../cpp/const-cpp.md)<br/>
[Wskaźniki const i volatile](../cpp/const-and-volatile-pointers.md)
