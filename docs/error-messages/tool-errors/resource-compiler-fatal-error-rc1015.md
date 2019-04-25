---
title: Błąd krytyczny kompilatora zasobów RC1015
ms.date: 11/04/2016
f1_keywords:
- RC1015
helpviewer_keywords:
- RC1015
ms.assetid: 23f187e1-5538-40b5-9042-edd2888f55c2
ms.openlocfilehash: f20101c2edc4da132c89dcda451c71af2304a13d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62297661"
---
# <a name="resource-compiler-fatal-error-rc1015"></a>Błąd krytyczny kompilatora zasobów RC1015

Otwórz, nie może zawierać pliku 'NazwaPliku'

Dany dołączanego pliku nie istnieje, nie można otworzyć lub nie został znaleziony.

Upewnij się, że ustawienia środowiska są prawidłowe i czy określono poprawną ścieżkę do pliku. Upewnij się, że wystarczające dojścia do plików są dostępne dla kompilatora zasobów. Jeśli plik znajduje się na dysku sieciowym, upewnij się, że masz uprawnienia do otwierania pliku.

RC1015 może wystąpić, nawet jeśli dołączanego pliku znajduje się w katalogu określony jako dodatkowym katalogiem obejmują we właściwości konfiguracji -> zasobów -> Strona właściwości ogólnych; Określ pełną ścieżkę do pliku dołączania.
