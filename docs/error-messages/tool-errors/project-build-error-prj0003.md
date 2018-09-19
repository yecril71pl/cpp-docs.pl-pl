---
title: Błąd PRJ0003 kompilacji projektu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0003
dev_langs:
- C++
helpviewer_keywords:
- PRJ0003
ms.assetid: fc5a84bb-c6d3-41d6-8dd6-475455820778
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3d1a23b8171c916b05df1d715f803893ab0720e6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46053820"
---
# <a name="project-build-error-prj0003"></a>Błąd PRJ0003 kompilacji projektu

> Błąd podczas duplikowania "*wiersza polecenia*".

*Wiersza polecenia* polecenia tworzony na podstawie danych wejściowych w **stron właściwości** okno dialogowe zwrócił kod błędu, ale nie widać żadnych informacji w **dane wyjściowe** okna.

Możliwe przyczyny tego błędu:

- Projekt zależy od aplikacji serwera ATL. Począwszy od programu Visual Studio 2008 aplikacji serwera ATL. nie jest już częścią Visual Studio, ale zostało udostępnione jako projekt źródłowy udostępniony w witrynie CodePlex. Aby pobrać kod źródłowy aplikacji serwera ATL. i narzędzi, przejdź do [narzędzia i biblioteki serwera ATL](http://go.microsoft.com/fwlink/p/?linkid=81979).

- Niewystarczające zasoby systemu. Zamknij niektóre aplikacje, aby rozwiązać ten problem.

- Niewystarczające uprawnienia zabezpieczeń. Sprawdź, czy masz wystarczające uprawnienia zabezpieczeń.

- Ścieżki pliku wykonywalnego, określony w **katalogi VC ++** zawiera ścieżkę do narzędzia które próbujesz uruchomić. Aby uzyskać informacje, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md)

- W przypadku projektów plików reguł programu make brakuje polecenie do uruchomienia w dowolnym **kompilacji wiersza polecenia** lub **odbudować wiersza polecenia**.

## <a name="see-also"></a>Zobacz też

[Błędy i ostrzeżenia kompilowania projektu (PRJxxxx)](../../error-messages/tool-errors/project-build-errors-and-warnings-prjxxxx.md)