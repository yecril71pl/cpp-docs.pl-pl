---
title: Wiersz polecenia BSCMAKE | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: BSCMAKE, command line
ms.assetid: 8006e8cf-8bfe-4c23-868a-b0a25e6bbf0f
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 278518ae37a4e76ea4fe0252e3341e54daebe599
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
 [Odwołanie BSCMAKE](../../build/reference/bscmake-reference.md)