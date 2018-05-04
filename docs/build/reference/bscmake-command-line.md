---
title: Wiersz polecenia BSCMAKE | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- BSCMAKE, command line
ms.assetid: 8006e8cf-8bfe-4c23-868a-b0a25e6bbf0f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7866d2960acdd89c3015470ef3971307ba162cd3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="bscmake-command-line"></a>Wiersz polecenia BSCMAKE
Aby uruchomić BSCMAKE, należy użyć następującej składni wiersza polecenia:  
  
```  
BSCMAKE [options] sbrfiles  
```  
  
 Opcje może występować tylko w `options` pól w wierszu polecenia.  
  
 *Sbrfiles* pole określa jeden lub więcej plików SBR utworzonych przez kompilator lub asemblera. Rozdziel nazwy plików SBR spacjami lub kart. Należy określić rozszerzenia. nie jest domyślnie. Można określić ścieżkę z nazwą pliku, a następnie można użyć symboli wieloznacznych systemu operacyjnego (* i?).  
  
 Podczas kompilacji przyrostowej można określić nowe pliki SBR, które nie zostały część oryginalnego kompilacji. Jeśli chcesz, aby wszystkie udziały pozostaną w pliku informacyjnego przeglądarki, należy określić wszystkie pliki SBR (w tym pliki obcięte), które zostały pierwotnie użyte do utworzenia pliku .bsc. W przypadku pominięcia pliku .sbr, ten plik udziału pliku informacyjnego przeglądarki zostaną usunięte.  
  
 Nie określaj pliku .sbr skrócona do pełnej kompilacji. Pełna kompilacja wymaga udziału wszystkich plików SBR określony. Przed wykonaniem pełnej kompilacji ponownie skompilować projekt i Utwórz nowy plik SBR dla każdego pliku puste.  
  
 Następujące polecenie uruchamia BSCMAKE do tworzenia pliku o nazwie MAIN.bsc z trzech plików SBR:  
  
```  
BSCMAKE main.sbr file1.sbr file2.sbr  
```  
  
 Aby uzyskać odpowiednie informacje, zobacz [plik polecenia BSCMAKE](../../build/reference/bscmake-command-file-response-file.md) i [opcje BSCMAKE](../../build/reference/bscmake-options.md).  
  
## <a name="see-also"></a>Zobacz też  
 [BSCMAKE — dokumentacja](../../build/reference/bscmake-reference.md)