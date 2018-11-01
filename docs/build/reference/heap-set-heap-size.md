---
title: /HEAP (Ustaw rozmiar sterty)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.HeapCommitSize
- /heap
- VC.Project.VCLinkerTool.HeapReserveSize
helpviewer_keywords:
- -HEAP linker option
- heap allocation, setting heap size
- /HEAP linker option
- HEAP linker option
ms.assetid: a3f71927-7f1d-492c-9fdb-dfccb1a043da
ms.openlocfilehash: 7ae600b50f791555dddb31fc4b46dcaf85ebd727
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50650740"
---
# <a name="heap-set-heap-size"></a>/HEAP (Ustaw rozmiar sterty)

```
/HEAP:reserve[,commit]
```

## <a name="remarks"></a>Uwagi

Opcja /HEAP ustawia rozmiar stosu w bajtach. Ta opcja jest tylko do użytku podczas tworzenia pliku .exe.

*Zarezerwować* argument określa Alokacja całkowita sterty w pamięci wirtualnej. Domyślny rozmiar stosu to 1 MB. Konsolidator zaokrągla w górę określoną wartość do najbliższej 4 bajty.

Opcjonalny `commit` argument określa ilość pamięci fizycznej do przydzielenia w danym momencie. Zadeklarowanej pamięci wirtualnej powoduje, że miejsce, które mają zostać zarezerwowane w pliku stronicowania. Uzyskanie lepszej `commit` wartość pozwala zaoszczędzić czas, gdy aplikacja potrzebuje więcej miejsca na stercie, ale zwiększa wymagania dotyczące pamięci i ewentualnie czas uruchamiania.

Określ *zarezerwować* i `commit` wartości dziesiętnych lub notacji języka C.

Ta funkcja jest również dostępna za pośrednictwem pliku definicji modułu za pomocą [HEAPSIZE](../../build/reference/heapsize.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [ustawienie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).

1. Kliknij przycisk **konsolidatora** folderu.

1. Kliknij przycisk **systemu** stronę właściwości.

1. Modyfikowanie **zatwierdzenia. Generace** właściwości.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.HeapReserveSize%2A> i <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.HeapCommitSize%2A>.

## <a name="see-also"></a>Zobacz też

[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)<br/>
[Opcje konsolidatora](../../build/reference/linker-options.md)