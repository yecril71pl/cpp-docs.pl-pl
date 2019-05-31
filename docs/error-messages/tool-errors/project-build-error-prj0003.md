---
title: Błąd PRJ0003 kompilacji projektu
ms.date: 11/04/2016
f1_keywords:
- PRJ0003
helpviewer_keywords:
- PRJ0003
ms.assetid: fc5a84bb-c6d3-41d6-8dd6-475455820778
ms.openlocfilehash: e30a63ba48434196478b52283880864d3e4ae6ea
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/31/2019
ms.locfileid: "66450754"
---
# <a name="project-build-error-prj0003"></a>Błąd PRJ0003 kompilacji projektu

> Błąd podczas duplikowania "*wiersza polecenia*".

*Wiersza polecenia* polecenia tworzony na podstawie danych wejściowych w **stron właściwości** okno dialogowe zwrócił kod błędu, ale nie widać żadnych informacji w **dane wyjściowe** okna.

Możliwe przyczyny tego błędu:

- Projekt zależy od aplikacji serwera ATL. Począwszy od programu Visual Studio 2008 aplikacji serwera ATL. nie jest już częścią Visual Studio, ale zostało udostępnione jako projekt źródłowy udostępniony w witrynie CodePlex. Aby pobrać kod źródłowy aplikacji serwera ATL. i narzędzi, przejdź do [narzędzia i biblioteki serwera ATL](https://go.microsoft.com/fwlink/p/?linkid=81979).

- Niewystarczające zasoby systemu. Zamknij niektóre aplikacje, aby rozwiązać ten problem.

- Niewystarczające uprawnienia zabezpieczeń. Sprawdź, czy masz wystarczające uprawnienia zabezpieczeń.

- Ścieżki pliku wykonywalnego, określony w **katalogi VC ++** zawiera ścieżkę do narzędzia które próbujesz uruchomić. Aby uzyskać informacje, zobacz [Ustaw kompilatora i właściwości kompilacji](../../build/working-with-project-properties.md)

- W przypadku projektów plików reguł programu make brakuje polecenie do uruchomienia w dowolnym **kompilacji wiersza polecenia** lub **odbudować wiersza polecenia**.

## <a name="see-also"></a>Zobacz także

[Błędy i ostrzeżenia kompilowania projektu (PRJxxxx)](../../error-messages/tool-errors/project-build-errors-and-warnings-prjxxxx.md)