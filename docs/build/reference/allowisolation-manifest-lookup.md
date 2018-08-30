---
title: -ALLOWISOLATION (przeszukiwanie manifestu) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /ALLOWISOLATION
- VC.Project.VCLinkerTool.AllowIsolation
dev_langs:
- C++
helpviewer_keywords:
- -ALLOWISOLATION linker option
- /ALLOWISOLATION linker option
ms.assetid: 6d41851e-b3c1-4bdf-beaa-031773089d6f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 62f467ff467d785d17601737436e0eb1ff972f37
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43205496"
---
# <a name="allowisolation-manifest-lookup"></a>/ALLOWISOLATION (Przeszukiwanie manifestu)
Określa zachowanie wyszukiwania plików manifestu.  
  
## <a name="syntax"></a>Składnia  
  
```  
/ALLOWISOLATION[:NO]  
```  
  
## <a name="remarks"></a>Uwagi  
 **/ALLOWISOLATION:No** wskazuje bibliotek DLL ładowanych tak, jakby nie było żadnych manifestu i powoduje, że konsolidator ustawia `IMAGE_DLLCHARACTERISTICS_NO_ISOLATION` bit w opcjonalnym nagłówku `DllCharacteristics` pola.  
  
 **/ ALLOWISOLATION** powoduje, że system operacyjny do manifestu, wyszukiwania i obciążeniami.  
  
 **/ ALLOWISOLATION** jest ustawieniem domyślnym.  
  
 Po wyłączeniu izolacji dla pliku wykonywalnego modułu ładującego Windows nie będzie próbował znaleźć manifest aplikacji do nowo utworzonego procesu. Nowy proces nie będzie domyślny kontekst aktywacji, nawet jeśli dostępny jest manifestu wewnątrz pliku wykonywalnego lub umieszczone w tym samym katalogu co plik wykonywalny o nazwie <em>nazwę pliku wykonywalnego</em>**. exe.manifest**.  
  
 Aby uzyskać więcej informacji, zobacz [odwołania plików manifestu](/windows/desktop/SbsCs/manifest-files-reference).  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Rozwiń **właściwości konfiguracji** węzła.  
  
3.  Rozwiń **konsolidatora** węzła.  
  
4.  Wybierz **pliku manifestu** stronę właściwości.  
  
5.  Modyfikowanie **Zezwalaj na izolację** właściwości.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)