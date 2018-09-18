---
title: Błąd krytyczny C1902 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1902
dev_langs:
- C++
helpviewer_keywords:
- C1902
ms.assetid: 2dc066cc-fcb1-4725-8bcb-9f44dd0905b7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e5a443b5f80eabe9691cf8ff5220bb9b66da51e4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46052572"
---
# <a name="fatal-error-c1902"></a>Błąd krytyczny C1902

Niezgodność Menedżera bazy danych programu; Sprawdź instalację

Plik bazy danych programu (.pdb) został utworzony przy użyciu nowszej wersji mspdb*XXX*.dll niż ta, można znaleźć kompilatora w Twoim systemie. Błąd ten zwykle wskazuje, że mspdbsrv.exe mspdbcore.dll brakuje lub różne wersje niż mspdb*XXX*.dll. ( *XXX* symbol zastępczy w mspdb*XXX*zmiany nazwy pliku dll wraz z każdą wersją produktu. Na przykład w programie Visual Studio 2015 nazwa pliku jest pliku mspdb140.dll).

Upewnij się, zgodne wersje mspdbsrv.exe, mspdbcore.dll i mspdb*XXX*dll są zainstalowane w systemie. Upewnij się, że niezgodność wersji nie został skopiowany do katalogu, który zawiera narzędzia kompilatora i link do docelowej platformy. Na przykład mogły zostać skopiowane pliki, dzięki czemu może wywołać narzędzie kompilatora lub linku w wierszu polecenia bez ustawienia **ścieżki** zmiennej środowiskowej odpowiednio.