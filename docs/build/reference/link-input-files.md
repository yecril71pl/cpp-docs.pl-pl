---
title: "Pliki wejściowe łącze | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: link
dev_langs: C++
helpviewer_keywords:
- files [C++], LINK
- module definition files
- resources [C++], linker files
- LINK tool [C++], input files
- module definition files, linker files
- input files [C++], LINK
- linker [C++], input files
- import libraries [C++], linker files
- command input to linker files [C++]
ms.assetid: bb26fcc5-509a-4620-bc3e-b6c6e603a412
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1d0cae9498d2c9b49e52cf56991d2425de39d7e1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="link-input-files"></a>Pliki wyjściowe LINK
Konsolidator dostarczać pliki zawierające obiekty, importowania i standardowych bibliotek zasobów, definicje modułów i dane wejściowe polecenia. ŁĄCZE nie używaj rozszerzeń plików umożliwia założenia dotyczące zawartości pliku. Zamiast tego łącza sprawdza, czy każdy plik wejściowy ustalenie, jakiego rodzaju pliku jest.  
  
 Pliki obiektów w wierszu polecenia są przetwarzane w kolejności, w jakiej znajdują się w wierszu polecenia. Biblioteki są przeszukiwane w kolejności wiersza polecenia, a także z następujące ostrzeżenie: nierozpoznane symbole, które są podczas wprowadzenia w pliku obiektu z biblioteki są wyszukiwane w tej bibliotece najpierw, a następnie polecenie następujące biblioteki z wiersza polecenia i [/DEFAULTLIB (Określanie domyślnej biblioteki)](../../build/reference/defaultlib-specify-default-library.md) dyrektywy, a następnie do żadnych bibliotek na początku wiersza polecenia.  
  
> [!NOTE]
>  ŁĄCZE nie będzie akceptował średnikiem (lub innego znaku) jako początku komentarz w plikach odpowiedzi i kolejność plików. Średnikami są rozpoznawane tylko jako początek komentarze w plikach definicji modułu (.def).  
  
 ŁĄCZE korzysta z następujących typów plików wejściowych:  
  
-   [pliki .obj](../../build/reference/dot-obj-files-as-linker-input.md)  
  
-   [pliki modułu .netmodule](../../build/reference/netmodule-files-as-linker-input.md)  
  
-   [.lib — pliki](../../build/reference/dot-lib-files-as-linker-input.md)  
  
-   [.EXP — pliki](../../build/reference/dot-exp-files-as-linker-input.md)  
  
-   [.def — pliki](../../build/reference/dot-def-files-as-linker-input.md)  
  
-   [.pdb, pliki](../../build/reference/dot-pdb-files-as-linker-input.md)  
  
-   [pliki .res](../../build/reference/dot-res-files-as-linker-input.md)  
  
-   [.exe — pliki](../../build/reference/dot-exe-files-as-linker-input.md)  
  
-   [pliki txt](../../build/reference/dot-txt-files-as-linker-input.md)  
  
-   [.ilk — pliki](../../build/reference/dot-ilk-files-as-linker-input.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)