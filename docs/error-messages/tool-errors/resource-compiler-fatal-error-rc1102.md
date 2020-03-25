---
title: Błąd krytyczny kompilatora zasobów RC1102
ms.date: 11/04/2016
f1_keywords:
- RC1102
helpviewer_keywords:
- RC1102
ms.assetid: bd2091f8-ef5e-4151-a8d6-98043e9422b6
ms.openlocfilehash: e614a7e85f508a452f42588fe40054dfcc8a7089
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182483"
---
# <a name="resource-compiler-fatal-error-rc1102"></a>Błąd krytyczny kompilatora zasobów RC1102

Błąd wewnętrzny: zbyt wiele argumentów do RCPP

Zbyt wiele argumentów zostało przekazano do preprocesora kompilatora zasobów. Zmniejsz liczbę symboli zdefiniowaną za pomocą opcji Definiuj symbole (/d), definiując je w źródle. Ten błąd może być również spowodowany przez określenie zbyt wielu ścieżek wyszukiwania plików dołączanych za pomocą opcji dołączania ścieżki wyszukiwania (/i).
