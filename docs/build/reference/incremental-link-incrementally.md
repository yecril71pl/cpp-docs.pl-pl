---
title: /INCREMENTAL (Łącz stopniowo)
ms.date: 11/04/2016
f1_keywords:
- /incremental
- VC.Project.VCLinkerTool.LinkIncremental
helpviewer_keywords:
- /INCREMENTAL linker option
- -INCREMENTAL linker option
- INCREMENTAL linker option
- link incrementally option
- LINK tool [C++], options for full linking
- incremental linking
ms.assetid: 135656ff-94fa-4ad4-a613-22e1a2a5d16b
ms.openlocfilehash: 189affe57694a8369e9cf7ac98815cc5888b69aa
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62270015"
---
# <a name="incremental-link-incrementally"></a>/INCREMENTAL (Łącz stopniowo)

```
/INCREMENTAL[:NO]
```

## <a name="remarks"></a>Uwagi

Określa, jak konsolidator obsługuje łączenie przyrostowe.

Domyślnie konsolidator jest uruchamiany w trybie przyrostowym. Aby zastąpić domyślne łączenie przyrostowe, określ /INCREMENTAL:NO.

Program łączony przyrostowo jest funkcjonalnie równoważny programowi innych niż przyrostowo połączony. Jednakże ponieważ jest przygotowany na kolejne łącza przyrostowe, przyrostowo połączony biblioteki statycznej, wykonywalny lub plik biblioteki dołączanej dynamicznie:

- Ze względu na dopełnienie kodu i danych jest większy niż program łączony przyrostowo. Dopełnienie umożliwia konsolidatorowi zwiększenie rozmiaru funkcji i danych bez konieczności ponownego tworzenia pliku.

- Może zawierać sekcje thunk skoków do obsługi przeniesienia funkcji do nowych adresów.

   > [!NOTE]
   > W celu zapewnienia, że ostateczna wersja kompilacji nie zawiera dopełnień ani sekcji Thunk, Połącz program bez przyrostowo.

Aby łączyć przyrostowo, niezależnie od ustawienia domyślnego, określ /INCREMENTAL. Gdy ta opcja jest zaznaczona, konsolidator generuje ostrzeżenie, jeśli nie może łączyć przyrostowo, a następnie łączy program bez przyrostowo. Niektóre opcje i sytuacje zastępują /INCREMENTAL.

Większość programów może być łączonych przyrostowo. Jednak niektóre zmiany są zbyt duże, a niektóre opcje są niezgodne z łączeniem przyrostowym. Polecenie LINK wykonuje pełne połączenie, jeżeli jest określona którakolwiek z następujących opcji:

- Łączenie przyrostowe nie jest zaznaczone (/INCREMENTAL:NO)

- Wybrano /OPT:REF

- Wybrano /OPT:ICF

- Wybrano /OPT:LBR

- Wybrano /ORDER

/ INCREMENTAL jest implikowane przy określeniu [/DEBUG](debug-generate-debug-info.md) jest określony.

Poza tym polecenie LINK wykonuje pełne połączenie, jeżeli wystąpi którakolwiek z następujących sytuacji:

- Brakuje pliku stanu przyrostowego (.ilk). (LINK tworzy nowy plik .ilk w ramach przygotowań do kolejnych łączeń przyrostowych).

- Nie ma uprawnienia do zapisu dla pliku .ilk. (LINK ignoruje plik .ilk i łączy inne niż przyrostowo.)

- Brakuje pliku wyjściowego .exe lub .dll.

- Sygnatura czasowa .ilk, .exe lub .dll została zmieniona.

- Opcja LINK została zmieniona. Większość opcji LINK po zmianie między kompilacjami powoduje pełne łącze.

- Plik obiektowy (.obj) jest dodawany lub pomijany.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **konsolidatora** folderu.

1. Wybierz **ogólne** stronę właściwości.

1. Modyfikowanie **Włącz konsolidację przyrostową** właściwości.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

1. Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.LinkIncremental%2A>.

## <a name="see-also"></a>Zobacz także

[Dokumentacja konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)
