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
ms.openlocfilehash: 2396b5afaed09a28fd83f22fccde0be04e3d7790
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221879"
---
# <a name="volatile-c"></a>volatile (C++)

Kwalifikator typu, który można użyć, aby zadeklarować, że można zmodyfikować obiekt w programie przez sprzęt.

## <a name="syntax"></a>Składnia

```
volatile declarator ;
```

## <a name="remarks"></a>Uwagi

Możesz użyć [/volatile](../build/reference/volatile-volatile-keyword-interpretation.md) przełącznika kompilatora, aby zmodyfikować, jak kompilator interpretuje słowa kluczowego.

Program Visual Studio interpretuje **volatile** — słowo kluczowe inaczej w zależności od architektury docelowej. Dla ARM, jeśli nie **/volatile** — opcja kompilatora jest określony, kompilator wykonuje tak, jakby **/volatile:iso** zostały określone. Dla architektur niż ARM, jeśli nie **/volatile** — opcja kompilatora jest określony, kompilator wykonuje tak, jakby **/volatile:ms** zostały określone; w związku z tym, dla architektur innych niż ARM firma Microsoft zdecydowanie Zaleca się, który określisz **/volatile:iso**, używanie jawnymi podstawami synchronizacji i niejawnymi kompilacjami, gdy masz do czynienia z pamięcią, która jest udostępniona w wielu wątkach.

Możesz użyć **volatile** kwalifikatora w celu zapewnienia dostępu do lokalizacji pamięci, które są używane przez proces asynchroniczny, takich jak programy obsługi przerwań.

Gdy **volatile** jest używany w zmiennej, która także ma [element __restrict](../cpp/extension-restrict.md) — słowo kluczowe, **volatile** ma pierwszeństwo przed.

Jeśli **struktury** element członkowski jest oznaczony jako **volatile**, następnie **volatile** jest propagowana do całej struktury. Jeśli struktura nie ma długości, która może zostać skopiowany na bieżącej architektury za pomocą jednej instrukcji **volatile** mogą zostać utracone całkowicie na tej struktury.

**Volatile** — słowo kluczowe może mieć żadnego wpływu na pola, jeśli jest spełniony jeden z następujących warunków:

- Długość pola nietrwałego przekracza maksymalny rozmiar, który można skopiować na bieżącej architektury za pomocą jednej instrukcji.

- Długość najbardziej zewnętrznej zawierającego **struktury**— lub jeśli jest ono członkiem prawdopodobnie zagnieżdżonych **struktury**— przekracza maksymalny rozmiar, który można skopiować na bieżącej architektury za pomocą jednej instrukcji.

Mimo, że procesor nie zmieniać kolejność dostępów do pamięci nie podlega buforowaniu, zmienne nie podlega buforowaniu, musi być oznaczona jako **volatile** celu zagwarantowania, że kompilator nie mogli zmienić kolejności pamięci uzyskuje dostęp.

Obiekty, które są zadeklarowane jako **volatile** nie są używane w niektórych optymalizacji, ponieważ ich wartości można zmienić w dowolnym momencie.  System ma zawsze wartość bieżącą wartość obiektu volatile żądanego, nawet w przypadku poprzednich instrukcji o podanie wartości z tego samego obiektu.  Ponadto wartość obiektu są zapisywane bezpośrednio na przypisanie.

## <a name="iso-compliant"></a>ISO zgodne

Jeśli znasz C# volatile — słowo kluczowe lub powszechnie znane z zachowaniem **volatile** we wcześniejszych wersjach programu Microsoft C++ kompilatora (MSVC), należy pamiętać, który Standard C ++ 11 ISO **volatile** — słowo kluczowe jest inny i jest obsługiwany w MSVC podczas [/volatile:iso](../build/reference/volatile-volatile-keyword-interpretation.md) określono opcję kompilatora. (Dla ARM, określono domyślnie). **Volatile** — słowo kluczowe w C ++ 11 ISO standardowy kod ma być używany tylko w przypadku dostępu do sprzętu; nie należy jej używać do komunikacji między wątku. Do komunikacji między wątku, użyj mechanizmów takich jak [std::atomic\<T >](../standard-library/atomic.md) z [standardowej biblioteki języka C++](../standard-library/cpp-standard-library-reference.md).

## <a name="end-of-iso-compliant"></a>Koniec ISO zgodne

## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft

Gdy **/volatile:ms** — opcja kompilatora jest używany — domyślnie, gdy architekturą docelową są architektur niż ARM — kompilator generuje dodatkowego kodu, aby zachować kolejność wśród odwołań do obiektów volatile oprócz obsługi kolejność z odwołaniami do innych obiektów globalnych. W szczególności:

- Zapis do obiektów volatile (znany także jako volatile zapis) ma semantykę wersji; oznacza to, że odwołanie do obiektu globalnych lub statycznych, który występuje przed zapisu do obiektu volatile w sekwencji instrukcji wystąpi przed tym volatile zapisu w skompilowanym plikiem binarnym.

- Odczyt obiektu volatile (znany także jako odczyt volatile) ma semantykę nabywania; oznacza to, że odwołania do obiektów globalnych lub statycznych, występujący po odczytu volatile pamięci w sekwencji instrukcji nastąpi po tym volatile odczytu w skompilowanym plikiem binarnym.

Dzięki temu obiektów volatile służący do blokowania pamięci i wersji w aplikacjach wielowątkowych.

> [!NOTE]
>  Gdy opiera się na rozszerzone gwarancji, że gdy udostępnił **/volatile:ms** — opcja kompilatora jest używany, kod nie jest przenośna.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[const](../cpp/const-cpp.md)<br/>
[Wskaźniki stałe i nietrwałe](../cpp/const-and-volatile-pointers.md)