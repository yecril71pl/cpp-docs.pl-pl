---
title: -INCREMENTAL (łącz stopniowo) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /incremental
- VC.Project.VCLinkerTool.LinkIncremental
dev_langs:
- C++
helpviewer_keywords:
- /INCREMENTAL linker option
- -INCREMENTAL linker option
- INCREMENTAL linker option
- link incrementally option
- LINK tool [C++], options for full linking
- incremental linking
ms.assetid: 135656ff-94fa-4ad4-a613-22e1a2a5d16b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7495b3dda7b79f45045176fc949016f89c92506a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="incremental-link-incrementally"></a>/INCREMENTAL (Łącz stopniowo)
```  
/INCREMENTAL[:NO]  
```  
  
## <a name="remarks"></a>Uwagi  
 Określa, jak konsolidator obsługuje łączenie przyrostowe.  
  
 Domyślnie konsolidator jest uruchamiany w trybie przyrostowym. Aby zastąpić domyślne łączenie przyrostowe, określ /INCREMENTAL:NO.  
  
 Przyrostowo programu jest funkcjonalnym odpowiednikiem program, który jest połączony z systemem innym niż — przyrostowo. Jednakże ponieważ jest przygotowywany kolejnych konsolidacji przyrostowej, przyrostowo połączone biblioteki pliku wykonywalnego, statyczne lub pliku biblioteki DLL:  
  
-   Jest większa niż program-przyrostowo połączonej z powodu uzupełniania kodu i danych. Dopełnienie umożliwia konsolidator, aby zwiększyć rozmiar funkcji i danych bez konieczności ponownego tworzenia pliku.  
  
-   Może zawierać sekcje thunk skoków do obsługi przeniesienia funkcji do nowych adresów.  
  
    > [!NOTE]
    >  Aby upewnić się, że ostatecznej wersji kompilacji nie zawiera uzupełnienie lub osadzeń, link nie przyrostowo programu.  
  
 Aby łączyć przyrostowo, niezależnie od ustawienia domyślnego, określ /INCREMENTAL. Gdy ta opcja jest zaznaczona, konsolidator wygeneruje ostrzeżenie, jeśli nie można połączyć przyrostowo, a następnie z systemem innym niż — przyrostowo łączy program. Niektóre opcje i sytuacje zastępują /INCREMENTAL.  
  
 Większość programów może być łączonych przyrostowo. Jednak niektóre zmiany są zbyt duże, a niektóre opcje są niezgodne z łączeniem przyrostowym. Polecenie LINK wykonuje pełne połączenie, jeżeli jest określona którakolwiek z następujących opcji:  
  
-   Łączenie przyrostowe nie jest zaznaczone (/INCREMENTAL:NO)  
  
-   Wybrano /OPT:REF  
  
-   Wybrano /OPT:ICF  
  
-   Wybrano /OPT:LBR  
  
-   Wybrano /ORDER  
  
 / INCREMENTAL technicznego po [/DEBUG](../../build/reference/debug-generate-debug-info.md) jest określona.  
  
 Poza tym polecenie LINK wykonuje pełne połączenie, jeżeli wystąpi którakolwiek z następujących sytuacji:  
  
-   Brakuje pliku stanu przyrostowego (.ilk). (LINK tworzy nowy plik .ilk w ramach przygotowań do kolejnych łączeń przyrostowych).  
  
-   Nie ma uprawnienia do zapisu dla pliku .ilk. (Łącze pomija plik .ilk i łącza z systemem innym niż — przyrostowo.)  
  
-   Brakuje pliku wyjściowego .exe lub .dll.  
  
-   Sygnatura czasowa .ilk, .exe lub .dll została zmieniona.  
  
-   Opcja LINK została zmieniona. Większość opcji LINK po zmianie między kompilacjami powoduje pełne łącze.  
  
-   Plik obiektowy (.obj) jest dodawany lub pomijany.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Wybierz **konsolidatora** folderu.  
  
3.  Wybierz **ogólne** strony właściwości.  
  
4.  Modyfikowanie **włączyć konsolidowania przyrostowego** właściwości.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora  
  
1.  Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.LinkIncremental%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)