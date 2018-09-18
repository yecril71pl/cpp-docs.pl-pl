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
ms.openlocfilehash: 7a72cba53ebe9a286ac2e7cbbf2c41b78f4e4e08
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46100769"
---
# <a name="resource-compiler-fatal-error-rc1015"></a>Błąd krytyczny kompilatora zasobów RC1015

Otwórz, nie może zawierać pliku 'NazwaPliku'

Dany dołączanego pliku nie istnieje, nie można otworzyć lub nie został znaleziony.

Upewnij się, że ustawienia środowiska są prawidłowe i czy określono poprawną ścieżkę do pliku. Upewnij się, że wystarczające dojścia do plików są dostępne dla kompilatora zasobów. Jeśli plik znajduje się na dysku sieciowym, upewnij się, że masz uprawnienia do otwierania pliku.

RC1015 może wystąpić, nawet jeśli dołączanego pliku znajduje się w katalogu określony jako dodatkowym katalogiem obejmują we właściwości konfiguracji -> zasobów -> Strona właściwości ogólnych; Określ pełną ścieżkę do pliku dołączania.

Aby uzyskać więcej informacji, zobacz artykuł bazy wiedzy Q326987: RC1015 błędu podczas przy użyciu zasobów widoku czy ścieżki dołączania jest za długa.