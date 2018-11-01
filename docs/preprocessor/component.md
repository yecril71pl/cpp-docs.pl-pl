---
title: składnik
ms.date: 11/04/2016
f1_keywords:
- vc-pragma.component
- component_CPP
helpviewer_keywords:
- component pragma
- pragmas, component
ms.assetid: 7b66355e-3201-4c14-8190-f4a2a81a604a
ms.openlocfilehash: af0e4d7267fab92c867431ab70f4d8a0240a79d2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50666118"
---
# <a name="component"></a>składnik
Kontroluje zbieranie informacji dotyczących przeglądania lub informacji zależności z plików źródłowych.

## <a name="syntax"></a>Składnia

```
#pragma component( browser, { on | off }[, references [, name ]] )
#pragma component( minrebuild, on | off )
#pragma component( mintypeinfo, on | off )
```

## <a name="remarks"></a>Uwagi

### <a name="browser"></a>Przeglądarka

Można włączyć lub wyłączyć zbieranie, a także określić szczególne nazwy do zignorowania podczas zbierania informacji.

Używanie włączania/wyłączania kontroli kolekcji informacji dotyczących przeglądania z pragmy do przodu. Na przykład:

```
#pragma component(browser, off)
```

zatrzymuje kompilator zbierający informacje dotyczące przeglądania.

> [!NOTE]
> Aby włączyć zbieranie informacji o przeglądaniu za pomocą tej pragmie [informacji o przeglądaniu należy najpierw włączyć](../build/reference/building-browse-information-files-overview.md).

`references` Opcji można użyć z lub bez *nazwa* argumentu. Za pomocą `references` bez *nazwa* Włącza lub wyłącza zbieranie odwołań (inne informacje przeglądania nadal będą jednak zbierane). Na przykład:

```
#pragma component(browser, off, references)
```

zatrzymuje kompilator zbierający informacje dotyczących odwołań.

Za pomocą `references` z *nazwa* i `off` zapobiega odwołania do *nazwa* były wyświetlane w oknie przeglądania informacji. Użyj następującej składni, aby zignorować nazwy i typy, którymi nie jesteś zainteresowany i zmniejsz rozmiar plików przeglądania informacji. Na przykład:

```
#pragma component(browser, off, references, DWORD)
```

ignoruje odwołania do typu DWORD od tego momentu. Możesz włączyć zbieranie odniesień do DWORD ponownie przy użyciu `on`:

```
#pragma component(browser, on, references, DWORD)
```

Jest jedynym sposobem, aby wznowić zbieranie odwołań do *nazwa*; Musisz jawnie włączyć dowolną *nazwa* , została wyłączona.

Aby uniemożliwić rozwijanie preprocesora *nazwa* (takich jak rozwijanie wartości NULL na wartość 0), umieść ją w cudzysłowie:

```
#pragma component(browser, off, references, "NULL")
```

### <a name="minimal-rebuild"></a>Minimalna ponowna kompilacja

Funkcja minimalnej kompilacji ponownej Visual C++ wymaga, aby kompilator tworzył i przechowywał informacje zależności klasy języka C++, które zajmują miejsce na dysku. Aby zaoszczędzić miejsce na dysku, można użyć `#pragma component( minrebuild, off )` zawsze, gdy nie musisz zbierać informacji o zależnościach, na przykład w niezmiennych plikach nagłówkowych. Wstaw `#pragma component(minrebuild, on)` po niezmiennych klasach, aby włączyć kolekcję zależności kopii na.

### <a name="reduce-type-information"></a>Ograniczenie informacji typu

`mintypeinfo` Opcja ogranicza informacje debugowania dotyczące określonego regionu. Wielkość tych informacji jest znaczna i dotyczy plików .pdb i .obj. Nie można debugować klas i struktur w regionie mintypeinfo. Korzystanie z opcji mintypeinfo może być pomocne, aby uniknąć następującego ostrzeżenia:

```
LINK : warning LNK4018: too many type indexes in PDB "filename", discarding subsequent type information
```

Aby uzyskać więcej informacji, zobacz [Włącz minimalną ponowną kompilację](../build/reference/gm-enable-minimal-rebuild.md) (/ Gm) opcję kompilatora.

## <a name="see-also"></a>Zobacz też

[Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)