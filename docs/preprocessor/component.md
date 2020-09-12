---
title: component, pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.component
- component_CPP
helpviewer_keywords:
- component pragma
- pragmas, component
ms.assetid: 7b66355e-3201-4c14-8190-f4a2a81a604a
ms.openlocfilehash: 73b308fdc426be9b403b808d4e638b4f5c1e9149
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040733"
---
# <a name="component-pragma"></a>component, pragma

Kontroluje zbieranie informacji o przeglądaniu lub informacji o zależnościach w plikach źródłowych.

## <a name="syntax"></a>Składnia

> **składnik #pragma (Browser,** { **on** \| **off** } \[ **,** **References** \[ **,** *name* ]] **)** \
> **składnik #pragma (minrebuild,** { **on** \| **off** } **)** \
> **składnik #pragma (Mintypeinfo,** { **on** \| **off** } **)**

## <a name="remarks"></a>Uwagi

### <a name="browser"></a>Przeglądarka

Można włączyć lub wyłączyć zbieranie, a także określić szczególne nazwy do zignorowania podczas zbierania informacji.

Używanie włączania/wyłączania kontroli kolekcji informacji dotyczących przeglądania z pragmy do przodu. Na przykład:

```cpp
#pragma component(browser, off)
```

zatrzymuje kompilator zbierający informacje dotyczące przeglądania.

> [!NOTE]
> Aby włączyć zbieranie informacji o przeglądaniu za pomocą tej dyrektywy pragma, [należy najpierw włączyć informacje o przeglądaniu](../build/reference/building-browse-information-files-overview.md).

Opcja **odwołania** może być używana z argumentem *name* lub bez niego. Użycie **odwołań** bez *nazwy* powoduje włączenie lub wyłączenie zbierania odwołań (inne informacje o przeglądaniu nadal są zbierane). Na przykład:

```cpp
#pragma component(browser, off, references)
```

zatrzymuje kompilator zbierający informacje dotyczących odwołań.

Użycie **odwołań** z *nazwą* i **Wyłącz** uniemożliwia odwoływanie się do *nazwy* w oknie informacji o przeglądaniu. Użyj następującej składni, aby zignorować nazwy i typy, którymi nie jesteś zainteresowany i zmniejsz rozmiar plików przeglądania informacji. Na przykład:

```cpp
#pragma component(browser, off, references, DWORD)
```

ignoruje odwołania do wartości DWORD od tego momentu. Można ponownie włączyć zbieranie odwołań do danych DWORD **przy użyciu:**

```cpp
#pragma component(browser, on, references, DWORD)
```

Jest to jedyny sposób na wznowienie zbierania odwołań do *nazwy*; należy jawnie włączyć dowolną *nazwę* , która została wyłączona.

Aby zapobiec powiększaniu *nazwy* przez preprocesora (na przykład rozszerzanie wartości null na 0), należy umieścić cudzysłowy wokół niej:

```cpp
#pragma component(browser, off, references, "NULL")
```

### <a name="minimal-rebuild"></a>Minimalna ponowna kompilacja

Przestarzała funkcja [/GM (Włącz minimalną](../build/reference/gm-enable-minimal-rebuild.md) ponowną kompilację) wymaga, aby kompilator utworzył i przechowywał informacje o zależnościach klas języka C++, które zajmują miejsce na dysku. Aby zaoszczędzić miejsce na dysku, można użyć `#pragma component( minrebuild, off )` zawsze, gdy nie trzeba zbierać informacji o zależnościach, na przykład w plikach nagłówkowych, które nie są zmieniane. Wstaw `#pragma component( minrebuild, on )` po cofnięciu zmiany klas, aby ponownie włączyć zbieranie zależności.

### <a name="reduce-type-information"></a>Zmniejsz informacje o typie

`mintypeinfo`Opcja zmniejsza informacje debugowania dla określonego regionu. Wielkość tych informacji jest znaczna i dotyczy plików .pdb i .obj. Nie można debugować klas i struktur w regionie mintypeinfo. Korzystanie z opcji mintypeinfo może być pomocne, aby uniknąć następującego ostrzeżenia:

```cmd
LINK : warning LNK4018: too many type indexes in PDB "filename", discarding subsequent type information
```

Aby uzyskać więcej informacji, zobacz opcję kompilatora [/GM (Włącz minimalną](../build/reference/gm-enable-minimal-rebuild.md)  ponowną kompilację).

## <a name="see-also"></a>Zobacz także

[Dyrektywy pragma i słowo kluczowe __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
