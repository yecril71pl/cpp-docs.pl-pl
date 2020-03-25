---
title: Błąd PRJ0003 kompilacji projektu
ms.date: 11/04/2016
f1_keywords:
- PRJ0003
helpviewer_keywords:
- PRJ0003
ms.assetid: fc5a84bb-c6d3-41d6-8dd6-475455820778
ms.openlocfilehash: 59028c6d886630ef7db115a2ea93327669b2fcfd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192929"
---
# <a name="project-build-error-prj0003"></a>Błąd PRJ0003 kompilacji projektu

> Wystąpił błąd podczas duplikowania "*wiersz polecenia*".

Polecenie *wiersza polecenia* utworzone na podstawie danych wejściowych w oknie dialogowym **strony właściwości** zwróciło kod błędu, ale w oknie **danych wyjściowych** nie są wyświetlane żadne informacje.

Możliwe przyczyny tego błędu to:

- Projekt zależy od serwera ATL. Począwszy od programu Visual Studio 2008, serwer ATL nie jest już uwzględniony jako część programu Visual Studio, ale został wystawiony jako projekt udostępnionego źródła w CodePlex. Aby pobrać kod źródłowy i narzędzia programu ATL Server, przejdź do [biblioteki i narzędzi serwera ATL](https://go.microsoft.com/fwlink/p/?linkid=81979).

- Niskie zasoby systemowe. Zamknij niektóre aplikacje, aby rozwiązać ten problem.

- Niewystarczające uprawnienia zabezpieczeń. Sprawdź, czy masz wystarczające uprawnienia zabezpieczeń.

- Ścieżki plików wykonywalnych określone w **katalogach VC + +** nie zawierają ścieżki do narzędzia, które próbujesz uruchomić. Aby uzyskać więcej informacji, zobacz [Ustawianie właściwości kompilatora i Build](../../build/working-with-project-properties.md)

- W przypadku projektów pliku reguł programu make brakuje polecenia do uruchomienia w **wierszu polecenia kompilacji** lub **ponownie skompiluj wiersz polecenia**.

## <a name="see-also"></a>Zobacz też

[Błędy i ostrzeżenia kompilowania projektu (PRJxxxx)](../../error-messages/tool-errors/project-build-errors-and-warnings-prjxxxx.md)
