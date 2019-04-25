---
title: _ITERATOR_DEBUG_LEVEL
ms.date: 11/04/2016
f1_keywords:
- _ITERATOR_DEBUG_LEVEL
helpviewer_keywords:
- _ITERATOR_DEBUG_LEVEL
ms.assetid: 718549cd-a9a9-4ab3-867b-aac00b321e67
ms.openlocfilehash: a584fe5a97e251205e750507b27e53e6e7b9a20e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62224197"
---
# <a name="iteratordebuglevel"></a>_ITERATOR_DEBUG_LEVEL

Formanty — makro _ITERATOR_DEBUG_LEVEL czy [sprawdzane Iteratory](../standard-library/checked-iterators.md) i [Obsługa iteratora debugowania](../standard-library/debug-iterator-support.md) są włączone. To makro zastępuje i łączy w sobie funkcje starsze makra _SECURE_SCL i _HAS_ITERATOR_DEBUGGING.

## <a name="macro-values"></a>Wartości — makro

W poniższej tabeli przedstawiono możliwe wartości dla makra _ITERATOR_DEBUG_LEVEL.

|Tryb kompilacji|Wartość — makro|Opis|
|----------------------|----------------|-----------------|
|**Debugowanie**|||
||0|Wyłącza Iteratory sprawdzane i wyłącza debugowania iteratora.|
||1|Włącza Iteratory sprawdzane i wyłącza debugowania iteratora.|
||2 (ustawienie domyślne)|Włącza iteratora debugowania. Iteratory sprawdzane nie są istotne.|
|**Wersja**|||
||0 (domyślnie)|Wyłącza sprawdzane Iteratory.|
||1|Iteratory sprawdzane umożliwia; nie dotyczy debugowania iteratora.|

W trybie wydania kompilator generuje błąd, jeśli określisz _ITERATOR_DEBUG_LEVEL jako 2.

## <a name="remarks"></a>Uwagi

Formanty — makro _ITERATOR_DEBUG_LEVEL czy [sprawdzane Iteratory](../standard-library/checked-iterators.md) są włączone i w trybie debugowania, czy [Obsługa iteratora debugowania](../standard-library/debug-iterator-support.md) jest włączona. Jeśli _ITERATOR_DEBUG_LEVEL jest zdefiniowana jako 1 lub 2, Iteratory sprawdzane zapewniają granice swoje kontenery nie są zastępowane. Jeśli _ITERATOR_DEBUG_LEVEL ma wartość 0, nie są sprawdzane Iteratory. Jeśli _ITERATOR_DEBUG_LEVEL jest zdefiniowana jako 1, każde użycie niebezpieczny iteratora powoduje błąd środowiska uruchomieniowego i program jest zamykany. Jeśli _ITERATOR_DEBUG_LEVEL jest zdefiniowana jako 2, niebezpieczne iteratora Użyj przyczyny, które assert i okno dialogowe błąd środowiska uruchomieniowego, które umożliwia wkroczenia do debugera.

Ponieważ makra _ITERATOR_DEBUG_LEVEL obsługuje funkcje podobne do _SECURE_SCL i _HAS_ITERATOR_DEBUGGING makra, może być pewności która makro, a makra wartość do użycia w danej sytuacji. Aby uniknąć pomyłek, zaleca się, że używasz tylko makro _ITERATOR_DEBUG_LEVEL. W tej tabeli opisano równoważny _ITERATOR_DEBUG_LEVEL wartość makra dla różnych wartości _SECURE_SCL i _HAS_ITERATOR_DEBUGGING w istniejącym kodzie.

|**_ITERATOR_DEBUG_LEVEL** |**_SECURE_SCL** |**_HAS_ITERATOR_DEBUGGING**|
|---|---|---|
|0 (wartość domyślna wersja)|0 (wyłączone)|0 (wyłączone)|
|1|1 (włączony)|0 (wyłączone)|
|2 (wartość domyślna debugowania)|(nie dotyczy)|1 (włączone w trybie debugowania)|

Aby uzyskać informacji na temat sposobu wyłączania ostrzeżeń dotyczących sprawdzonych iteratorów, zobacz [_SCL_SECURE_NO_WARNINGS](../standard-library/scl-secure-no-warnings.md).

### <a name="example"></a>Przykład

Aby określić wartość dla makra _ITERATOR_DEBUG_LEVEL, użyj [/D](../build/reference/d-preprocessor-definitions.md) — opcja kompilatora do definiowania go w wierszu polecenia lub użyć `#define` przed C++ nagłówki standardowej biblioteki znajdują się w plikach źródłowych. Na przykład, w wierszu polecenia, aby skompilować *sample.cpp* w trybie debugowania i użyj Obsługa iteratora debugowania, można określić _ITERATOR_DEBUG_LEVEL definicji makra:

`cl /EHsc /Zi /MDd /D_ITERATOR_DEBUG_LEVEL=1 sample.cpp`

W pliku źródłowym należy określić makra przed wszystkie nagłówki biblioteki standardowej, które definiują Iteratory.

```cpp
// sample.cpp

#define _ITERATOR_DEBUG_LEVEL 1

#include <vector>

// ...
```

## <a name="see-also"></a>Zobacz także

[Zaznaczone iteratory](../standard-library/checked-iterators.md)<br/>
[Obsługa iteratora debugowania](../standard-library/debug-iterator-support.md)<br/>
[Bezpieczne biblioteki: Standardowa biblioteka C++](../standard-library/safe-libraries-cpp-standard-library.md)<br/>
