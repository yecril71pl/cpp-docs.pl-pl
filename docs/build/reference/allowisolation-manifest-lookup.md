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
ms.openlocfilehash: a0e063aa51e136dfcc7a4445948e8a68d7a99bca
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32369841"
---
# <a name="allowisolation-manifest-lookup"></a>/ALLOWISOLATION (Przeszukiwanie manifestu)
Określa zachowanie wyszukiwania manifestu.  
  
## <a name="syntax"></a>Składnia  
  
```  
/ALLOWISOLATION[:NO]  
```  
  
## <a name="remarks"></a>Uwagi  
 **/ALLOWISOLATION:No** wskazuje bibliotek DLL ładowanych tak, jakby nie było żadnych manifestu i powoduje, że konsolidator ustawia `IMAGE_DLLCHARACTERISTICS_NO_ISOLATION` bitu w nagłówku opcjonalne `DllCharacteristics` pola.  
  
 **/ ALLOWISOLATION** powoduje, że system operacyjny do manifestu wyszukiwań i obciążeń.  
  
 **/ ALLOWISOLATION** jest ustawieniem domyślnym.  
  
 Wyłączenie izolacji pliku wykonywalnego modułu ładującego systemu Windows nie będzie podejmować próby znajdź manifest aplikacji dla nowo utworzonego procesu. Nowy proces nie ma domyślny kontekst aktywacji, nawet jeśli dostępny jest manifestu wewnątrz pliku wykonywalnego lub umieszczane w tym samym katalogu co plik wykonywalny o nazwie * wykonywalnego — nazwa ***. exe.manifest**.  
  
 Aby uzyskać więcej informacji, zobacz [odwołania pliki manifestu](http://msdn.microsoft.com/library/aa375632).  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Rozwiń węzeł **właściwości konfiguracji** węzła.  
  
3.  Rozwiń węzeł **konsolidatora** węzła.  
  
4.  Wybierz **plik manifestu** strony właściwości.  
  
5.  Modyfikowanie **Zezwalaj izolacji** właściwości.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)