---
title: "Błąd krytyczny C1902 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C1902
dev_langs:
- C++
helpviewer_keywords:
- C1902
ms.assetid: 2dc066cc-fcb1-4725-8bcb-9f44dd0905b7
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4e5f6c22ea848a49a12cc85508fd80a4cfcb90e0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1902"></a>Błąd krytyczny C1902
Niezgodność Menedżera bazy danych programu; Sprawdź swoją instalację  
  
Plik bazy danych programu (PDB) został utworzony przy użyciu nowszej wersji mspdb*XXX*dll niż kompilator znaleziono w systemie. Błąd ten zwykle wskazuje, że mspdbsrv.exe mspdbcore.dll brakuje lub korzystają z różnych wersji niż mspdb*XXX*dll. ( *XXX* symbol zastępczy w mspdb*XXX*zmiany nazwy pliku .dll w poszczególnych wersjach produktu. Na przykład w programie Visual Studio 2015 nazwa pliku jest pliku mspdb140.dll).  
  
Upewnij się, zgodnych wersji mspdbsrv.exe, mspdbcore.dll i mspdb*XXX*dll są zainstalowane w systemie. Upewnij się, że niezgodne wersje nie został skopiowany do katalogu, który zawiera narzędzia kompilatora i łącza do docelowej platformy. Na przykład mogły zostać skopiowane pliki, można wywołać kompilatora lub łącze narzędzie z wiersza polecenia bez ustawienia **ścieżki** zmiennej środowiskowej odpowiednio.