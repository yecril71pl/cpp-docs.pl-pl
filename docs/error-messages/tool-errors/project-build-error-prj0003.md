---
title: Błąd PRJ0003 kompilacji projektu
ms.date: 11/04/2016
f1_keywords:
- PRJ0003
helpviewer_keywords:
- PRJ0003
ms.assetid: fc5a84bb-c6d3-41d6-8dd6-475455820778
ms.openlocfilehash: 00d101e62d49078ebfcfff9455497f30224b84fe
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59039523"
---
# <a name="project-build-error-prj0003"></a>Błąd PRJ0003 kompilacji projektu

> Błąd podczas duplikowania "*wiersza polecenia*".

*Wiersza polecenia* polecenia tworzony na podstawie danych wejściowych w **stron właściwości** okno dialogowe zwrócił kod błędu, ale nie widać żadnych informacji w **dane wyjściowe** okna.

Możliwe przyczyny tego błędu:

- Projekt zależy od aplikacji serwera ATL. Począwszy od programu Visual Studio 2008 aplikacji serwera ATL. nie jest już częścią Visual Studio, ale zostało udostępnione jako projekt źródłowy udostępniony w witrynie CodePlex. Aby pobrać kod źródłowy aplikacji serwera ATL. i narzędzi, przejdź do [narzędzia i biblioteki serwera ATL](http://go.microsoft.com/fwlink/p/?linkid=81979).

- Niewystarczające zasoby systemu. Zamknij niektóre aplikacje, aby rozwiązać ten problem.

- Niewystarczające uprawnienia zabezpieczeń. Sprawdź, czy masz wystarczające uprawnienia zabezpieczeń.

- Ścieżki pliku wykonywalnego, określony w **katalogi VC ++** zawiera ścieżkę do narzędzia które próbujesz uruchomić. Aby uzyskać informacje, zobacz [Ustaw kompilatora i właściwości kompilacji](../../build/working-with-project-properties.md)

- W przypadku projektów plików reguł programu make brakuje polecenie do uruchomienia w dowolnym **kompilacji wiersza polecenia** lub **odbudować wiersza polecenia**.

## <a name="see-also"></a>Zobacz także

[Błędy w kompilacji projektu oraz ostrzeżenia (PRJxxxx)](../../error-messages/tool-errors/project-build-errors-and-warnings-prjxxxx.md)