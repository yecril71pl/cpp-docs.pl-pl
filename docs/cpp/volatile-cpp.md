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
ms.openlocfilehash: 841b2e1e4ffbec87a170c45be8ad0cd0f831a0ef
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371899"
---
# <a name="volatile-c"></a>volatile (C++)

Kwalifikator typu, którego można użyć do zadeklarowania, że obiekt może być modyfikowany w programie przez sprzęt.

## <a name="syntax"></a>Składnia

```
volatile declarator ;
```

## <a name="remarks"></a>Uwagi

Przełącznik [/volatile](../build/reference/volatile-volatile-keyword-interpretation.md) kompilatora można użyć, aby zmodyfikować sposób, w jaki kompilator interpretuje to słowo kluczowe.

Visual Studio interpretuje słowo kluczowe **volatile** inaczej w zależności od architektury docelowej. Dla ARM, jeśli nie **/volatile** kompilator opcja jest określona, kompilator wykonuje tak, jakby **/volatile:iso** zostały określone. Dla architektur innych niż ARM, jeśli nie **/volatile** kompilator opcja jest określona, kompilator wykonuje tak, jakby **/volatile:ms** zostały określone; w związku z tym dla architektur innych niż ARM zdecydowanie zaleca się określenie **/volatile:iso**i używać jawnych ujednuchwień synchronizacji i wewnętrznego kompilatora, gdy masz do czynienia z pamięcią współużytkowaną przez wątki.

Można użyć **kwalifikator volatile,** aby zapewnić dostęp do lokalizacji pamięci, które są używane przez procesy asynchroniczne, takie jak programy obsługi przerwań.

Gdy **volatile** jest używany na zmiennej, która ma również [__restrict](../cpp/extension-restrict.md) słowa kluczowego, **volatile** ma pierwszeństwo.

Jeśli **element członkowski struktury** jest oznaczony jako **lotny,** wówczas **volatile** jest propagowany do całej struktury. Jeśli struktura nie ma długości, która może być skopiowana na bieżącej architekturze przy użyciu jednej instrukcji, **volatile** mogą zostać całkowicie utracone na tej strukturze.

Słowo kluczowe **volatile** może nie mieć wpływu na pole, jeśli spełniony jest jeden z następujących warunków:

- Długość pola nietrwałego przekracza maksymalny rozmiar, który można skopiować na bieżącej architekturze przy użyciu jednej instrukcji.

- Długość najbardziej zewnętrznej **struktury**zawierającej — lub jeśli jest to element członkowski ewentualnie zagnieżdżonej **struktury**— przekracza maksymalny rozmiar, który można skopiować na bieżącej architekturze przy użyciu jednej instrukcji.

Mimo że procesor nie zmienia kolejności dostępu do pamięci nieskrywowanej, zmienne nieskładkalne muszą być oznaczone jako **zmienne,** aby zagwarantować, że kompilator nie zamieści ponownie kolejności dostępu do pamięci.

Obiekty, które są zadeklarowane jako **nietrwałe** nie są używane w niektórych optymalizacji, ponieważ ich wartości można zmienić w dowolnym momencie.  System zawsze odczytuje bieżącą wartość obiektu lotnego, gdy jest wymagany, nawet jeśli poprzednia instrukcja poprosiła o wartość z tego samego obiektu.  Ponadto wartość obiektu jest zapisywana natychmiast przy przypisywaniu.

## <a name="iso-compliant"></a>Zgodność z normą ISO

Jeśli znasz słowo kluczowe volatile języka C# lub znasz zachowanie **volatile** we wcześniejszych wersjach kompilatora Microsoft C++(MSVC), należy pamiętać, że C ++ 11 ISO Standard **volatile** — słowo kluczowe jest inny i jest obsługiwany w msvc, gdy określono opcję [kompilatora /volatile:iso.](../build/reference/volatile-volatile-keyword-interpretation.md) (W przypadku arm jest on domyślnie określony). Słowo kluczowe **volatile** w kodzie standardu ISO języka C++11 ma być używane tylko w celu uzyskania dostępu do sprzętu; nie używać go do komunikacji między wątkami. W przypadku komunikacji między wątkami należy użyć mechanizmów takich jak [\<std::atomic T>](../standard-library/atomic.md) z [biblioteki standardowej języka C++.](../standard-library/cpp-standard-library-reference.md)

## <a name="end-of-iso-compliant"></a>Koniec zgodności z normą ISO

**Specyficzne dla firmy Microsoft**

Gdy używana jest opcja **kompilatora /volatile:ms** — domyślnie, gdy są ukierunkowane architektury inne niż ARM — kompilator generuje dodatkowy kod do obsługi kolejności między odwołaniami do obiektów nietrwałych oprócz utrzymywania kolejności odwołań do innych obiektów globalnych. W szczególności:

- Zapis do obiektu lotnego (znanego również jako zapis lotny) ma semantykę wydania; oznacza to, że odwołanie do obiektu globalnego lub statycznego, który występuje przed zapis do obiektu lotnego w sekwencji instrukcji nastąpi przed tym volatile zapisu w skompilowanym pliku binarnym.

- Odczyt obiektu lotnego (znanego również jako odczyt lotny) ma semantykę Acquire; oznacza to, że odwołanie do obiektu globalnego lub statycznego, który występuje po odczytie pamięci nietrwałej w sekwencji instrukcji wystąpi po tym volatile odczytu w skompilowanym pliku binarnym.

Dzięki temu nietrwałe obiekty mają być używane do blokad pamięci i zwalnia w aplikacjach wielowątkowych.

> [!NOTE]
> Gdy opiera się na rozszerzonej gwarancji, która jest podana, gdy **/volatile:ms** opcja kompilatora jest używany, kod jest nieprzenośny.

**ZAKOŃCZ Specyficzne dla firmy Microsoft**

## <a name="see-also"></a>Zobacz też

[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[const](../cpp/const-cpp.md)<br/>
[Wskaźniki stałe i nietrwałe](../cpp/const-and-volatile-pointers.md)
