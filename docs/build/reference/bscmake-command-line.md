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
ms.openlocfilehash: b79f7e7c181112877c795f3601e8211e70403563
ms.sourcegitcommit: 7eadb968405bcb92ffa505e3ad8ac73483e59685
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2018
ms.locfileid: "39207750"
---
# <a name="bscmake-command-line"></a>Wiersz polecenia BSCMAKE
Aby uruchomić BSCMAKE, użyj następującej składni wiersza polecenia:  
  
```  
BSCMAKE [options] sbrfiles  
```  
  
 Opcje mogą być wyświetlane tylko w `options` pola w wierszu polecenia.  
  
 *Sbrfiles* pole określa jeden lub więcej plików SBR, utworzony przez kompilator lub asemblera. Rozdziel nazwy plików SBR tabulacji lub spacji. Należy określić rozszerzenia. nie jest domyślnie. Można określić ścieżkę przy użyciu nazwy pliku, a następnie można użyć symboli wieloznacznych systemu operacyjnego (\* i?).  
  
 Podczas kompilacji przyrostowej można określić nowe pliki SBR, które nie były częścią oryginalnego kompilacji. Jeśli chcesz, aby wszystkie współtworzone elementy pozostaną w pliku informacyjnego przeglądarki, należy określić wszystkie pliki SBR (w tym pliki obcięte), które zostały pierwotnie użyte do utworzenia pliku .bsc. Jeżeli pominięto plik SBR wkładu tego pliku do pliku informacyjnego przeglądarki zostaną usunięte.  
  
 Nie należy określać plik SBR obcięte dla pełnej kompilacji. Pełna kompilacja wymaga wkłady wszystkich plików SBR określony. Przed wykonaniem pełnej kompilacji należy ponownie skompilować projekt i Utwórz nowy plik SBR dla każdego pliku puste.  
  
 Następujące polecenie uruchamia BSCMAKE do tworzenia pliku o nazwie MAIN.bsc z trzech plików SBR:  
  
```  
BSCMAKE main.sbr file1.sbr file2.sbr  
```  
  
 Aby uzyskać powiązane informacje, zobacz [plik polecenia BSCMAKE](../../build/reference/bscmake-command-file-response-file.md) i [opcje BSCMAKE](../../build/reference/bscmake-options.md).  
  
## <a name="see-also"></a>Zobacz też  
 [BSCMAKE — dokumentacja](../../build/reference/bscmake-reference.md)