---
title: Niskiego poziomu I-O | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: c.io
dev_langs: C++
helpviewer_keywords:
- I/O [CRT], low-level
- I/O [CRT], functions
- low-level I/O routines
- file handles [C++]
- file handles [C++], I/O functions
ms.assetid: 53e11bdd-6720-481c-8b2b-3a3a569ed534
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c22164fdc2bd8236b6f4819609175c80bd472abf
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="low-level-io"></a>We/Wy niskiego poziomu
Te funkcje wywoływać bezpośrednio dla operacji niższe niż te dostarczone przez strumień we/wy systemu operacyjnego. Niskiego poziomu dane wejściowe i wyjściowe wywołania czy nie buforu lub format danych.  
  
 Procedury niższego poziomu mogą uzyskiwać dostęp do standardowych strumieni otwierane w momencie uruchamiania programu przy użyciu następujących deskryptorów plików wstępnie zdefiniowane.  
  
|Strumień|Plik deskryptora|  
|------------|---------------------|  
|`stdin`|0|  
|`stdout`|1|  
|`stderr`|2|  
  
 Niskiego poziomu zestawu procedury we/wy [errno](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) — zmienna globalna po wystąpieniu błędu. Stdio — musi zawierać. H podczas korzystania z funkcji niskiego poziomu tylko wtedy, gdy program wymaga stałą, który jest zdefiniowany w stdio —. H, takich jak plik końcowy wskaźnika (`EOF`).  
  
### <a name="low-level-io-functions"></a>Funkcje We/Wy niskiego poziomu  
  
|Funkcja|Zastosowanie|  
|--------------|---------|  
|[_zamknij](../c-runtime-library/reference/close.md)|Zamknij plik|  
|[_commit —](../c-runtime-library/reference/commit.md)|Zapisywanie plików do dysku|  
|[_creat —, _wcreat —](../c-runtime-library/reference/creat-wcreat.md)|Utwórz plik|  
|[_dup —](../c-runtime-library/reference/dup-dup2.md)|Zwracany dalej deskryptorów plików dostępnych dla danego pliku|  
|[_dup2 —](../c-runtime-library/reference/dup-dup2.md)|Utworzyć drugi deskryptora dla danego pliku|  
|[_eof —](../c-runtime-library/reference/eof.md)|Test na koniec pliku|  
|[_lseek —, _lseeki64 —](../c-runtime-library/reference/lseek-lseeki64.md)|Zmiana położenia wskaźnika pliku do podanej lokalizacji|  
|[_otwórz, _wopen —](../c-runtime-library/reference/open-wopen.md)|Otwórz plik|  
|[_przeczytaj](../c-runtime-library/reference/read.md)|Odczyt danych z pliku|  
|[_sopen —, _wsopen —](../c-runtime-library/reference/sopen-wsopen.md), [_sopen_s —, _wsopen_s —](../c-runtime-library/reference/sopen-s-wsopen-s.md)|Otwórz plik do udostępniania plików|  
|[_tell —, _telli64 —](../c-runtime-library/reference/tell-telli64.md)|Pobierz bieżącą pozycję wskaźnika pliku|  
|[_umask —](../c-runtime-library/reference/umask.md), [_umask_s —](../c-runtime-library/reference/umask-s.md)|Ustaw uprawnienia pliku maska|  
|[_Write](../c-runtime-library/reference/write.md)|Wpisywanie danych do pliku|  
  
 `_dup`i `_dup2` są zwykle używane do skojarzenia z różnych plików deskryptorów plików wstępnie zdefiniowane.  
  
## <a name="see-also"></a>Zobacz też  
 [Dane wejściowe i wyjściowe](../c-runtime-library/input-and-output.md)   
 [Procedury czasu wykonywania według kategorii](../c-runtime-library/run-time-routines-by-category.md)   
 [Wywołania systemowe](../c-runtime-library/system-calls.md)