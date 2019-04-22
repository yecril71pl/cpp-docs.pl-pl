---
title: składnik
ms.date: 04/08/2019
f1_keywords:
- vc-pragma.component
- component_CPP
helpviewer_keywords:
- component pragma
- pragmas, component
ms.assetid: 7b66355e-3201-4c14-8190-f4a2a81a604a
ms.openlocfilehash: 4870860650a39d27639ad18100ba37ba14aa15c0
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59424069"
---
# <a name="component"></a>składnik

Kontrolę nad zbieraniem informacji dotyczących przeglądania lub informacji zależności z plików źródłowych.

## <a name="syntax"></a>Składnia

> **#pragma component (przeglądarki,** { **na** | **poza** } [**,** **odwołania** [**,** *nazwa* ]] **)** \
> **#pragma component (minrebuild na** | **wyłączone)** \
> **#pragma component (mintypeinfo na** | **wyłączone)**

## <a name="remarks"></a>Uwagi

### <a name="browser"></a>Przeglądarka

Można włączyć lub wyłączyć zbieranie, a także określić szczególne nazwy do zignorowania podczas zbierania informacji.

Używanie włączania/wyłączania kontroli kolekcji informacji dotyczących przeglądania z pragmy do przodu. Na przykład:

```cpp
#pragma component(browser, off)
```

zatrzymuje kompilator zbierający informacje dotyczące przeglądania.

> [!NOTE]
> Aby włączyć zbieranie informacji o przeglądaniu za pomocą tej pragmie [informacji o przeglądaniu należy najpierw włączyć](../build/reference/building-browse-information-files-overview.md).

`references` Opcji można użyć z lub bez *nazwa* argumentu. Za pomocą `references` bez *nazwa* Włącza lub wyłącza zbieranie odwołań (inne informacje przeglądania nadal będą jednak zbierane). Na przykład:

```cpp
#pragma component(browser, off, references)
```

zatrzymuje kompilator zbierający informacje dotyczących odwołań.

Za pomocą `references` z *nazwa* i `off` zapobiega odwołania do *nazwa* były wyświetlane w oknie przeglądania informacji. Użyj następującej składni, aby zignorować nazwy i typy, którymi nie jesteś zainteresowany i zmniejsz rozmiar plików przeglądania informacji. Na przykład:

```cpp
#pragma component(browser, off, references, DWORD)
```

ignoruje odwołania do typu DWORD od tego momentu. Możesz włączyć zbieranie odniesień do DWORD ponownie przy użyciu `on`:

```cpp
#pragma component(browser, on, references, DWORD)
```

Jest jedynym sposobem, aby wznowić zbieranie odwołań do *nazwa*; Musisz jawnie włączyć dowolną *nazwa* , została wyłączona.

Aby uniemożliwić rozwijanie preprocesora *nazwa* (takich jak rozwijanie wartości NULL na wartość 0), umieść ją w cudzysłowie:

```cpp
#pragma component(browser, off, references, "NULL")
```

### <a name="minimal-rebuild"></a>Minimalna ponowna kompilacja

Przestarzała [/Gm (Włącz minimalną ponowną kompilację)](../build/reference/gm-enable-minimal-rebuild.md) funkcja wymaga kompilatora, aby utworzyć i zapisać C++ klasy informacji o zależnościach, które zajmują miejsce na dysku. Aby zaoszczędzić miejsce na dysku, można użyć `#pragma component( minrebuild, off )` zawsze, gdy nie musisz zbierać informacji o zależnościach, na przykład w niezmiennych plikach nagłówkowych. Wstaw `#pragma component(minrebuild, on)` po niezmiennych klasach, aby włączyć kolekcję zależności kopii na.

### <a name="reduce-type-information"></a>Ograniczenie informacji typu

`mintypeinfo` Opcja ogranicza informacje debugowania dotyczące określonego regionu. Wielkość tych informacji jest znaczna i dotyczy plików .pdb i .obj. Nie można debugować klas i struktur w regionie mintypeinfo. Korzystanie z opcji mintypeinfo może być pomocne, aby uniknąć następującego ostrzeżenia:

```cmd
LINK : warning LNK4018: too many type indexes in PDB "filename", discarding subsequent type information
```

Aby uzyskać więcej informacji, zobacz [/Gm (Włącz minimalną ponowną kompilację)](../build/reference/gm-enable-minimal-rebuild.md) — opcja kompilatora.

## <a name="see-also"></a>Zobacz także

[Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)