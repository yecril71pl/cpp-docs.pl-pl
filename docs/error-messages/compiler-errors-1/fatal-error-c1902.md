---
title: "Błąd krytyczny C1902 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C1902
dev_langs: C++
helpviewer_keywords: C1902
ms.assetid: 2dc066cc-fcb1-4725-8bcb-9f44dd0905b7
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 89354565f67c8704eee8c8b5f9dcb94523800c63
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="fatal-error-c1902"></a>Błąd krytyczny C1902
Niezgodność Menedżera bazy danych programu; Sprawdź swoją instalację  
  
Plik bazy danych programu (PDB) został utworzony przy użyciu nowszej wersji mspdb*XXX*dll niż kompilator znaleziono w systemie. Błąd ten zwykle wskazuje, że mspdbsrv.exe mspdbcore.dll brakuje lub korzystają z różnych wersji niż mspdb*XXX*dll. ( *XXX* symbol zastępczy w mspdb*XXX*zmiany nazwy pliku .dll w poszczególnych wersjach produktu. Na przykład w programie Visual Studio 2015 nazwa pliku jest pliku mspdb140.dll).  
  
Upewnij się, zgodnych wersji mspdbsrv.exe, mspdbcore.dll i mspdb*XXX*dll są zainstalowane w systemie. Upewnij się, że niezgodne wersje nie został skopiowany do katalogu, który zawiera narzędzia kompilatora i łącza do docelowej platformy. Na przykład mogły zostać skopiowane pliki, można wywołać kompilatora lub łącze narzędzie z wiersza polecenia bez ustawienia **ścieżki** zmiennej środowiskowej odpowiednio.