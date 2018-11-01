---
title: Błąd krytyczny C1210
ms.date: 11/04/2016
f1_keywords:
- C1210
helpviewer_keywords:
- C1210
ms.assetid: e2208309-c284-425c-a7e8-48e96e66f35b
ms.openlocfilehash: a90ca3e3b55642f1a6cd847997b83e4b7db46818
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50591814"
---
# <a name="fatal-error-c1210"></a>Błąd krytyczny C1210

> / CLR: pure i/CLR: Safe nie są obsługiwane przez wersję zainstalowanego środowiska uruchomieniowego

**/CLR: pure** i **/CLR: Safe** opcje kompilatora są przestarzałe w programie Visual Studio 2015 i obsługiwane w programie Visual Studio 2017.

C1210 występuje, gdy masz kompilatora dla bieżącej wersji, ale środowisko uruchomieniowe języka wspólnego z poprzedniej wersji.

Niektóre funkcje kompilatora może nie działać w poprzedniej wersji w czasie wykonywania.

Aby rozwiązać C1210 Zainstaluj wspólnej wersję środowiska wykonawczego języka jest przeznaczona do użytku z kompilatora.