---
title: "Pliki poleceń LINK | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- link
dev_langs:
- C++
helpviewer_keywords:
- syntax, LINK command files
- command files [C++]
- LINK tool [C++]
- text files, passing arguments to LINK
- LINK tool [C++], command-line syntax
- command files [C++], LINK
ms.assetid: 7154511c-32b9-4e5b-a515-3922fa9de48e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e585fb8fa11d4e3ffe8eff842baacb05f109754c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="link-command-files"></a>Wiersze poleceń LINK
Argumenty wiersza polecenia można przekazać do łącza w formie pliku polecenia. Aby określić plik polecenia do konsolidatora, należy użyć następującej składni:  
  
```  
LINK @commandfile  
```  
  
 `commandfile` To nazwa pliku tekstowego. Nie spację lub tabulator jest dozwolone między znak @ (@) i nazwa pliku. Nie będzie domyślna zwiększenia; należy określić pełną nazwę pliku, w tym wszystkie rozszerzenia. Nie można używać symboli wieloznacznych. Można określić ścieżką bezwzględną ani względną nazwę pliku. ŁĄCZE nie używa zmiennej środowiskowej, aby wyszukać plik.  
  
 W pliku poleceń, argumentów może być oddzielone spacjami lub karty (w wierszu polecenia) i znaki nowego wiersza.  
  
 Całość lub część wiersza polecenia można określić w pliku poleceń. Można użyć więcej niż jeden plik polecenia w poleceniu łącza. ŁĄCZE akceptuje dane wejściowe polecenia pliku tak, jakby zostały określone w tej lokalizacji, w wierszu polecenia. Pliki poleceń nie mogą być zagnieżdżone. ŁĄCZE informujące o zawartość plików poleceń, chyba że [/nologo](../../build/reference/nologo-suppress-startup-banner-linker.md) określono opcję.  
  
## <a name="example"></a>Przykład  
 Poniższe polecenie, aby utworzyć biblioteki DLL przekazuje nazwy plików obiektu i bibliotek w plikach osobne polecenie i używa innego polecenia Specyfikacja opcji /EXPORTS w pliku:  
  
```  
link /dll @objlist.txt @liblist.txt @exports.txt  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)