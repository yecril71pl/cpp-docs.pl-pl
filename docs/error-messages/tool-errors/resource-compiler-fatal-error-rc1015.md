---
title: Błąd krytyczny kompilatora zasobów RC1015 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC1015
dev_langs:
- C++
helpviewer_keywords:
- RC1015
ms.assetid: 23f187e1-5538-40b5-9042-edd2888f55c2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0456845152fb2879d2f58c9c40af2562c7207535
ms.sourcegitcommit: d3c41b16bf05af2149090e996d8e71cd6cd55c7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/09/2018
ms.locfileid: "48890247"
---
# <a name="resource-compiler-fatal-error-rc1015"></a>Błąd krytyczny kompilatora zasobów RC1015

Otwórz, nie może zawierać pliku 'NazwaPliku'

Dany dołączanego pliku nie istnieje, nie można otworzyć lub nie został znaleziony.

Upewnij się, że ustawienia środowiska są prawidłowe i czy określono poprawną ścieżkę do pliku. Upewnij się, że wystarczające dojścia do plików są dostępne dla kompilatora zasobów. Jeśli plik znajduje się na dysku sieciowym, upewnij się, że masz uprawnienia do otwierania pliku.

RC1015 może wystąpić, nawet jeśli dołączanego pliku znajduje się w katalogu określony jako dodatkowym katalogiem obejmują we właściwości konfiguracji -> zasobów -> Strona właściwości ogólnych; Określ pełną ścieżkę do pliku dołączania.
