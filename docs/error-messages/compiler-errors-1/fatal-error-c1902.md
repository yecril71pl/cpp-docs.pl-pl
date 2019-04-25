---
title: Błąd krytyczny C1902
ms.date: 11/04/2016
f1_keywords:
- C1902
helpviewer_keywords:
- C1902
ms.assetid: 2dc066cc-fcb1-4725-8bcb-9f44dd0905b7
ms.openlocfilehash: c425430a6d08ae8a97c4dcd0f5764f44dee43e5f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62165869"
---
# <a name="fatal-error-c1902"></a>Błąd krytyczny C1902

Niezgodność Menedżera bazy danych programu; Sprawdź instalację

Plik bazy danych programu (.pdb) został utworzony przy użyciu nowszej wersji mspdb*XXX*.dll niż ta, można znaleźć kompilatora w Twoim systemie. Błąd ten zwykle wskazuje, że mspdbsrv.exe mspdbcore.dll brakuje lub różne wersje niż mspdb*XXX*.dll. ( *XXX* symbol zastępczy w mspdb*XXX*zmiany nazwy pliku dll wraz z każdą wersją produktu. Na przykład w programie Visual Studio 2015 nazwa pliku jest pliku mspdb140.dll).

Upewnij się, zgodne wersje mspdbsrv.exe, mspdbcore.dll i mspdb*XXX*dll są zainstalowane w systemie. Upewnij się, że niezgodność wersji nie został skopiowany do katalogu, który zawiera narzędzia kompilatora i link do docelowej platformy. Na przykład mogły zostać skopiowane pliki, dzięki czemu może wywołać narzędzie kompilatora lub linku w wierszu polecenia bez ustawienia **ścieżki** zmiennej środowiskowej odpowiednio.