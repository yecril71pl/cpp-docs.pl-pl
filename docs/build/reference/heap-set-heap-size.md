---
title: /HEAP (Ustaw rozmiar stosu)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.HeapCommitSize
- VC.Project.VCLinkerTool.HeapReserveSize
helpviewer_keywords:
- -HEAP linker option
- heap allocation, setting heap size
- /HEAP linker option
- HEAP linker option
ms.assetid: a3f71927-7f1d-492c-9fdb-dfccb1a043da
ms.openlocfilehash: f155ad56ec1a90479b402e38e7ec7f3e3d80e470
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439526"
---
# <a name="heap-set-heap-size"></a>/HEAP (Ustaw rozmiar stosu)

```
/HEAP:reserve[,commit]
```

## <a name="remarks"></a>Uwagi

Opcja/HEAP ustawia rozmiar sterty w bajtach. Ta opcja jest używana tylko podczas kompilowania pliku. exe.

Argument *rezerwy* określa całkowitą alokację sterty w pamięci wirtualnej. Domyślny rozmiar sterty wynosi 1 MB. Konsolidator zaokrągla określoną wartość do najbliższej 4 bajtów.

Opcjonalny `commit` argument określa ilość pamięci fizycznej do przydzielenia w danym momencie. Przydzielona pamięć wirtualna powoduje, że miejsce jest zarezerwowane w pliku stronicowania. Wyższa wartość `commit` umożliwia zaoszczędzenie czasu, gdy aplikacja wymaga większej ilości miejsca, ale zwiększa wymagania dotyczące pamięci i prawdopodobnie czas uruchamiania.

Określ wartości *rezerw* i `commit` w notacji dziesiętnej lub w języku C.

Ta funkcja jest również dostępna za pośrednictwem pliku definicji modułu z [heapsize](heapsize.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [ C++ Ustawianie właściwości kompilatora i Build w programie Visual Studio](../working-with-project-properties.md).

1. Kliknij folder **konsolidator** .

1. Kliknij stronę właściwości **systemu** .

1. Zmodyfikuj właściwość **rozmiar zatwierdzenia sterty** .

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.HeapReserveSize%2A> i <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.HeapCommitSize%2A>.

## <a name="see-also"></a>Zobacz też

[Dokumentacja konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)
