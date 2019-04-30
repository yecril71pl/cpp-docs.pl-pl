---
title: Błąd krytyczny kompilatora zasobów RC1102
ms.date: 11/04/2016
f1_keywords:
- RC1102
helpviewer_keywords:
- RC1102
ms.assetid: bd2091f8-ef5e-4151-a8d6-98043e9422b6
ms.openlocfilehash: 7e322b96d32e6d531de4081386702767d45f0837
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62374309"
---
# <a name="resource-compiler-fatal-error-rc1102"></a>Błąd krytyczny kompilatora zasobów RC1102

Błąd wewnętrzny: za dużo argumentów dla RCPP

Zbyt wiele argumentów zostało przekazanych do preprocesora kompilatora zasobów. Zmniejsz liczbę symboli zdefiniowanych z symbolami zdefiniować (/ d) opcja, definiując je w źródle. Ten błąd, również może być spowodowany określając zbyt wiele zawiera ścieżki wyszukiwania pliku przy użyciu opcji zawierają ścieżkę wyszukiwania (/ i).